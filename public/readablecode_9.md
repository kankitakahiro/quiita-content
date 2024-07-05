---
title: リーダブルコード　9章　変数と読みやすさ
tags:
  - リーダブルコード
  - 命名規則
private: true
updated_at: 
id: 
organization_url_name: null
slide: false
ignorePublish: false
---
- [1. 変数を削除する](#1-変数を削除する)
    - [役に立たないコード一覧](#役に立たないコード一覧)
    - [中間結果を削除する](#中間結果を削除する)
    - [制御フロー変数を削除する](#制御フロー変数を削除する)
- [2. 変数のスコープを縮める](#2-変数のスコープを縮める)
  - [C++のif文のスコープ](#cのif文のスコープ)
  - [JavaScriptで「プライベート」変数を作る](#javascriptでプライベート変数を作る)
  - [JavaScriptのグローバルスコープ](#javascriptのグローバルスコープ)
  - [PythonとJavascrptのネストしないスコープ](#pythonとjavascrptのネストしないスコープ)
  - [定義の位値を下げる](#定義の位値を下げる)
- [3. 変数は一度だけ書き込む](#3-変数は一度だけ書き込む)
- [4. 最後の列](#4-最後の列)
- [5. まとめ](#5-まとめ)

変数を適当に使うとプログラムが理解しにくくなる

1. 変数が多いと変数を追跡するのが難しくなる
2. 変数のスコープが大きいとスコープを把握する時間が長くなる
3. 変数が頻繁に変更されると現在の値を把握するのが難しくなる

この問題への対処法を説明している

### 1. 変数を削除する

不要な変数は排除することで読みやすくなる

##### 役に立たないコード一覧

```python
now = datetime.datetime.now()
root_message.last_view_time = now
```

このコードでnowを使う意味はない。

理由

* 複雑な式を分割していない。
* より明確になっていない。date.time.now()のままでも十分に明確である。
* 一度しか使用していないため重複コードの削除になっていない。

このような特徴がある場合は変数を削除しよう。

##### 中間結果を削除する

```javascript
var remove_one = function(array, value_to_remove){
    var index_to_remove = null;
    for (var i = 0; i < array.length; i += 1){
        if(array[i] === value_to_remove){
            index_to_remove = 1;
            break;
        }
    }
    if(index_to_remove !== null){
        array.splice(index_to_remove,1);
    }
}
```
変数index_to_removeは中間結果を保持するために使っているため削除することが出来る。

```javascript
var remove_one = function(array, value_to_remove){
    for (var i = 0; i < array.length; i += 1){
        if(array[i] === value_to_remove){
            array.splice(i,1);
            return;
        }
    }
}
```
早く関数から返すことで簡潔になった。
タスクはできるだけ早く完了する方が良い

##### 制御フロー変数を削除する

```javascript
boolean done = false;
while(/*条件*/ && !done){
    ...
    if(...){
        done = true;
        continue;
    }
}
```
この`done`はループのいろいろなところに設定されている。

このような変数を「制御フロー変数」呼んでいる。

うまくプログラミングすると制御フロー変数は削除することが出来る。

```javascript
while(/*条件*/){
    ...
    if(...){
        break;
    }
}
```

このように修正すると削除することが出来る。

ネストが深くbreakが使えない場合はコード（ループの内部のコードやループ全体）を新しい関数に移動すると良い。

### 2. 変数のスコープを縮める

* 鍵となる考え
変数のことが見えるコード行数を出来るだけ減らす。

多くのプログラムはモジュール・クラス・関数・ブロックスコープなどのスコープのアクセスレベルが複数用意されている。

このアクセスを出来るだけ減らすと良い。

こうすることで一度に考える変数の数を減らすことが出来る。

```C#
class LargeClass{
    string str_;

    void Method1(){
        str_ = ...;
        Method2();
    }
    void Method2(){
        // str_を使っている
    }
    // str_を使っていないメソッドがたくさんある
};
```

メンバ変数はクラスの中で「ミニグローバル」になっているとも言える。

大きな変数で把握することは難しい。

従ってこの場合はstr_を「格下げ」すると良い

```C#
class LargeClass{
    void Method1(){
        string str_ = ...;
        Method2(str_);
    }
    void Method2(string str){
        // str_を使っている
    }
    // その他のメソッドではstrは見えない
};
```

クラスのメンバへのアクセスを制限するもう1つの方法にメソッドを出来るだけ`static`にするという方法がある

`static`を使うと「メンバ変数と関係ない」ことがよくわかる

もう1つの方法は大きなクラスを小さなクラスに分割することだ。

ただし、分割したいのはデータ（つまり変数）であることを意識して、相互にメンバを参照することがなどがないようにしよう。

#### C++のif文のスコープ

```C++
PaymentInfo* Info = database.ReadPaymentInfo();
if (info){
    cout << "User paid: " << info->amount() << endl;
}
```
変数infoはif文の中でしか使われない。そのため条件式で定義すると良い。

```C++
if(PaymentInfo* info = database.ReadPaymentInfo()){
    cout << "User paid: " << info->amount() << endl;
}
```

#### JavaScriptで「プライベート」変数を作る

```C++
submitted = false; // 注意：グローバル変数
var submit_form = function (form_name){
    if (submitted){
        return; // 二重投稿禁止
    }
    submitted = true;
};
```
submittedのようなグローバル変数は良くない。このような場合クロージャで包むと良い。

```C++
var submit_form = (function(){
    var submitted = false; // 注意：以下の関数からしかアクセスされない

    return function (form_name){
        if (submitted){
            return; // 二重投稿禁止
        }
    };
    submitted = true;
}())
```

#### JavaScriptのグローバルスコープ

Javascriptは変数にvarを付けないとグローバルスコープに入ってしまう。

すると全てのJavascriptファイルや`<script>`ブロックからアクセスできてしまう。

'''JavaScript
<script>
    var f = function(){
        // 危険:'i'は'var'で宣言されていない!
        for(i = 0; i < 10; i += 1)
    };

    f();
</script>
<script>
    alert(i); // '10'が表示される。'i'はグローバル変数
</script>
'''

このスコープ規則によって奇妙なバグが起こることが考えられる。
変数を定義するときには常にvarキーワードを付ける(例：var x = i)。このように使うことで変数のスコープをその変数が定義された関数に制限することが出来る。

#### PythonとJavascrptのネストしないスコープ

C++やjavaのような言語にはブロックスコープがある。

if,for,tryなどのブロックで定義された変数はスコープがそのブロックに制限される。

```php
if (...){
    int x = 1;
}
x++; // コンパイルエラー!'x'は未定義です。
```

PYthonやjavascriptではブロックで定義された変数はその関数全体に「こぼれ出る」。

```python
# ここまではexample_valueを使っていない
if request:
    for value in request.value:
        if value > 0:
            example_value = value
            break
for logger in debag.loggers:
    logger.log("Example:", example_value)
```
このようなコードは読みにくい。
`example_value`を使っている場所に「最も近い共通の祖先」で変数を定義すればコードが読みやすくなる。

```python
example_value = None

if request:
    for value in request.value:
        if value > 0:
            example_value = value
            break
for logger in debag.loggers:
    logger.log("Example:", example_value)
```
または`example_value`は中間結果を保持しているだけのため削除することも出来る。

```python
def LogExample(value):
    for logger in debag.loggers:
        logger.log("Example:", example_value)
if request:
    for value in request.value:
        if value > 0:
            LogExample(value) # すぐに'value'を使う
            break
```

#### 定義の位値を下げる

元々C言語では関数やブロックの先頭で変数を定義する必要があった。

```C
def ViewFilteredReplies(original_id):
    filter_replies = []
    root_message = Messages.objects.get(original_id)
    all_replies = Messatges.objects.select(root_id=original_id)

    root_message.view_count += 1
    root_message.last_view_time = datetime.datetime.now()
    root_message.save()

    for reply in all_replies:
        if reply.spam_votes <= MAX_SPAM_VOTES:
            filtered_replies.append(reply)

    return filtered_replies
```
このコードの問題点は常に3つの変数を切り替えなければいけないこと。
変数の定義を変数を使う直前に移動することで読みやすくなる。

```python
def ViewFilteredReplies(original_id):
    root_message = Messages.objects.get(original_id)
    root_message.view_count += 1
    root_message.last_view_time = datetime.datetime.now()
    root_message.save()

    all_replies = Messatges.objects.select(root_id=original_id)
    filter_replies = []
    for reply in all_replies:
        if reply.spam_votes <= MAX_SPAM_VOTES:
            filtered_replies.append(reply)

    return filtered_replies
```

### 3. 変数は一度だけ書き込む

変数が絶えず更新され続けると理解しにくい。

この問題を対処するために変数は一度だけ書き込むようにするとわかりやすくなる。

変数の変更する箇所を少なくすることで読みやすさがあがる。

実際多くの言語でStringなどの組み込み型はイミュータブルになっている。「イミュータブルはトラブルになる傾向が少ない」ため積極的にconstなどを使うと良い。

* 鍵となる考え
変数を操作する場所が増えると、現在値の判断が難しくなる。

※イミュータブル : 変更不可

### 4. 最後の列

'''html
<input type="text" id="input1" value="Dustin">
<input type="text" id="input2" value="Trevor">
<input type="text" id="input3" value="">
<input type="text" id="input4" value="Melissa">
'''

idはinput1から1ずつ増加する。
文字列を受け取ってウェブページにある最初の空の<input>に入力する関数を作りたい。
関数の戻り値は更新したDOM要素(空の入力フィールドがなければnull)になる。

```javascript
var setFirstEmptyInput = function (new_value){
    var found = false;
    var i = 1;
    var elem = document.getElementById('input' + i);
    while (elem !== null){
        if (elem.value === ''){
            found = true;
            break;
        }
        i++;
        elem = document.getElementById('input' + i);
    }
    if (found) elem.value = new_value;
    return elem;
};
```
このコードは動くが綺麗ではない。
この場合は変数から考えると良い。

var found
var i
var elem

この三つの変数は関数の中でなんども書き換えられており、わかりにくい。

```javascript
var setFirstEmptyInput = function (new_value){
    var i = 1;
    var elem = document.getElementById('input' + i);
    while (elem !== null){
        if (elem.value === ''){
            elem.value = new_value;
            return elem
        }
        i++;
        elem = document.getElementById('input' + i);
    }
    return null;
};
```
次にelemを見る。
elemはiに合わせてイテレートしている。
そこでwhileをforに書き換えてみる。
```javascript
var setFirstEmptyInput = function (new_value){
    for(var i = 1; true; i++){
        var elem = document.getElementById('input' + i);
        if(elem === null)
            retrun null; //検索失敗。空のフィールドは見つからなかった。
        if (elem.value === ''){
            elem.value = new_value;
            return elem
        }
    }
};
```
### 5. まとめ

* 邪魔な変数を削除する
* 変数のスコープを出来るだけ小さくする
* 一度だけ書き込む変数を使う