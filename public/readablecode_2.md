---
title: リーダブルコード　2章　名前に情報を詰め込む
tags:
  - リーダブルコード
  - 命名規則
private: true
updated_at: '2025-10-27T00:52:38+09:00'
id: 1b55d14f3a3b3dd7b295
organization_url_name: null
slide: false
ignorePublish: false
---
- [明確な単語を選ぶ](#明確な単語を選ぶ)
- [汎用的な名前を避ける](#汎用的な名前を避ける)
    - [意味のない名前](#意味のない名前)
  - [ループイテレータ](#ループイテレータ)
    - [ループイテレータの例](#ループイテレータの例)
- [抽象的な名前よりも具体的な名前を使う](#抽象的な名前よりも具体的な名前を使う)
- [名前の長さを決める](#名前の長さを決める)
- [名前のフォーマットで情報を伝える](#名前のフォーマットで情報を伝える)
_________________________

* カギとなる考え
名前に情報を詰め込む

### 明確な単語を選ぶ

* カギとなる考え
気取った言い回しよりも明確で正確なほうが良い

例 右の代替案の方が情報量の多い単語!?

| 単語 | 代替案 |
|---------|---------|
| send  | deliver, dispatch, announce, distribute, route  |
| find  | search, extract, locate, recover  |
| start  | launch, create, begin, open  |
| make  | create, set up, build, generate, compose, add, new |
|   |   |
|   |   |

### 汎用的な名前を避ける

* カギとなる考え

エンティティの値や目的を表した名前を選ぼう

##### 意味のない名前

retval, tmp, foo

情報の一時的な保存のために使用され、生存期間も数行しかない場合は意味のない名前で上げた変数でも充分である。

#### ループイテレータ

##### ループイテレータの例
i, j, k, iter

インデックスやループイテレータでよく使われる。基本的にはこれで問題はない。
しかし、イテレータが複数ある時はもっと明確な名前を付けることが好ましい。

* カギとなる考え
tmp,it,retvalのような汎用的な名前を使うときは、それ相応の理由を用意しよう。

### 抽象的な名前よりも具体的な名前を使う

直行する概念は別々に名前を定義すると良い
例：ローカル用の特別なデータベースを設定して使う場合 -> --run_locally_database

フォーマットが重要ならばフォーマットがわかるような名前付けをする。
例:IDのフォーマットが16進数であることを明確にする -> hex_id

単位のある値を入れるならば単位がわかるようにする。
例：
| 関数の仮引数 | 単位をつかした仮引数 |
|---------|---------|
| Start(int delay) | delay -> delay_secs |
| CreateCache(int size) | size -> size_mb |
| ThrottleDownload(float limmit) | limmit -> max_kbps |
| Rotate(float angle) | angle -> degrees_cw |

危険や注意喚起する情報も入れたほうが良い。

例: untrustedUrl, unsafeMessageBody

- 追加：ハンガリアン記法

| 変数名 | 意味 |
|---------|---------|
| pLast | あるデータ構造の最後の要素を指すポインタ(p) |
| pszBuffer | ゼロ終端(z)の文字列(s)バッファを指すポインタ(p) |
| cch | 文字(ch)のカウント(c) |
| mpcopx | カラーポインタ(pco)からX軸のポインタ(px)を指すマップ(m) |

### 名前の長さを決める

1. スコープが小さければ短い名前でもよい

2. 頭文字と省略形
新しいチームメイトが名前の意味を理解できるかを意識する。

3. 不要な単語を投げ捨てる

### 名前のフォーマットで情報を伝える

クラス名 -> CamelCase
変数名 -> lower_separated
定数 -> kConstantName
#defineマクロ -> MACRO_NAME
クラスのメンバ変数 -> offset_　　　後ろがアンダースコア

javascriptでは
コンストラクタは大文字で始める
通常の関数は小文字で始める
jQueryのライブラリ関数 -> 変数の頭に$

HTML,CSSでは
idの区切り文字 -> アンダースコア (middle_column)
classの区切り文字 -> ハイフン (main-content)
```html
<div id="middle_column" class="main-content">
```

プロジェクトで一貫を持たせること！！！！！
