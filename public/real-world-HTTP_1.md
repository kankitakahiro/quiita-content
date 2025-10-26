---
title: Real World HTTP　1章　ブラウザは何をしているのか
tags:
  - Go
  - HTTP
  - ブラウザ
private: true
updated_at: '2025-10-27T05:48:21+09:00'
id: ef7492d26237e34f25e8
organization_url_name: null
slide: false
ignorePublish: false
---

- [1.2 ウェブページが表示されるまで](#12-ウェブページが表示されるまで)
  - [1.2.1 最初のページの表示](#121-最初のページの表示)
    - [DNSをコマンドで試す](#dnsをコマンドで試す)
    - [ブラウザがサーバーに送るメッセージ](#ブラウザがサーバーに送るメッセージ)
    - [サーバーが返してくるコンテンツ](#サーバーが返してくるコンテンツ)
  - [1.2.2 リンクをクリック](#122-リンクをクリック)
  - [1.2.3 検索](#123-検索)
  - [1.2.4 ログイン](#124-ログイン)
    - [ログインフォームのHTML](#ログインフォームのhtml)
    - [ログインフォームからサーバーに送られる内容](#ログインフォームからサーバーに送られる内容)
    - [リダイレクトさせるためにサーバーが返してくるコンテンツ](#リダイレクトさせるためにサーバーが返してくるコンテンツ)

## 1.2 ウェブページが表示されるまで

ブラウザが最初にページを要求する「リクエスト」とサーバーが返す「レスポンス」の2種類のメッセージのやりとりがある。

### 1.2.1 最初のページの表示

ブラウザはまずURLを分解する。

 | 部分 | 値 |
 |---------|---------|
 | スキーマ  | https  |
 | ホスト名  | github.com  |
 | パス  | /oreilly-japan/real-world-http  |
 | ハッシュ | #readme |

 ブラウザはデフォルトのホスト名を見て`http://`か`https://`を自動で付与する。

 ホスト名がわかるとサーバーのIPアドレスを取得する。

 ドメイン名からIPアドレスを取得するサービスである、**DNSサーバー**に問い合わせる。

ブラウザはパソコンやスマートフォンのネットワーク設定にあるDNSサーバー設定を見て問い合わせ先を決定する。

基本はインターネットサービスプロバイダーや電話回線のキャリアが提供している。

#### DNSをコマンドで試す
```shell-session
$ dig github.com
;; ANSWER SECTION:
github.com.             0       IN      A       20.27.177.113
```

IPアドレスがわかるとそのサーバーにHTTPのリクエストを送信する。

送信の方式はいくつかあり、この方式のことを**スキーマ**と呼ぶ。

#### ブラウザがサーバーに送るメッセージ
```shell-session
GET /oreilly-japan/real-world-http HTTP/1.1
Host: github.com
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,⏎
image/apng,*/*;q=0.8
Accept-Encoding: gzip, deflate, br
Accept-Language: ja-JP,ja;q=0.9,en-US;q=0.8,en;q=0.7
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko)⏎
Chrome/98.0.4758.82 Safari/537.36
```

ブラウザがサーバーに対して送るのは「このページが欲しい」という情報で**GET**がそれに対応する。他にも**POST**や**DELETE**がある。これらを**メソッド**と呼ぶ。

1行目はメソッド以外にパス情報が含まれる。

「名前：値」のリストは**フィールド**と呼ばれる。

先頭にある物は「ヘッダーフィールド」であり、「ヘッダー」と呼ばれることが多い。

Host:は「私が送信したサーバーはこれだ」というメッセージであり、それ以外のフィールドはブラウザがサーバーに対して自己紹介をしている。

* Accept:は私（ブラウザ）が処理できるデータフォーマットはこれです、というリスト
* Accept-Encoding:は私が処理できる高速化のためのデータ圧縮のアルゴリズムはこれです、とい
うリスト
* Accept-Language:は私を使っているユーザー（人間）が読める言語はこれです、というリスト
* User-Agent:は私の種類はこれです、という名前

サーバーはブラウザに最適な形式でコンテンツを返す。

#### サーバーが返してくるコンテンツ

```
HTTP/1.1 200 OK
Content-Encoding: gzip
Content-Type: text/html; charset=utf-8
Date: Sat, 27 May 2023 02:54:02 GMT
Server: GitHub.com
<!DOCTYPE html>
<html lang="en" data-color-mode="auto" data-light-theme="light" data-dark-theme="dark" dataa11y-
animated-images="system">
<head>
<meta charset="utf-8">
<script type="application/javascript" src="https://github.githubassets.com/assets/code-menu.
js"></script>
: （略）
```
末尾にはブラウザが欲しかったHTMLファイルが付いている。

後ろの空行の後のデータ（ここではHTML）は**ボディ**と呼ばれる。

その前にはサーバーが正しく処理できたことを示すフィールドが付いている。

リクエストされたパスが間違っ
ていたり、ログインが必要だった場合には、200 OK以外のテキストがここに書かれる。

Content-EncodingとContent-Typeには実際にサーバーが返した物の情報が入っている。

ブラウザはサーバーから帰ってきたファイルの種別がtext/htmlであることを確認し、新しいページのロードを始める。HTMLのファイルの中には画像やスタイルシートのリンクが書かれている。

ブラウザはこの表示に必要なファイルも、HTTPを使って芋づる式に取得する。

スタイルシートはtext/css、JavaScriptはtext/javascriptのように、Content-Typeが異なるだけでHTTPのGETメソッドを使い、コンテンツに格納されて伝達される点は同じである。

ページに必要なファイルがそろったらブラウザはHTMLのレンダリングエンジンに情報を渡しユーザに見せる。

### 1.2.2 リンクをクリック

基本的には最初のリクエストと同じだがヘッダーリストに次のような遷移前の情報のヘッダーフィールドが追加されている。

```
Referer: https://github.com/oreilly-japan/real-world-http
```

画面をリフレッシュするかはブラウザが決めており、ブラウザが表示可能なコンテンツ（HTMLやJPEG/PNGなどの画像）であれば、ブラウザの画面をリセットして表示し、表示可能で
ないコンテンツの場合は、ブラウザはそのファイルをコンピューター上に保存しようする。

### 1.2.3 検索

ページのフォームに検索ワードを入れて検索を行うとURLバーには`https://github.com/oreilly-japan/real-world-http/search?q=x-www-form-urlencode`と表示される。

ウェブサイトとしては`/oreilly-japan/real-world-http/search`がリクエストを受けるが、検索ワードはURLの一部とし
て表現される。

リクエストはGETだがパスが変わり、検索用語は`?q=`として表現される。この？以降を**クエリーパラメーター**と呼ぶ。

Githubサーバーは内部で処理するときにこの部分を検索エンジンに渡して検索する。

### 1.2.4 ログイン

ログインではブラウザから認証に必要な情報を送付し、自分は登録されたユーザーであるとサーバーに確認してもらう。

ログインページにアクセスするとログインフォームがあり、ログインページの情報にはGETメソッドを使うが、ログインではPOSTメソッドを使う。

#### ログインフォームのHTML
```html
<form method="post" action="login">
<label for="email">Email Address</label>
<input type="email" name="email" value="">
<label for="password">Password</label>
<input type="password" id="password" name="password" value="">
<input type="submit" name="login" value="ログイン">
</form>
```

フォーム自体はGETメソッドでのリクエストも可能ではあるがログインやデータの変更などのなにかしらの副作用のあるアクセスにはPOSTメソッドを使用する。

HTTPには他のメソッドもあるが、javascriptを使わずに送信できるのはGETとPOSTだけである。

送信ボタンを押すと次の内容がサーバーに送られる。

#### ログインフォームからサーバーに送られる内容

```
POST /ebook/login HTTP/1.1
Host: www.oreilly.co.jp
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 ⏎
(KHTML, like Gecko) Chrome/98.0.4758.82 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,⏎
image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate, br
Accept-Language: ja-JP,ja;q=0.9,en-US;q=0.8,en;q=0.7
Origin: https://www.oreilly.co.jp
Referer: https://www.oreilly.co.jp/ebook/login
Content-Length: 92
Content-Type: application/x-www-form-urlencoded

email=test%40example.com&password=yourpassword&login=%E3%83%AD%E3%82%B0%E3%82%A4%E3%83%B3
```

サーバーからのHTMLレスポンスと同じように、空行をあけてコンテンツとしてテキストが含まれている。

これはフィールドとは異なる内容を送信している。内容はapplicationx-www-formurlencodedという形式で表現された情報であることがContent-Type:フィールドを見るとわかる。

また、Content-Length:を見ると、92文字の長さのテキストであることがわかる。

POSTではダウンロードの逆で様々な情報をアップロード出来る。

検索などの「何度行っても結果は変わらない」操作以外のインターネット上の買い物の処理、SNSの書き込みなどは全てこのPOSTになる。

サーバーはこのユーザーIDとパスワードに対してレスポンスを返す。

成功時はブラウザに名にもないページを一瞬表示してユーザーの書庫のページに遷移する。
サーバーはこのリダイレクトのために次のようなレスポンスを返す。

#### リダイレクトさせるためにサーバーが返してくるコンテンツ

```
HTTP/1.1 302 Found
Date: Mon, 29 May 2023 08:49:04 GMT
Location: https://www.oreilly.co.jp/ebook/bookshelf
Set-Cookie: osid=24882b5c30a628b44878f91fe0f5ed38; path=/
Content-Type: text/html; charset=iso-8859-1
Content-Length: 225
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>302 Found</title>
</head><body>
<h1>Found</h1>
<p>The document has moved <a href="https://www.oreilly.co.jp/ebook/bookshelf">here</a>.</p>
</body></html>
```

ブラウザは302Foundというレスポンスを受けると、Locationフィールドに含まれるパスに遷移する。

もう1つの大切な要素にSet-Cookieフィールドがある。これが付与されると、ブラウザは次のCookieフィールドを使って、サーバーへのリクエストと一緒に、この情報を毎回送るようになる。クッキーがあることで毎回IDとパスワードを送付しなくても、サーバーが「この人は承認済みのあのユーザーだ」と判断でき、コンテンツのアクセスを許可できる。


