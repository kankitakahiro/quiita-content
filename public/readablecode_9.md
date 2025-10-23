---
title: リーダブルコード　9章　変数と読みやすさ
tags:
  - リーダブルコード
  - 命名規則
private: true
updated_at: '2025-10-23T22:38:41+09:00'
id: 7a28a87b88cc5a77e4b6
organization_url_name: null
slide: false
ignorePublish: false
---
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

##### C++のif文のスコープ

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
