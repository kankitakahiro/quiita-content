---
title: リーダブルコード　5章 コメントすべきことを知る 6章 コメントは正確で簡潔に
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
- [1. コメントすべきでは「ない」こと](#1-コメントすべきではないこと)
- [2. 自分の考えを記録する](#2-自分の考えを記録する)
- [3. 読み手の立場になって考える](#3-読み手の立場になって考える)
- [4. ライターズブロックを乗り越える](#4-ライターズブロックを乗り越える)
- [5. コメントは簡潔にしておく](#5-コメントは簡潔にしておく)
- [6. 曖昧な代名詞を避ける](#6-曖昧な代名詞を避ける)
- [7. 歯切れの悪い文章を磨く](#7-歯切れの悪い文章を磨く)
- [8. 関数の動作を正確に記述する](#8-関数の動作を正確に記述する)
- [9. 入出力のコーナーケースに実例を使う](#9-入出力のコーナーケースに実例を使う)
- [10. コードの意図を書く](#10-コードの意図を書く)
- [11. 「名前付き引数」コメント](#11-名前付き引数コメント)
- [12. 情報密度の高い言葉を使う](#12-情報密度の高い言葉を使う)
_______

### 1. コメントすべきでは「ない」こと

* コードからすぐにわかることをコメントに書かない

「すぐに」が大切であり、コメントを読んだ方が早く理解できる場合はコメントすることもあり。

* コメントのためのコメントをしない

コメントを追加する方が良いと考えて闇雲に追加して関数宣言とほぼ同じコメントを書くようなことをしてはいけない。
具体的な動作についてなど他に書くことはある。

* ひどい名前はコメントを付けずに名前を変える

コメントはひどい名前の埋め合わせに使う物ではない。

```C++
// replyに対してRequestで記述した制限を課す。
// 例えば、返ってくる項目数や合計バイト数など
void CleanReplay(Request request, Reply reply);
```

このコメントは「clean」の意味をわかりやすく説明しているだけである。
「制限を課す（enforce limit）」という言葉を関数名に入れた方が良い。

```C++
// 'reply'を'request'にある項目数やバイト数の制限に合わせる。
void EnforceLimitFromRequest(Request request, Reply reply);
```
この関数は自己文書化されている。
通常は「補助的なコメント」が必要になることはない。
「優れたコード　＞　ひどいコード　＋　優れたコメント」
ということだ。

### 2. 自分の考えを記録する

* 自分の考えをコメントに書くと良い
```C++
// このデータだとハッシュテーブルよりもバイナリーツリー方が40％早かった
// 左右の比較よりもハッシュの計算コストの方が高いようだ

// ヒューリスティックだと単語が漏れることがあるが仕方ない。100％は難しい。

// このクラスは汚くなってきている
// サブクラス'ResourceNode'を作って整理した方がいいかもしれない。
```
このように書くことで無駄な修正のために時間をかけることが減ったり、修正箇所がわかるようになる。

* コードの欠陥にコメントを付ける

| 記法 | 典型的な意味 |
| ---- | ---- |
| TODO: | 後で手を付ける |
| FIXME: | 既知の不具合のあるコード |
| HACK: | あまり綺麗じゃない解決策 |
| XXX: | 危険！　大きな問題がある |

* 定数にコメントを付ける
なぜその値を持っているのか背景を書くとよい

```python
NUM_THREADS = 8 # 値は「>= 2 * num_process」で十分
```
```C++
// 合理的な限界値。人間にこんなに読めない
const int MAX_RSS_SUBSCRIPTION = 1000;
```
```c++
image_quality = 0.72; // 0.72ならユーザーはファイルサイズと品質の面で妥協できる
```

### 3. 読み手の立場になって考える
「他の人」とはプロジェクトのことを熟知していない人のことである

* 質問されそうなことを想像する
* はまりそうな罠を告知する
「このコードを見てびっくりすることはなんだろう？どんな風に間違えて使う可能性があるだろう?」
```C++
// メールを送信する外部のサービスを呼び出している(1分でタイムアウト)
void SendEmail(string to, string subject, string body);
```
```python
// 実行時間はO(タグの数 * タグの深さの平均)なので、ネストの深さに気をつける
def FixBrokenHtml(html):...
```

* 全体像のコメント
全体像の理解が一番難しい。
新しいメンバーにコードを教えるためにこんなことを言うだろう
  * これはビジネスロジックとデータベースをつなぐグルーコードです。アプリケーションから直接使ってはいけません。
  * このクラスは複雑に見えますけど、単なるキャッシュです。システムのことは関知していません。

この内容は高レベルのコメントに書くべき情報だ。

```C++
// このファイルには、ファイルシステムに関する便利なインターフェースを提供
// するヘルパー関数が含まれています。ファイルのパーミッションなどを扱います。
```
短い適切な文章でもいいから書こう。
ないよりましだ。

* 要約コメント

関数内部でも「全体像」についてコメントすると良い

```python
def GenerateUserReport():
    # このユーザーのロックを獲得する
    ...
    # ユーザーの情報をデータベースから読み込む
    ...
    # 情報をファイルに書き出す
    ...
    # このユーザーのロックを解放する

```
関数の処理を箇条書きでまとめたため詳細を調べなくても関数の概要を把握できる

### 4. ライターズブロックを乗り越える

面倒くさくてもコメントをとりあえず書こう！
名にもないよりはましなはず。
コメントを書く手順は3つに分解できる。
* 頭の中にあるコメントをとにかく書き出す
* コメントを読んで改善が必要な物を見つける
* 改善する

### 5. コメントは簡潔にしておく

* 鍵となる考え
コメントは領域に対する情報の比率が高くなければならない

```C++
// intはCategoryType
// pairの最初のfloatは'score'
// 2つめは'weight'
typeof hash_map<int, pair<float, float> > ScoreMap;
```
このように3行で書くのは良くない。

次のように1行で書けるはずだ。

```C++
// CategoryType -> (score, weight)
typeof hash_map<int, pair<float, float> > ScoreMap;
```

### 6. 曖昧な代名詞を避ける

代名詞は物事を複雑にしてしまうため避けよう.

```C++
// データをキャッシュに入れる。ただし、先にそのサイズをチェックする。
```

これでは「その」が指している物が「データ」か「キャッシュ」かわからない。

以下が変更したコメント。

```C++
// データをキャッシュに入れる。ただし、先にデータのサイズをチェックする。

// データが十分に小さければ、それをキャッシュに入れる。
```

### 7. 歯切れの悪い文章を磨く

コメントを正確にすることは簡潔なコメントにつながることが多い。

```python
# これまでにクロールしたURLかどうかによって優先度を変える

# これまでにクロールしていないURLの優先度を高くする
```

下の方が単純で短く直接的だ。また、クロールしていないURLの優先度が高いという情報が増えている。

### 8. 関数の動作を正確に記述する

ファイルの行数を数える関数を書いているとする。

``` C++
// このファイルに含まれる行数を返す
int CoutLines(string filename){...}
```
「行」には様々な意味があるためこのコメントは正確でない。

最も簡単な実装は\nを数える物だ。

このときは
``` C++
// このファイルに含まれる改行文字('\n')を数える
int CoutLines(string filename){...}
```
### 9. 入出力のコーナーケースに実例を使う

コメントで動作をイメージし辛い場合は実例をコメントに書くと良い。

このときに実例が出来るだけ読み手に誤解を与えないものを選ぶことが大切。

### 10. コードの意図を書く
プログラマがコードを書いたときに考えていたことを書くと冗長検査の役割も果たすかも

### 11. 「名前付き引数」コメント

以下のような関数呼び出しだと何が渡されているのかよくわからない。

```python
 Connect(10, false)
```

以下のように書ける

```python
def Connect(timeout, userencryption):
  ...

Connect(timeout=10, user_encryption = False)

```

C++やjavaではこれは出来ない。しかしインラインコメントを使うことで同じような効果は得られる

```C++
void Connect(int timeout, bool use_encryption){...}

Connect(/* timeout_ms = */ 10, /* use_encryptin = */ false);
```

### 12. 情報密度の高い言葉を使う

例
* キャッシュ層
* 正規化
* ヒューリスティック
* ブルートフォース
* ナイーブソリューション