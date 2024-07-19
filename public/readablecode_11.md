---
title: リーダブルコード　11章　一度に１つのことを
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

* 鍵となる考え
コードは１つずつタスクを行うようにしなければならない

1. コードが行っている「タスク」を列挙する。
2. タスクを出来るだけ異なる関数に分割する。

### 1. タスクは小さく出来る

例：ユーザーは賛成と反対を投票できる。賛成＋１、反対－１

```javascript
var vote_changed = function(old_vote, new_vote){
    var score = get_score();

    if (new_vote !== old_vote){
        if (new_vote === 'Up'){
            score += (old_vote === 'Down' ? 2 : 1);
        } else if (new_vote === 'Down'){
            score -= (old_vote === 'Up' ? 2 : 1);
        } else if (new_vote === ''){
            score += (old_vote === 'Up' ? -1 : 1);
        }
    }
    set_score(score);
};
```
このコードでは一度に２つのタスクを行っている。

1. old_voteとnew_voteを数値にパースする
2. scoreを更新する

この２つのタスクは別々に解決する。

```javascript
var vote_value = function(vote){
    if (vote === 'Up'){
        retun +1;
    }
    if (vote === 'Down'){
        return -1;
    }
    return 0;
};

var vote_changed = function (old_vote, new_vote){
    var score = get_score();
    score -= vote_value(old_vote); // 古い値を削除する
    score += vote_value(new_vote); // 新しい値を追加する
    set_score(score);
}
```
これで楽に理解できるようになった。

わかりやすいコードを書くこつ

1. タスクを細かく分解する。
2. それぞれのタスクについて考える。


