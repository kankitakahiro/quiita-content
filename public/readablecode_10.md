---
title: リーダブルコード　10章　無関係な下位問題を抽出する
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

エンジニアリングとは

-> 大きな問題を小さな問題に分割して解決策を組み立てること。

無関係の下位問題を積極的に見つけて抽出することが大事になる。

考えること

1. 関数やコードブロックを見て「このコードの高レベルの目標は何か？」と自問する
2. コードの各行に対して「高レベルの目標に直接的に効果があるのか？あるいは無関係の下位問題を解決しているのか？」と自問する。
3. 無関係の下位問題を解決しているコードが相当量あれば、それらを抽出して別の関数にする。

### 1. 入門的な例：findClosestLocation()

高レベルな目標：「与えられた地点から最も近い場所を見つけること」

```javascript
// 与えられた緯度経度に最も近い'array'をかえす。
// 地球が完全な球体であることを前提としている。
var findClosetLocation = function(lat,lng,array){
    var closest;
    var closest_dist = Number.MAX_VALUE;
    for (var i = 0; i < array.length; i += 1){
        // 2つの地点をラジアンに変換する
        var lat_rad = radians(lat);
        var lng_rad = radians(lng);
        var lat2_rad = radians(array[i].latitude);
        var lng2_rad = radians(array[i].longitude);

        // 「球面三角法の第2余弦定理」の公式を使う
        var dist = Math.acos(Math.sin(lat_rad) * Math.sin(lat2_rad) + 
                             Math.cos(lat_rad) * Math.cos(lat2_rad) *
                             Math.cos(lng2_rad - lng_rad);
        )
        
        if (dist < closest_dist){
            closest = array[i];
            closest_dist = dist;
        }
    }
    return closest;
};
```

ループ内のコードは無関係の下位問題を扱っている。

-> 「2つの地点（緯度経度）の球面距離を算出する」

コード量が多いため新しい関数spherical_distance()に抽出する。

```javascript

var spherical_distance = function (lat1, lng1, lat2, lng2){
    var lat_rad = radians(lat1);
    var lng_rad = radians(lng1);
    var lat2_rad = radians(lat2);
    var lng2_rad = radians(lng2);

    // 「球面三角法の第2余弦定理」の公式を使う
    var dist = Math.acos(Math.sin(lat_rad) * Math.sin(lat2_rad) + 
                            Math.cos(lat_rad) * Math.cos(lat2_rad) *
                            Math.cos(lng2_rad - lng_rad));
};

var findClosetLocation = function(lat,lng,array){
    var closest;
    var closest_dist = Number.MAX_VALUE;
    for (var i = 0; i < array.length; i += 1){
        var dist = spherical_distance(lat, lng, array[i].latitude, array[i].longitude);
        
        if (dist < closest_dist){
            closest = array[i];
            closest_dist = dist;
        }
    }
    return closest;
};

```

これによりspherical_distance()は個別にテストでき、再利用可能な関数として定義できた。

### 2. 純粋なユーティリティコード

基本的なタスクはプログラミング言語の組み込みライブラリとして実装されている。

しかし、たまに自分で用意する必要がある。

このとき、自分で書き、複数のプロジェクトで仕えるユーティリティコードにすれば良い。

### 3. その他の汎用コード

```javascript
ajax_post({
    url: 'http://example.com/submit',
    data: data,
    on_success: function(response_data) {
        var str = "{\n";
        for (var key in response_data){
            str += " " + key + " = " + response_data[key] + "\n";
        }
        alert(str + "}");
        // 引き続き'response_data'の処理
    }
})
```

このコードの高レベルの目標は「サーバーをAjaxで呼び出してレスポンスを処理する」である。
しかし、コードの大部分は「ディクショナリを綺麗に印字する」という無関係の下位問題を解決しようとしている。

このようなコードを抽出すると以下のようになる。

```javascript
var format_pretty = function(obj){
    var str = "{\n";
    for (var key in obj){
        str += " " + key + " = " + obj[key] + "\n";
    }
    return str + "}";
}

```

この改善により、呼び出し側のコードは簡潔になるし、再利用も出来る。

また、「コードが独立していれば、format_pretty()の改善が楽になる」

### 4. 汎用コードをたくさん作る

無関係の下位問題を抽出したら複数のプロジェクトで再利用できるため簡単に共有できる特別なディレクトリ、(例：util)を用意するとよい。

プロジェクトから完全に切り離されているため汎用コードは素晴らしい。

プログラミングで大切なことは下位問題を分離して処理できるかだ。

### 5. プロジェクトに特化した機能

完全に独立していなくても下位問題を取り除くことは有効になる。

どこに置くかは後でよく、とりあえず抽出しよう！

### 6. 既存のインターフェースを簡潔にする。

「理想とほど遠いインターフェースに妥協することはない」

自分でラッパー関数を用意して汚いインターフェースを覆い隠そう。

### 7. 必要に応じてインターフェースを整える

多くのコードは他のコードを支援するために存在する。別の関数に分離するのはこのようなコードになる。

高レベルの目標：「ユーザーの情報を暗号化してＵＲＬに含める」

型や暗号化などのステップを踏むうちにコードの大部分は「pythonのオブジェクトをＵＲＬセーフな文字列にする」に置き換わってしまう。

このような下位問題は抽出し、本質的なロジックを扱うコードは簡潔になる。

### 8. やり過ぎ

小さな関数を作ると逆に読みにくくなってしまう。そのため分割しすぎは良くない。

合わせて読むと良い本

* リファクタリング - プログラムの体質改善テクニック
* ケントベックのsmalltalkベストプラクティス・パターン - シンプルデザインへの宝石集