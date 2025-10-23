---
title: リーダブルコード　8章　巨大な式を分割する
tags:
  - リーダブルコード
  - 命名規則
private: true
updated_at: '2025-10-23T01:19:13+09:00'
id: ff28f7d4a78e28800886
organization_url_name: null
slide: false
ignorePublish: false
---

- [1. 説明変数](#1-説明変数)
- [2. 要約変数](#2-要約変数)
- [3. ド・モルガンの法則を使う](#3-ドモルガンの法則を使う)
- [4. 短絡評価の悪用](#4-短絡評価の悪用)
- [5. 例：複雑なロジックと格闘する](#5-例複雑なロジックと格闘する)
- [6. 巨大な文を分割する](#6-巨大な文を分割する)
- [7. 式を簡潔にするもう1つの創造的な方法](#7-式を簡潔にするもう1つの創造的な方法)


コードが大きくなるとそれだけ理解が難しくなる。

* カギとなる考え
巨大な式は飲み込みやすい大きさに分割する

### 1. 説明変数

式を簡単に分割するには式を表す変数を使えばいい。この変数を説明変数という。

例
```python
if line.split(':')[0].strip() == "root": # 説明変数なし

username = line.split(':')[0].strip()    # 説明変数あり
if  username == 'root':
```

### 2. 要約変数

大きなコードの塊を小さな名前に置き換えて、管理や把握を簡単にする変数のことを要約変数という。

```java
if (request.user.id == documaent.owner_id){
    // ユーザーはこの文書を編集できる
}
...
if (request.user.id != document.owner_id){
    // 文書は読み取り専用
}
```
`request.user.id != document.owner_id`は変数が5つも入っているためわかりにくい。

このコードが言いたいことは「ユーザーは文書を所持しているか？」なので要約変数に追加をするともっと明確になる。

```java
final boolean user_owns_document = (request.user.id == document.owner_id)
if (user_owns_document){
    // ユーザーはこの文書を編集できる
}
if (!user_owns_document){
    // 文書は読み取り専用
}
```
user_owns_documentを最上部に定義したことで「この関数で参照する概念」を事前に伝えることができるようになった。

### 3. ド・モルガンの法則を使う

1. not (a or b or c)   <=> (not a) and (not b) and (not c)
2. not (a and b and c) <=> (not a) or  (not b) or  (not c)

この法則を使うと論理式を読みやすくなる。

```C++
if (!(file_exists && !is_protected)) Error("Sorry, could not read file.") // ド・モルガン適用前

if (!file_exists || is_protected) Error("Sorry, could not read file.")    // ド・モルガン適用後
```

### 4. 短絡評価の悪用

ブール演算子を使うものは短絡評価になりやすい。`if(a||b)`では`a`が`true`のとき`b`は評価されない

```C#
assert((!(bucket = FindBucket(key))) || !bucket->IsOccupied());
```
これは「このキーのバケツを取得する。もしバケツがnullじゃなかったら、中身が入っていないか確認する」という意味である。
```C#
bucket = FindBucket(key);
if (bucket != NULL) assert(!bucket->IsOccupied());
```
全く同じ内容で2行になっているが内容が理解しやすくなった。

* カギとなる考え
「頭がいい」コードに気を付ける。後でほかの人がコードを読むときにわかりにくくなる。

### 5. 例：複雑なロジックと格闘する

場合分けや条件が多すぎる場合は全く違った手法を考えてみることも大事だ。

最初は簡単だったのに複雑なコードになる場合はもっと**簡単な方法**がある。

解決策の一つに「反対」から考えてみるという手がある。

### 6. 巨大な文を分割する

繰り返し行われる同じ式や文字列は要約変数としてまとめるとわかりやすくなる。

これにより以下のような効果が期待できる。

* タイプミスを減らす
* 横幅が縮まり読みやすくなる
* クラス名を変更するときに一か所を変更すればよくなる
  
### 7. 式を簡潔にするもう1つの創造的な方法

同じ操作を繰り返しているときはマクロを組んでみることも考えると良い。
