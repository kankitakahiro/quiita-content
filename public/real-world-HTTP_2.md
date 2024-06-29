---
title: Real World HTTP　2章　HTTP/1.0の世界：基本となる4つの要素
tags:
  - ブラウザ
  - HTTP
  - Go
private: true
updated_at: 
id: 
organization_url_name: null
slide: false
ignorePublish: false
---

### 2.1.1 テストエコーサーバーの実行

#### エコーサーバー
```go
package main

import (
    "fmt"
    "log"
    "net/http"
    "net/http/httputil"
)

// handler関数は、HTTPリクエストを処理し、HTTPレスポンスを返す。
// 引数:
//   w: http.ResponseWriter - クライアントへのレスポンスを作成するために使用。具体的には、レスポンスのヘッダ、ステータスコード、ボディなどを設定・送信するために使う。
//   r: *http.Request - クライアントからのリクエスト情報が含まれる。具体的には、メソッド、URL、ヘッダ、ボディなどが含まれる。
func handler(w http.ResponseWriter, r *http.Request) {
    // クライアントからのリクエストをダンプ（すべての情報を文字列に変換）する。
    dump, err := httputil.DumpRequest(r, true)
    if err != nil {
        // ダンプに失敗した場合、500 Internal Server Errorを返す。
        http.Error(w, fmt.Sprint(err), http.StatusInternalServerError)
        return
    }
    // ダンプしたリクエスト情報を標準出力に表示する。
    fmt.Println(string(dump))
    // クライアントに対してHTMLレスポンスを返す。
    fmt.Fprintf(w, "<html><body>hello</body></html>\n")
}

// main関数は、HTTPサーバーを初期化し、指定されたポートでリッスンを開始する。
// 出力:
//   サーバーの起動ログおよびエラーログを標準出力に出力する。
func main() {
    var httpServer http.Server
    // トップのパス"/"にアクセスがあったときにhandler関数を呼び出すように設定する。
    http.HandleFunc("/", handler)
    // サーバーが18888ポートで起動することをログに出力する。
    log.Println("start http listening :18888")
    // サーバーのアドレスとポートを設定する。
    httpServer.Addr = ":18888"
    // サーバーを起動し、エラーが発生した場合はログに出力する。
    log.Println(httpServer.ListenAndServe())
}
```

18888ポートで起動するように設定されている。本来HTTPは80番を用いるが若い番号は**ウェルノウンポート（Well Known Port）**として扱われる。番号ごとにようとがほぼ決まっており、ウェブやFTPなどのネットワークのクライアントは特別な指定がなければウェルノウンポートにアクセスする。80番の代替には3000、8000、8080、8888番が人気であるが今回は18888番を使っている。

### 2.2　HTTP/0.9でできることを試す

HTTP/0.9はとてもシンプルなプロトコルであり、テキスト情報が書かれたページのパスをサーバーに指定してそれを取得するだけのプロトコル。
ここでは模擬的に1.0を使用する。

curlコマンドの実行例
```shell-session
$ curl --http1.0 http://localhost:18888/greeting
```

サーバー側のログ
```
GET /greeting HTTP/1.0
Host: localhost:18888
Connection: close
Accept: */*
User-Agent: curl/7.52.1
```

ウェブページのサーバーに要求し、その返事としてWebサイトの内容を受け取ります。
