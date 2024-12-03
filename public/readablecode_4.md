---
title: リーダブルコード　4章　美しさ
tags:
  - リーダブルコード
  - 命名規則
private: true
updated_at: '2024-12-04T01:07:55+09:00'
id: dff77a163af8e92d441f
organization_url_name: null
slide: false
ignorePublish: false
---
- [1. なぜ美しさが大切なのか](#1-なぜ美しさが大切なのか)
- [2. 一貫性のある簡潔な改行位置](#2-一貫性のある簡潔な改行位置)
- [3. メソッドを使った整列](#3-メソッドを使った整列)
- [4. 縦の線をまっすぐにする](#4-縦の線をまっすぐにする)
- [5. 一貫性と意味のある並び](#5-一貫性と意味のある並び)
- [6. 宣言をブロックにまとめる](#6-宣言をブロックにまとめる)
- [7. コードを「段落」に分割する](#7-コードを段落に分割する)
- [8. 個人的な好みと一貫性](#8-個人的な好みと一貫性)
____________________

### 1. なぜ美しさが大切なのか

プログラミングの時間のほとんどがコードを読む時間である。
そのため流し読みができれば使いやすいコードだといえるだろう。

美しいコードを書くための3つの原則

* 読み手が慣れているパターンと一貫性のあるレイアウトを使う。
* 似ているコードは似ているように見せる
* 関連するコードをまとめてブロックにする

### 2. 一貫性のある簡潔な改行位置

余計な改行などが入り、似ているコードにもかかわらず見た目が違うと可読性が下がる。
コードの見た目を一貫性のあるものにするには適切な改行を入れるようにしよう。（コメントも整列させる）

```java
public class PerformanceTester {
    public static final TopConnectionSimulator wifi =
        new TopConnectionSimulator(
            500,   /* Kbps */
            80,    /* millisecs latency */
            200,   /* jitter */
            1,     /* packet loss */);

    public static final TopConnectionSimulator t3_fiber =
        new TopConnectionSimulator(
            45000, /* Kbps */
            10,    /* millisecs latency */
            0,     /* jitter */
            0,     /* packet loss */);

    public static final TopConnectionSimulator cell =
        new TopConnectionSimulator(
            100,   /* Kbps */
            400,   /* millisecs latency */
            250,   /* jitter */
            5,     /* packet loss */);
}
```

このようなコードには一貫性があり楽に目を通すことができる。
しかし、同じコメントが3回言書かれていることが気になる。

```java
public class PerformanceTester {
    // TopConnectionSimulator(thorouput, latency, jitter, packet_loss)
    //                           [kbps]     [ms]    [ms]    [percent]
    public static final TopConnectionSimulator wifi =
        new TopConnectionSimulator(500,   80,  200, 1);

    public static final TopConnectionSimulator t3_fiber =
        new TopConnectionSimulator(45000, 10,  0,   0);

    public static final TopConnectionSimulator cell =
        new TopConnectionSimulator(100,   400, 250, 5);
}
```

このようにコメントを最上部に移動して仮引数を一行で書くようにすることでより簡潔な表組みにデータが並ぶようになった。

### 3. メソッドを使った整列

人事データベースを考える

// 「Doug Adams」のようなpartial_nameを「Mr. Douglas Adams」に変える
// それができなければerrorに説明文を入れる
```C++
string ExpandFullName(DarabaseConnection dc, string partial_name, string* error);
```

```C++
DatabaseConnection database_connection;
assert(ExpandFullName(database_connection, "Doug Adams", &error)
    == "Mr. Douglas Adams");
assert(error == "");
assert(ExpandFullName(database_connection, " Jake Brown ", &error)
    == "Mr. Jacob Brown III");
assert(error == "");
assert(ExpandFullName(database_connection, "No such Guy", &error) == "");
assert(error == "no match found");
assert(ExpandFullName(database_connection, "John", &error) == "");
assert(error == "more than one result");
```
このコードは見た目が悪い。シルエットは不細工で一貫性のあるパターンもない。
改行の位置を変えなければいけないが`assert(ExpandFullName(database_connection, ...`
や`error`などの文字列が邪魔している。
このコードを本当の意味で改善するにはヘルパーメソッドを使う必要がある。

```C++
CheckFullName("Doug Adams", "Mr. Douglas Adams", "");
CheckFullName(" Jak Brown ", "Mr. Jake Brown III", "");
CheckFullName("No such Guy", "", "no such found");
CheckFullName("john", "", "more than one result");
```

これなら引数の異なる4つのテストがあることがわかる。

```C++
void CheckFullName(string partial_name,
                   string expected_full_name,
                   string expected_error) {
    // database_connectionはクラスのメンバになっている
    string error;
    string full_name = EcpandFullName(database_connection, partial_name, &error);
    assert(error == expected_error);
    assert(full_name == expected_full_name);
}
```

ここでの目標はコードの見た目を美しくすることだったがこの変更によってうれしい副作用がもたらされた。
* 重複を排除したことでコードが簡潔になった。
* テストケースの重要な部分（名前やエラー文字列）が見やすくなった。
* テストの追加が簡単になった。

### 4. 縦の線をまっすぐにする

列を整列させるとコードが読みやすくなる。
CheckFullName()引数を例に考えてみる。
```C++
CheckFullName("Doug Adams" , "Mr. Douglas Adams" , "");
CheckFullName(" Jak Brown ", "Mr. Jake Brown III", "");
CheckFullName("No such Guy", ""                  , "no such found");
CheckFullName("john"       , ""                  , "more than one result");
```
2番目と3番目の引数がわかりやすくなった。
またこうすることでタイプミスをみつけやすくなる。

### 5. 一貫性と意味のある並び

どんな順番に並べても構わない場合は意味のある順番で並べるといい。

* 対応するHTMLフォームの`<input>`フィールドと同じ並び順にする
* 「最重要」なものから重要度順に並べる
* アルファベット順に並べる

どの並び順にするにしても一連のコードでは同じ並び順を使うべき。

### 6. 宣言をブロックにまとめる

人間の脳はグループや階層を1つの単位として考える。

```C++
class FrontendServer{
    public:
    FrontendServer();
    void ViewProfile(HttpRequest* request);
    void OpenDatabase(string location, string user);
    void SaveProfile(HttpRequest* request);
    string ExtractQueryParam(HttpRequest* request, string param);
    void ReplyOK(HttpRequest* request, string html);
    void FindFriends(HttpRequest* request);
    void ReplyNotFound(HttpRequest* request, string error);
    void CloseDatabase(string location);
    ~FrontendServer();
};
```
このコードはメソッドの概要をすぐに把握できるような配置になっていない。
論理的なグループに分けると良いだろう。

```C++
class FrontendServer{
    public:
    FrontendServer();
    ~FrontendServer();

    // ハンドラ
    void ViewProfile(HttpRequest* request);
    void SaveProfile(HttpRequest* request);
    void FindFriends(HttpRequest* request);

    // リクエストとリプライのユーティリティ
    string ExtractQueryParam(HttpRequest* request, string param);
    void ReplyOK(HttpRequest* request, string html);
    void ReplyNotFound(HttpRequest* request, string error);

    // データベースのヘルパー
    void OpenDatabase(string location, string user);
    void CloseDatabase(string location);
};
```
概要が把握しやすくなった。

### 7. コードを「段落」に分割する

* 似ている考えをグループにまとめて、他の考えと分けるため
* 視覚的な「踏み石」を提供できる。ページの中で自分の場所を見失ってしまう。
* 段落単位で移動できるようになる。

```python
# ユーザーのメール帳をインポートして、システムのユーザーと照合する
# そして、まだ友達になっていないユーザーの一覧を表示する
def suggest_new_friends(user, email_password):
    friends = user.friends()
    friend_emails = set(f.email for f in friends)
    contacts = import_contacts(user.email, email_password)
    contact_emails = set(c.email for c in contacts)
    non_friend_emails = contact_emails - friend_emails
    suggested_friends = User.objects.select(email__in=non_friend_emails)
    display['user'] = user
    display['friends'] = friends
    display['suggested_friends'] = suggested_friends
    return render("suggested_friends.html", disply)
```

この一塊のコードは誰も読む気がしない。
このコードを段落に分割すると良い。

```python
def suggest_new_friends(user, email_password):
    # ユーザーの友達のメールアドレスを取得する
    friends = user.friends()
    friend_emails = set(f.email for f in friends)

    # ユーザーのメールアカウントからすべてのメールアドレスをインポートする
    contacts = import_contacts(user.email, email_password)
    contact_emails = set(c.email for c in contacts)

    # まだ友達になっていないユーザーを探す
    non_friend_emails = contact_emails - friend_emails
    suggested_friends = User.objects.select(email__in=non_friend_emails)

    # それをページに表示する
    display['user'] = user
    display['friends'] = friends
    display['suggested_friends'] = suggested_friends

    return render("suggested_friends.html", disply)
```

段落ごとに要約コメントを追加した。
これで読みやすくなった。

### 8. 個人的な好みと一貫性
* 鍵となる考え
  一貫性のあるスタイルは「正しい」スタイルよりも大切だ
