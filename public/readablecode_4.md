---
title: リーダブルコード　4章
tags:
  - リーダブルコード
  - 命名規則
private: true
updated_at: '2024-05-02T14:29:10+09:00'
id: 11c059098993219d53b3
organization_url_name: null
slide: false
ignorePublish: false
---
# 美しさ

----------------------------

- [美しさ](#美しさ)
    - [1. なぜ美しさが大切なのか](#1-なぜ美しさが大切なのか)
    - [2. 一貫性のある簡潔な改行位置](#2-一貫性のある簡潔な改行位置)
_________________________

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
