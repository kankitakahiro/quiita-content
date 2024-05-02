勉強したことをquiitaに保存していく.

## Qiita Preview の起動（プレビュー画面の表示）

本文の執筆は、ブラウザでプレビューしながら確認できます。  
ブラウザでプレビューするためには以下のコマンドを実行します。コマンド実行時に、Qiita に投稿している記事がダウンロードされます。

```console
npx qiita preview
```

コマンド実行すると、Qiita Preview(プレビュー画面)にアクセスすることが可能になります。  
プレビュー画面のデフォルトの URL は http://localhost:8888 です。

### 記事ファイルの配置について

1 つの記事の内容は、1 つの markdown ファイル（◯◯.md）で管理します。  
記事ファイルは`public`ディレクトリ内に含める必要があります。

```console
.
└─ public
   ├── newArticle001.md
   └── newArticle002.md
```

## Qiita CLI で記事を管理する

### 記事の作成

Qiita Preview 上の「新規記事作成」ボタン、または以下のコマンドで新規記事を作成できます。

```console
npx qiita new 記事のファイルのベース名
```

記事のファイルのベース名は自由に変更が可能です。

> 記事のファイル名を`newArticle001.md`にしたい場合は`newArticle001`にします。
>
> 例): `$ npx qiita new newArticle001`

作成された記事ファイルの中身は次のようになっています。

```yaml
---
title: newArticle001 # 記事のタイトル
tags:
  - "" # タグ（ブロックスタイルで複数タグを追加できます）
private: false # true: 限定共有記事 / false: 公開記事
updated_at: "" # 記事を投稿した際に自動的に記事の更新日時に変わります
id: null # 記事を投稿した際に自動的に記事のUUIDに変わります
organization_url_name: null # 関連付けるOrganizationのURL名
slide: false # true: スライドモードON / false: スライドモードOFF
ignorePublish: false # true: `publish`コマンドにおいて無視されます（Qiitaに投稿されません） / false: `publish`コマンドで処理されます（Qiitaに投稿されます）
---
# new article body
```

ファイルの上部には`---`に挟まれる形で記事の設定（Front Matter）が含まれています。  
ここに記事のタイトル（title）やタグ(tags)などを yaml 形式で指定します。

### 記事の投稿・更新

Qiita Preview 上の「記事を投稿する」ボタン、または以下のコマンドで投稿・更新ができます。

```console
npx qiita publish 記事のファイルのベース名
```

以下のコマンドで全ての記事を反映させることができます。

```console
npx qiita publish --all
```

`--force`オプションを用いることで、強制的に記事ファイルの内容を Qiita に反映させます。

```console
npx qiita publish 記事ファイルのベース名 --force
# -f は --force のエイリアスとして使用できます。
npx qiita publish 記事ファイルのベース名 -f
```

### 記事の削除

Qiita CLI、Qiita Preview から記事の削除はできません。  
`public`ディレクトリから markdown ファイルを削除しても Qiita 上では削除はされません。

[Qiita](https://qiita.com)上で記事の削除を行なえます。
