---
title: ハッカソンに向けての調査結果を書き込む
tags:
  - ハッカソン
  - 生成AI
private: true
updated_at: '2026-07-01T05:53:04+09:00'
id: 475b32c3db8818471026
organization_url_name: null
slide: false
ignorePublish: false
---

- [ハッカソンの調査結果](#ハッカソンの調査結果)
- [Teams](#teams)
  - [チーム１のチャット想定例](#チーム１のチャット想定例)
  - [Teamsチーム２チーム、スレッドを活用](#teamsチーム２チームスレッドを活用)
  - [Teamsチーム３チームスレッドを活用](#teamsチーム３チームスレッドを活用)
- [outlook](#outlook)
  - [チーム1　予定表例](#チーム1予定表例)
  - [outlookチーム２例](#outlookチーム２例)
  - [outlookチーム３](#outlookチーム３)
  - [議事録例チーム２](#議事録例チーム２)
  - [議事録例チーム3](#議事録例チーム3)
  - [議事録例チーム4](#議事録例チーム4)
  - [議事録チーム４別日](#議事録チーム４別日)
  - [議事録チーム４別日２](#議事録チーム４別日２)
  - [議事録全体会議チーム横断新プロジェクト](#議事録全体会議チーム横断新プロジェクト)
  - [議事録チーム２に新規参画者がきた](#議事録チーム２に新規参画者がきた)
- [基にしたjson](#基にしたjson)


# ハッカソンの調査結果

とにかく情報の取得にはMicrosoft Graph API を使う。
これがあればoutook,teamsの情報が取得可能。

どんなデータがかえてっくるの？

# Teams

## チーム１のチャット想定例
```text
中村優
@佐藤健 さん
在庫APIの共通エラーフォーマットについて少し確認させてください。
現在、{"error": {"code": "E001", "message": "xxx"}} のような構造を想定してますが、detail や trace_id も含めた方が良いですか？
社外APIとの連携時のログ追跡を考えると入れておいた方がいいかなと思っています。

佐藤健（開発リーダー）
@中村優
ナイスです。
そうですね、今後の運用を考えると trace_id は入れておくべきですね。
detail は開発向け情報なので、debug モード時のみ出す形にしましょう。
私の方で共通フォーマット案を今日中に上げます。

石川怜奈
@佐藤健 さん
ありがとうございます！
ちなみに、UI側でエラー表示を統一したいので、code と message は必須で固定化される認識でいいでしょうか？
もし trace_id が追加される場合、UIでは非表示にする予定です。

佐藤健
@石川怜奈
はい、それでOKです。
code と message はAPIレスポンス仕様として固定します。
trace_id は内部用なのでUIでは扱わなくて大丈夫。

高橋純（テクニカルリード）
@佐藤健
エラーフォーマットの話に関連して、認証系のエラーコードは共通で定義しておきたいです。
たとえば E401_UNAUTHORIZED、E403_FORBIDDEN のような形で。
API Gatewayの設計に入る前に一覧化しておきます。

河合亮（DevOpsエンジニア）
@高橋純 了解しました。
Gateway側でも同じコードを返すよう統一しておきます。
あと、Lambdaとの連携検証を進めてるんですが、AWS_IAM 認証を使うか Cognito を使うかで迷ってます。
高橋さんの想定はどちらですか？

高橋純
@河合亮
今回はサービス間通信がメインなので、Cognito より IAMロール ベースの方が良いと思います。
ユーザー認証が必要になるのは次フェーズ（フロント公開時）なので、今は簡素に行きましょう。

伊藤萌（テスター）
@中村優 さん
販売APIとの結合テスト、進める際にテストデータの生成ルールってどこで管理してますか？
先週のモック修正で整合性が崩れてた部分が少し気になっていて…。

中村優
@伊藤萌
/tests/resources/mockdata.json に最新版があります。
ただ、customer_id と inventory_id の整合性は一部未調整なので、私の方で今夜修正入れます。
結合テストは月曜午前から着手予定です。

伊藤萌
了解です！ありがとうございます。
網羅率の集計は pytest --cov で出してるカバレッジをベースにまとめますね。
次回会議までに80%以上目標で整理しておきます。

石川怜奈
@高橋純 さん
バージョニングポリシーの件ですが、UI側では /api/v1/ のようにURLでバージョンを分ける運用を想定しています。
パラメータやヘッダでの指定も検討されていますか？

高橋純
@石川怜奈
基本はURLバージョンでOKです。
ヘッダ指定は後方互換性の維持が難しいので、第一フェーズでは採用しません。
ただし内部APIだけ例外的に X-API-Version を使うかもしれません。詳細は佐藤さんと調整中です。

河合亮
Slack通知連携の件、GitHub Actions の workflow_run イベントを使えば、テスト成功／失敗の結果を自動でSlackに送れるようになりそうです。
試しに #api-ci通知 チャンネルにデモ投げてもいいですか？

佐藤健
@河合亮
いいですね、ぜひお願いします。
本番導入前に一度チーム全員で確認しましょう。
通知フォーマット（成功・失敗アイコンなど）も統一しておきたいです。

石川怜奈
@中村優 さん
販売APIの /sales/summary のレスポンス構造って、前回から total_amount → total_price に変更されてますよね？
UIの一部で旧キー参照してたので修正中です。
確定のキー名を教えてもらえますか？

中村優
@石川怜奈
すみません、それ修正し忘れてました💦
正式に total_price に統一でOKです。
ドキュメントも更新しておきます！

伊藤萌
みなさん、統合テストの失敗2件はデータ整合性の問題でした。
すでに修正済みで、再実行結果は全件成功しました🎉
次回会議でレポート共有します。

佐藤健
ありがとうございます！
これで統合テストは一段落ですね。
来週の会議（10/30）は、

バージョニング方針最終確認（@高橋 さんと私）

デプロイ手順書レビュー（@河合 さん中心）
をメインに進めましょう。

高橋純
了解です。
ゲートウェイ設計書は10/29にドラフト共有します。
皆さん確認よろしく！

河合亮
Slack通知の自動化も10/28に完成予定です。
CI/CD整備、いい流れになってきましたね。

佐藤健（締め）
みんなありがとうございます！
予定通り進捗していて助かります。
それぞれのタスク完了報告はTeamsタスクボードにも反映しておいてください🙌
```
```json
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('team-001')/channels('channel-api-dev')/messages",
  "value": [
    {
      "id": "msg-001",
      "replyToId": null,
      "etag": "msg-001",
      "messageType": "message",
      "createdDateTime": "2025-10-24T01:02:45.910Z",
      "lastModifiedDateTime": "2025-10-24T01:02:45.910Z",
      "importance": "normal",
      "locale": "ja-JP",
      "from": {
        "user": {
          "id": "user-sato",
          "displayName": "佐藤健",
          "userIdentityType": "aadUser"
        }
      },
      "body": {
        "contentType": "html",
        "content": "在庫APIの共通エラーフォーマットについて、<br>必須は <code>code</code> と <code>message</code>、<br>内部用に <code>trace_id</code> を追加します。<br>本日中に仕様案を共有します。"
      },
      "mentions": [],
      "reactions": [
        {
          "reactionType": "like",
          "createdDateTime": "2025-10-24T01:03:12.000Z",
          "user": { "user": { "id": "user-ishikawa", "displayName": "石川怜奈" } }
        }
      ],
      "webUrl": "https://teams.microsoft.com/l/message/team-001/channel-api-dev/msg-001",
      "replies": [
        {
          "id": "msg-001-r1",
          "replyToId": "msg-001",
          "createdDateTime": "2025-10-24T01:06:33.100Z",
          "from": {
            "user": {
              "id": "user-ishikawa",
              "displayName": "石川怜奈",
              "userIdentityType": "aadUser"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<at id=\"0\">佐藤健</at> さん、UI側では <code>code</code> と <code>message</code> を固定化します。<br><code>trace_id</code> は非表示で対応します。"
          },
          "mentions": [
            {
              "id": 0,
              "mentionText": "佐藤健",
              "mentioned": { "user": { "id": "user-sato", "displayName": "佐藤健" } }
            }
          ],
          "reactions": [],
          "webUrl": "https://teams.microsoft.com/l/message/team-001/channel-api-dev/msg-001-r1"
        },
        {
          "id": "msg-001-r2",
          "replyToId": "msg-001",
          "createdDateTime": "2025-10-24T01:10:00.250Z",
          "from": {
            "user": {
              "id": "user-takahashi",
              "displayName": "高橋純",
              "userIdentityType": "aadUser"
            }
          },
          "body": {
            "contentType": "html",
            "content": "認証系の共通エラーコードとして <code>E401_UNAUTHORIZED</code> と <code>E403_FORBIDDEN</code> を定義します。<br>API Gateway設計書に追記します。"
          },
          "mentions": [],
          "reactions": [
            {
              "reactionType": "like",
              "createdDateTime": "2025-10-24T01:11:00.000Z",
              "user": { "user": { "id": "user-sato", "displayName": "佐藤健" } }
            }
          ]
        }
      ]
    },
    {
      "id": "msg-002",
      "replyToId": null,
      "createdDateTime": "2025-10-24T01:15:40.000Z",
      "from": {
        "user": {
          "id": "user-kawai",
          "displayName": "河合亮",
          "userIdentityType": "aadUser"
        }
      },
      "body": {
        "contentType": "html",
        "content": "<at id=\"0\">高橋純</at> さん、API Gateway の認証連携について確認です。<br>IAM ロールベースで進める認識でよいでしょうか？"
      },
      "mentions": [
        {
          "id": 0,
          "mentionText": "高橋純",
          "mentioned": { "user": { "id": "user-takahashi", "displayName": "高橋純" } }
        }
      ],
      "reactions": [],
      "replies": [
        {
          "id": "msg-002-r1",
          "replyToId": "msg-002",
          "createdDateTime": "2025-10-24T01:17:20.000Z",
          "from": {
            "user": {
              "id": "user-takahashi",
              "displayName": "高橋純",
              "userIdentityType": "aadUser"
            }
          },
          "body": {
            "contentType": "html",
            "content": "はい、今回はサービス間通信が中心なので IAM ロールで進めましょう。<br>Cognito は次フェーズから検討します。"
          },
          "mentions": [],
          "reactions": []
        }
      ]
    },
    {
      "id": "msg-003",
      "replyToId": null,
      "createdDateTime": "2025-10-24T01:20:45.000Z",
      "from": {
        "user": {
          "id": "user-ito",
          "displayName": "伊藤萌",
          "userIdentityType": "aadUser"
        }
      },
      "body": {
        "contentType": "html",
        "content": "<at id=\"0\">中村優</at> さん、結合テストのテストデータ生成ルールはどこで管理してますか？<br>一部モック不整合があった箇所を確認したいです。"
      },
      "mentions": [
        {
          "id": 0,
          "mentionText": "中村優",
          "mentioned": { "user": { "id": "user-nakamura", "displayName": "中村優" } }
        }
      ],
      "replies": [
        {
          "id": "msg-003-r1",
          "replyToId": "msg-003",
          "createdDateTime": "2025-10-24T01:22:10.000Z",
          "from": {
            "user": {
              "id": "user-nakamura",
              "displayName": "中村優",
              "userIdentityType": "aadUser"
            }
          },
          "body": {
            "contentType": "html",
            "content": "`/tests/resources/mockdata.json` に最新版があります。<br>整合性は今夜修正して、月曜から結合テスト着手予定です。"
          },
          "mentions": [],
          "reactions": []
        },
        {
          "id": "msg-003-r2",
          "replyToId": "msg-003",
          "createdDateTime": "2025-10-24T01:25:15.000Z",
          "from": {
            "user": {
              "id": "user-ito",
              "displayName": "伊藤萌",
              "userIdentityType": "aadUser"
            }
          },
          "body": {
            "contentType": "html",
            "content": "ありがとうございます！<br>カバレッジ集計も合わせてまとめておきます。目標80%以上で！"
          },
          "mentions": [],
          "reactions": []
        }
      ]
    },
    {
      "id": "msg-004",
      "replyToId": null,
      "createdDateTime": "2025-10-24T01:30:00.000Z",
      "from": {
        "user": {
          "id": "user-ishikawa",
          "displayName": "石川怜奈",
          "userIdentityType": "aadUser"
        }
      },
      "body": {
        "contentType": "html",
        "content": "販売APIの <code>/sales/summary</code> のレスポンスキー、<br><code>total_price</code> で確定でよいでしょうか？<br>UI側の参照を更新中です。"
      },
      "mentions": [],
      "replies": [
        {
          "id": "msg-004-r1",
          "replyToId": "msg-004",
          "createdDateTime": "2025-10-24T01:31:45.000Z",
          "from": {
            "user": {
              "id": "user-nakamura",
              "displayName": "中村優",
              "userIdentityType": "aadUser"
            }
          },
          "body": {
            "contentType": "html",
            "content": "はい、正式に <code>total_price</code> で統一です。<br>ドキュメントも更新します！"
          },
          "mentions": [],
          "reactions": []
        }
      ]
    },
    {
      "id": "msg-005",
      "replyToId": null,
      "createdDateTime": "2025-10-24T01:35:50.000Z",
      "from": {
        "user": {
          "id": "user-ito",
          "displayName": "伊藤萌",
          "userIdentityType": "aadUser"
        }
      },
      "body": {
        "contentType": "html",
        "content": "統合テストの結果を共有します。<br>全80件中、最終的に全件成功になりました🎉<br>次回会議でレポート提出します。"
      },
      "mentions": [],
      "reactions": [
        {
          "reactionType": "like",
          "createdDateTime": "2025-10-24T01:36:30.000Z",
          "user": { "user": { "id": "user-sato", "displayName": "佐藤健" } }
        },
        {
          "reactionType": "heart",
          "createdDateTime": "2025-10-24T01:36:45.000Z",
          "user": { "user": { "id": "user-ishikawa", "displayName": "石川怜奈" } }
        }
      ]
    },
    {
      "id": "msg-006",
      "replyToId": null,
      "createdDateTime": "2025-10-24T01:40:00.000Z",
      "from": {
        "user": {
          "id": "user-sato",
          "displayName": "佐藤健",
          "userIdentityType": "aadUser"
        }
      },
      "body": {
        "contentType": "html",
        "content": "みなさん、進捗ありがとうございます！<br>来週（10/30）の会議では、<br>・バージョニング方針の最終確認（<at id=\"0\">高橋純</at> さんと私）<br>・デプロイ手順書レビュー（<at id=\"1\">河合亮</at> さん中心）<br>を進めます。"
      },
      "mentions": [
        {
          "id": 0,
          "mentionText": "高橋純",
          "mentioned": { "user": { "id": "user-takahashi", "displayName": "高橋純" } }
        },
        {
          "id": 1,
          "mentionText": "河合亮",
          "mentioned": { "user": { "id": "user-kawai", "displayName": "河合亮" } }
        }
      ],
      "reactions": []
    }
  ]
}

```

## Teamsチーム２チーム、スレッドを活用
```text
💬 チャネル：一般
🧵 スレッド①：テスト項目書レビュー進捗

山本綾子（QAリーダー）

テスト項目書の全体レビューが完了しました。
販売・在庫・会計の3モジュールは重点観点として整理済みです。
ただし、API変更点が一部未反映なので、設計・開発チームからの最新API一覧が届き次第、10/25までに更新します。

藤原光（テストエンジニア）

@山本綾子 さん
最新API一覧って、佐藤さん（開発チーム）から共有済みでしたっけ？
DevOpsのリポジトリにあるAPI仕様書（v1.4）だと古いかもしれません。

山本綾子

まだ正式な最新版は未共有です。
佐藤さんからは「10/24午前にアップ予定」とのことなので、それを受け取って更新作業に入ります。

岡田奈々（ドキュメント担当）

了解しました。更新後に私の方で整形・版管理しておきます。
更新版を共有フォルダに「Test_Spec_v1.3_reviewed.xlsx」として置きますね。

🧵 スレッド②：自動テストスクリプト修正状況

藤原光

Python + Selenium の自動テストスクリプト、UI変更の影響で一部テストが失敗してます。
ログインページのXPath指定が変わっていたので、修正対応中です。
@河合 さん、CI/CD上での並列実行設定について、明日少し打ち合わせ可能ですか？

河合（DevOpsチーム）

@藤原光 さん
明日（10/25）の午後15時〜で大丈夫です。
Azure Pipeline側のテストジョブ分割のサンプルを共有しておきます👇
[リンク] CI_CDPipeline_sample.yaml

山本綾子

藤原さん、CI連携の確認は必ず10/27までにお願いします。
テスト実行ログが安定すれば、そのまま統合テストにも流用できます。

藤原光

承知しました。10/25に河合さんと調整して、27日には動作確認まで完了します。

🧵 スレッド③：不具合報告テンプレート改訂

岡田奈々

不具合報告テンプレートの初版を共有しました。
[リンク] Bug_Report_Template_v1.xlsx

山本綾子

岡田さん、ありがとうございます。
「再現手順」「影響範囲」「環境情報」は必須項目として追加お願いします。
特に環境情報は、OS / ブラウザ / APIバージョンを分けて書けるようにしておきましょう。

岡田奈々

了解しました。
修正版を10/26までに「共有フォルダ > QA_Templates」配下にアップします。

藤原光

再現動画の添付欄を追加してもらえると助かります。
Seleniumテスト結果を動画化して貼れるようにしたいです。

岡田奈々

ナイス案です！それも入れておきます。

📢 チャネル：連絡
🧵 スレッド①：統合テストスケジュール確定案

山本綾子

統合テストは以下スケジュールで進める案で考えています👇
期間：11/4（月）〜11/15（金）
対象：販売・在庫・会計モジュール＋連携API群

バグ報告〜修正〜再テストのサイクルを短縮するため、
日次進捗報告をTeamsの「#qa_daily」チャンネルに投稿してください。

藤原光

了解しました。自動テスト結果も同チャンネルで共有します。

岡田奈々

日次報告テンプレートも用意しておきます。
「完了項目」「未実施項目」「障害発生数」「主な懸念点」などを記入する形にします。

山本綾子

助かります。
スケジュール最終版は10/28の会議で確定します。

🧵 スレッド②：次回会議（10/28）リマインド

岡田奈々

📅 次回会議のリマインドです。
日時：10/28（火）16:00〜17:00
議題：
・テスト項目書最終確認
・自動テストスクリプト動作報告
・不具合報告テンプレートレビュー

会議URL： [Teams Meeting Link]

山本綾子

ありがとう！
当日は最新版のテスト項目書を画面共有して進行します。

📚 チャネル：情報共有
🧵 スレッド①：自動テストTips共有

藤原光

Seleniumのテスト失敗時に自動でスクリーンショットを保存する方法をまとめました👇

driver.save_screenshot(f"screenshots/{test_name}.png")


CI/CDでのテスト可視化に使えます。
@岡田奈々 さん、報告テンプレートの「添付資料欄」にもこの出力を入れられるようにしておくと良いかもです。

岡田奈々

ありがとうございます！早速テンプレートに反映します。

🧵 スレッド②：API更新情報共有

山本綾子

設計・開発チームよりAPI一覧の最新版（v1.5）が届きました。
共有フォルダ： \\share\dev_team\API_docs\v1.5
更新点は以下の通り：

/inventory/update に warehouse_id パラメータ追加

/sales/export の戻り値に transaction_id フィールド追加

@藤原光 さん、この更新に伴う自動テストの修正対応お願いします。

藤原光

了解しました。テストスクリプト内のリクエスト部分を修正して、
明日のCI実行に反映させます。

🧵 スレッド③：QAプロセス改善提案

岡田奈々

今後の品質保証プロセス改善として、
「テスト結果自動集計 + ダッシュボード化」を提案します。
Power BIまたはExcelマクロで、日次報告を自動的に集約できるようにしたいです。

山本綾子

いいですね。まずはExcelマクロ版で試しましょう。
11月テスト期間中に簡易レポート化して運用してみましょう。
```
```json
{
  "exportedAt": "2025-10-24T00:55:00Z",
  "source": "Microsoft Graph v1.0 (simulated)",
  "team": {
    "id": "c2b8d0a1-4a1d-4e9d-8d2e-1b2c3d4e5f60",
    "displayName": "テスト・品質保証チーム",
    "description": "統合テスト・リリース前検証タスク用チーム",
    "webUrl": "https://teams.microsoft.com/l/team/19%3Aqa-team",
    "channels": [
      {
        "id": "19:general@thread.tacv2",
        "displayName": "一般",
        "description": "チーム内の全般連絡・進捗共有",
        "membershipType": "standard",
        "webUrl": "https://teams.microsoft.com/l/channel/19%3Ageneral%40thread.tacv2",
        "messages": [
          {
            "id": "169f8a98-6b1d-4f63-8e0f-1a9f7a10c001",
            "messageType": "message",
            "subject": "テスト項目書レビュー進捗",
            "createdDateTime": "2025-10-24T00:10:00Z",
            "lastModifiedDateTime": "2025-10-24T00:10:00Z",
            "from": {
              "user": {
                "id": "6a2b0d51-0d4a-4c7c-8f2a-8c6f4c8f1111",
                "displayName": "山本綾子",
                "userIdentityType": "aadUser",
                "userPrincipalName": "ayako.yamamoto@contoso.com"
              }
            },
            "body": {
              "contentType": "html",
              "content": "<p>テスト項目書の全体レビューが完了しました。<br/>販売・在庫・会計の3モジュールは重点観点として整理済みです。<br/>API変更点が一部未反映のため、設計・開発チームからの最新API一覧が届き次第、<b>10/25</b>までに更新します。</p>"
            },
            "mentions": [],
            "attachments": [],
            "reactions": [
              {
                "reactionType": "like",
                "createdDateTime": "2025-10-24T00:11:10Z",
                "user": {
                  "user": {
                    "id": "8c9d2f77-2a2c-4a5b-9b41-3f1f2e2a2222",
                    "displayName": "岡田奈々"
                  }
                }
              }
            ],
            "replies": [
              {
                "id": "r-001-a1",
                "replyToId": "169f8a98-6b1d-4f63-8e0f-1a9f7a10c001",
                "createdDateTime": "2025-10-24T00:12:30Z",
                "from": {
                  "user": {
                    "id": "5e1d13a2-9b34-4b7a-9a6b-6b2cf8d33333",
                    "displayName": "藤原光",
                    "userPrincipalName": "hikaru.fujiwara@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p><at id=\"0\">山本綾子</at> さん、最新API一覧は開発の佐藤さんから共有済みでしたか？ v1.4 だと古いかもです。</p>"
                },
                "mentions": [
                  {
                    "id": 0,
                    "mentionText": "山本綾子",
                    "mentioned": {
                      "user": {
                        "id": "6a2b0d51-0d4a-4c7c-8f2a-8c6f4c8f1111",
                        "displayName": "山本綾子"
                      }
                    }
                  }
                ]
              },
              {
                "id": "r-001-a2",
                "replyToId": "169f8a98-6b1d-4f63-8e0f-1a9f7a10c001",
                "createdDateTime": "2025-10-24T00:13:40Z",
                "from": {
                  "user": {
                    "id": "6a2b0d51-0d4a-4c7c-8f2a-8c6f4c8f1111",
                    "displayName": "山本綾子",
                    "userPrincipalName": "ayako.yamamoto@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p>正式最新版は未共有です。<br/>佐藤さんから<b>10/24 午前</b>にアップ予定と連絡あり。受領後に項目書を更新します。</p>"
                },
                "mentions": []
              },
              {
                "id": "r-001-a3",
                "replyToId": "169f8a98-6b1d-4f63-8e0f-1a9f7a10c001",
                "createdDateTime": "2025-10-24T00:14:20Z",
                "from": {
                  "user": {
                    "id": "8c9d2f77-2a2c-4a5b-9b41-3f1f2e2a2222",
                    "displayName": "岡田奈々",
                    "userPrincipalName": "nana.okada@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p>了解です。更新後、私の方で版管理して共有します。ファイル名は <code>Test_Spec_v1.3_reviewed.xlsx</code> で配置します。</p>"
                },
                "mentions": []
              }
            ]
          },
          {
            "id": "d7b0a725-1c42-4a2f-9a41-9e4e4ea0c002",
            "messageType": "message",
            "subject": "自動テストスクリプト修正状況",
            "createdDateTime": "2025-10-24T00:15:00Z",
            "lastModifiedDateTime": "2025-10-24T00:15:00Z",
            "from": {
              "user": {
                "id": "5e1d13a2-9b34-4b7a-9a6b-6b2cf8d33333",
                "displayName": "藤原光",
                "userIdentityType": "aadUser",
                "userPrincipalName": "hikaru.fujiwara@contoso.com"
              }
            },
            "body": {
              "contentType": "html",
              "content": "<p>Python + Selenium の自動テスト、UI変更の影響で一部失敗しています。<br/>ログインページのXPath変更に対応中です。<br/><at id=\"0\">河合</at> さん、CI/CD上の並列実行設定について、<b>10/25 15:00</b>で打ち合わせ可能でしょうか？</p>"
            },
            "mentions": [
              {
                "id": 0,
                "mentionText": "河合",
                "mentioned": {
                  "user": {
                    "id": "2f4a8d10-1e8b-4a33-8a27-4d4fbc444444",
                    "displayName": "河合",
                    "userPrincipalName": "kawai.devops@contoso.com"
                  }
                }
              }
            ],
            "attachments": [],
            "reactions": [],
            "replies": [
              {
                "id": "r-002-b1",
                "replyToId": "d7b0a725-1c42-4a2f-9a41-9e4e4ea0c002",
                "createdDateTime": "2025-10-24T00:22:10Z",
                "from": {
                  "user": {
                    "id": "2f4a8d10-1e8b-4a33-8a27-4d4fbc444444",
                    "displayName": "河合",
                    "userPrincipalName": "kawai.devops@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p><at id=\"0\">藤原光</at> さん、<b>10/25 15:00</b> でOKです。<br/>Azure Pipeline のジョブ分割サンプル置きました→ <a href=\"https://dev.azure.com/contoso/qa/_git/pipelines?path=%2FCI_CDPipeline_sample.yaml\">CI_CDPipeline_sample.yaml</a></p>"
                },
                "mentions": [
                  {
                    "id": 0,
                    "mentionText": "藤原光",
                    "mentioned": {
                      "user": {
                        "id": "5e1d13a2-9b34-4b7a-9a6b-6b2cf8d33333",
                        "displayName": "藤原光"
                      }
                    }
                  }
                ]
              },
              {
                "id": "r-002-b2",
                "replyToId": "d7b0a725-1c42-4a2f-9a41-9e4e4ea0c002",
                "createdDateTime": "2025-10-24T00:23:05Z",
                "from": {
                  "user": {
                    "id": "6a2b0d51-0d4a-4c7c-8f2a-8c6f4c8f1111",
                    "displayName": "山本綾子",
                    "userPrincipalName": "ayako.yamamoto@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p>藤原さん、CI連携の確認は<b>10/27</b>までにお願いします。統合テストでも流用します。</p>"
                },
                "mentions": []
              },
              {
                "id": "r-002-b3",
                "replyToId": "d7b0a725-1c42-4a2f-9a41-9e4e4ea0c002",
                "createdDateTime": "2025-10-24T00:24:10Z",
                "from": {
                  "user": {
                    "id": "5e1d13a2-9b34-4b7a-9a6b-6b2cf8d33333",
                    "displayName": "藤原光",
                    "userPrincipalName": "hikaru.fujiwara@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p>承知しました。<br/>10/25に<at id=\"0\">河合</at>さんと調整し、<b>10/27</b>までに動作確認完了します。</p>"
                },
                "mentions": [
                  {
                    "id": 0,
                    "mentionText": "河合",
                    "mentioned": {
                      "user": {
                        "id": "2f4a8d10-1e8b-4a33-8a27-4d4fbc444444",
                        "displayName": "河合"
                      }
                    }
                  }
                ]
              }
            ]
          },
          {
            "id": "c424c2a9-1b4b-4c1d-b770-42e8a0b0c003",
            "messageType": "message",
            "subject": "不具合報告テンプレート改訂",
            "createdDateTime": "2025-10-24T00:20:00Z",
            "lastModifiedDateTime": "2025-10-24T00:20:00Z",
            "from": {
              "user": {
                "id": "8c9d2f77-2a2c-4a5b-9b41-3f1f2e2a2222",
                "displayName": "岡田奈々",
                "userIdentityType": "aadUser",
                "userPrincipalName": "nana.okada@contoso.com"
              }
            },
            "body": {
              "contentType": "html",
              "content": "<p>不具合報告テンプレートの初版を共有します。<br/><a href=\"https://contoso.sharepoint.com/sites/qa/Shared%20Documents/Bug_Report_Template_v1.xlsx\">Bug_Report_Template_v1.xlsx</a></p>"
            },
            "mentions": [],
            "attachments": [
              {
                "id": "att-001",
                "contentType": "reference",
                "name": "Bug_Report_Template_v1.xlsx",
                "contentUrl": "https://contoso.sharepoint.com/sites/qa/Shared%20Documents/Bug_Report_Template_v1.xlsx"
              }
            ],
            "reactions": [],
            "replies": [
              {
                "id": "r-003-c1",
                "replyToId": "c424c2a9-1b4b-4c1d-b770-42e8a0b0c003",
                "createdDateTime": "2025-10-24T00:21:30Z",
                "from": {
                  "user": {
                    "id": "6a2b0d51-0d4a-4c7c-8f2a-8c6f4c8f1111",
                    "displayName": "山本綾子",
                    "userPrincipalName": "ayako.yamamoto@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p>ありがとう。必須項目として<b>再現手順・影響範囲・環境情報</b>を追加してください。OS / ブラウザ / APIバージョンを分けて記載できるように。</p>"
                },
                "mentions": []
              },
              {
                "id": "r-003-c2",
                "replyToId": "c424c2a9-1b4b-4c1d-b770-42e8a0b0c003",
                "createdDateTime": "2025-10-24T00:22:20Z",
                "from": {
                  "user": {
                    "id": "8c9d2f77-2a2c-4a5b-9b41-3f1f2e2a2222",
                    "displayName": "岡田奈々",
                    "userPrincipalName": "nana.okada@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p>了解です。<b>10/26</b>までに「共有フォルダ &gt; QA_Templates」に修正版をアップします。</p>"
                },
                "mentions": []
              },
              {
                "id": "r-003-c3",
                "replyToId": "c424c2a9-1b4b-4c1d-b770-42e8a0b0c003",
                "createdDateTime": "2025-10-24T00:23:30Z",
                "from": {
                  "user": {
                    "id": "5e1d13a2-9b34-4b7a-9a6b-6b2cf8d33333",
                    "displayName": "藤原光",
                    "userPrincipalName": "hikaru.fujiwara@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p>再現動画の添付欄もあると助かります。Selenium結果の動画を貼りたいです。</p>"
                },
                "mentions": []
              },
              {
                "id": "r-003-c4",
                "replyToId": "c424c2a9-1b4b-4c1d-b770-42e8a0b0c003",
                "createdDateTime": "2025-10-24T00:24:20Z",
                "from": {
                  "user": {
                    "id": "8c9d2f77-2a2c-4a5b-9b41-3f1f2e2a2222",
                    "displayName": "岡田奈々",
                    "userPrincipalName": "nana.okada@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p>ナイス案です！その欄も追加します。</p>"
                },
                "mentions": []
              }
            ]
          }
        ]
      },
      {
        "id": "19:notice@thread.tacv2",
        "displayName": "連絡",
        "description": "スケジュール・会議・決定事項",
        "membershipType": "standard",
        "webUrl": "https://teams.microsoft.com/l/channel/19%3Anotice%40thread.tacv2",
        "messages": [
          {
            "id": "m-notice-001",
            "messageType": "message",
            "subject": "統合テストスケジュール確定案",
            "createdDateTime": "2025-10-24T00:30:00Z",
            "lastModifiedDateTime": "2025-10-24T00:30:00Z",
            "from": {
              "user": {
                "id": "6a2b0d51-0d4a-4c7c-8f2a-8c6f4c8f1111",
                "displayName": "山本綾子",
                "userPrincipalName": "ayako.yamamoto@contoso.com"
              }
            },
            "body": {
              "contentType": "html",
              "content": "<p>統合テストは以下案で進めます：<br/><b>期間：11/4（月）〜11/15（金）</b><br/>対象：販売・在庫・会計＋連携API群<br/><br/>バグ報告〜修正〜再テストのサイクル短縮のため、<b>#qa_daily</b> への日次進捗報告をお願いします。</p>"
            },
            "mentions": [],
            "attachments": [],
            "reactions": [
              {
                "reactionType": "like",
                "createdDateTime": "2025-10-24T00:31:10Z",
                "user": {
                  "user": {
                    "id": "5e1d13a2-9b34-4b7a-9a6b-6b2cf8d33333",
                    "displayName": "藤原光"
                  }
                }
              },
              {
                "reactionType": "like",
                "createdDateTime": "2025-10-24T00:31:30Z",
                "user": {
                  "user": {
                    "id": "8c9d2f77-2a2c-4a5b-9b41-3f1f2e2a2222",
                    "displayName": "岡田奈々"
                  }
                }
              }
            ],
            "replies": [
              {
                "id": "r-notice-001-a1",
                "replyToId": "m-notice-001",
                "createdDateTime": "2025-10-24T00:32:10Z",
                "from": {
                  "user": {
                    "id": "5e1d13a2-9b34-4b7a-9a6b-6b2cf8d33333",
                    "displayName": "藤原光",
                    "userPrincipalName": "hikaru.fujiwara@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p>了解です。自動テスト結果も #qa_daily に共有します。</p>"
                }
              },
              {
                "id": "r-notice-001-a2",
                "replyToId": "m-notice-001",
                "createdDateTime": "2025-10-24T00:33:20Z",
                "from": {
                  "user": {
                    "id": "8c9d2f77-2a2c-4a5b-9b41-3f1f2e2a2222",
                    "displayName": "岡田奈々",
                    "userPrincipalName": "nana.okada@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p>日次報告テンプレートを用意します。<br/>「完了項目」「未実施項目」「障害発生数」「主な懸念点」でまとめます。</p>"
                }
              },
              {
                "id": "r-notice-001-a3",
                "replyToId": "m-notice-001",
                "createdDateTime": "2025-10-24T00:34:15Z",
                "from": {
                  "user": {
                    "id": "6a2b0d51-0d4a-4c7c-8f2a-8c6f4c8f1111",
                    "displayName": "山本綾子",
                    "userPrincipalName": "ayako.yamamoto@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p>助かります。スケジュール最終版は<b>10/28</b>会議で確定します。</p>"
                }
              }
            ]
          },
          {
            "id": "m-notice-002",
            "messageType": "message",
            "subject": "次回会議（10/28）リマインド",
            "createdDateTime": "2025-10-24T00:35:00Z",
            "lastModifiedDateTime": "2025-10-24T00:35:00Z",
            "from": {
              "user": {
                "id": "8c9d2f77-2a2c-4a5b-9b41-3f1f2e2a2222",
                "displayName": "岡田奈々",
                "userPrincipalName": "nana.okada@contoso.com"
              }
            },
            "body": {
              "contentType": "html",
              "content": "<p>📅 次回会議のリマインドです。<br/><b>日時：10/28（火）16:00〜17:00</b><br/>議題：<br/>・テスト項目書最終確認<br/>・自動テストスクリプト動作報告<br/>・不具合報告テンプレートレビュー<br/><br/><a href=\"https://teams.microsoft.com/l/meetup-join/19%3Ameeting\">Teams Meeting Link</a></p>"
            },
            "mentions": [],
            "attachments": [],
            "replies": [
              {
                "id": "r-notice-002-b1",
                "replyToId": "m-notice-002",
                "createdDateTime": "2025-10-24T00:36:00Z",
                "from": {
                  "user": {
                    "id": "6a2b0d51-0d4a-4c7c-8f2a-8c6f4c8f1111",
                    "displayName": "山本綾子",
                    "userPrincipalName": "ayako.yamamoto@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p>ありがとう！ 当日は最新版のテスト項目書を画面共有します。</p>"
                }
              }
            ]
          }
        ]
      },
      {
        "id": "19:info-share@thread.tacv2",
        "displayName": "情報共有",
        "description": "Tips・API更新・改善提案",
        "membershipType": "standard",
        "webUrl": "https://teams.microsoft.com/l/channel/19%3Ainfo-share%40thread.tacv2",
        "messages": [
          {
            "id": "m-info-001",
            "messageType": "message",
            "subject": "自動テストTips共有",
            "createdDateTime": "2025-10-24T00:40:00Z",
            "lastModifiedDateTime": "2025-10-24T00:40:00Z",
            "from": {
              "user": {
                "id": "5e1d13a2-9b34-4b7a-9a6b-6b2cf8d33333",
                "displayName": "藤原光",
                "userPrincipalName": "hikaru.fujiwara@contoso.com"
              }
            },
            "body": {
              "contentType": "html",
              "content": "<p>Selenium失敗時にスクリーンショット保存👇</p><pre><code>driver.save_screenshot(f\"screenshots/{'{'}test_name{'}'}.png\")\n</code></pre><p>CI/CDでの可視化に活用できます。<br/><at id=\"0\">岡田奈々</at> さん、報告テンプレートの「添付資料欄」にこの出力も入れられると良いかもです。</p>"
            },
            "mentions": [
              {
                "id": 0,
                "mentionText": "岡田奈々",
                "mentioned": {
                  "user": {
                    "id": "8c9d2f77-2a2c-4a5b-9b41-3f1f2e2a2222",
                    "displayName": "岡田奈々",
                    "userPrincipalName": "nana.okada@contoso.com"
                  }
                }
              }
            ],
            "attachments": [],
            "replies": [
              {
                "id": "r-info-001-a1",
                "replyToId": "m-info-001",
                "createdDateTime": "2025-10-24T00:41:30Z",
                "from": {
                  "user": {
                    "id": "8c9d2f77-2a2c-4a5b-9b41-3f1f2e2a2222",
                    "displayName": "岡田奈々",
                    "userPrincipalName": "nana.okada@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p>ありがとうございます！ テンプレートに反映します。</p>"
                }
              }
            ]
          },
          {
            "id": "m-info-002",
            "messageType": "message",
            "subject": "API更新情報共有",
            "createdDateTime": "2025-10-24T00:45:00Z",
            "lastModifiedDateTime": "2025-10-24T00:45:00Z",
            "from": {
              "user": {
                "id": "6a2b0d51-0d4a-4c7c-8f2a-8c6f4c8f1111",
                "displayName": "山本綾子",
                "userPrincipalName": "ayako.yamamoto@contoso.com"
              }
            },
            "body": {
              "contentType": "html",
              "content": "<p>開発よりAPI一覧最新版（v1.5）が届きました。<br/>共有フォルダ： \\\\share\\dev_team\\API_docs\\v1.5<br/>更新点：<br/>・<code>/inventory/update</code> に <code>warehouse_id</code> 追加<br/>・<code>/sales/export</code> のレスポンスに <code>transaction_id</code> 追加</p><p><at id=\"0\">藤原光</at> さん、自動テストの修正対応お願いします。</p>"
            },
            "mentions": [
              {
                "id": 0,
                "mentionText": "藤原光",
                "mentioned": {
                  "user": {
                    "id": "5e1d13a2-9b34-4b7a-9a6b-6b2cf8d33333",
                    "displayName": "藤原光",
                    "userPrincipalName": "hikaru.fujiwara@contoso.com"
                  }
                }
              }
            ],
            "attachments": [],
            "replies": [
              {
                "id": "r-info-002-b1",
                "replyToId": "m-info-002",
                "createdDateTime": "2025-10-24T00:46:20Z",
                "from": {
                  "user": {
                    "id": "5e1d13a2-9b34-4b7a-9a6b-6b2cf8d33333",
                    "displayName": "藤原光",
                    "userPrincipalName": "hikaru.fujiwara@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p>了解しました。リクエスト・レスポンス定義を修正し、明日のCIに反映させます。</p>"
                }
              }
            ]
          },
          {
            "id": "m-info-003",
            "messageType": "message",
            "subject": "QAプロセス改善提案",
            "createdDateTime": "2025-10-24T00:50:00Z",
            "lastModifiedDateTime": "2025-10-24T00:50:00Z",
            "from": {
              "user": {
                "id": "8c9d2f77-2a2c-4a5b-9b41-3f1f2e2a2222",
                "displayName": "岡田奈々",
                "userPrincipalName": "nana.okada@contoso.com"
              }
            },
            "body": {
              "contentType": "html",
              "content": "<p>品質保証プロセス改善案：<br/>日次報告の<b>自動集計＋ダッシュボード化</b>（Power BIまたはExcelマクロ）を提案します。</p>"
            },
            "mentions": [],
            "attachments": [],
            "reactions": [
              {
                "reactionType": "like",
                "createdDateTime": "2025-10-24T00:50:45Z",
                "user": {
                  "user": {
                    "id": "6a2b0d51-0d4a-4c7c-8f2a-8c6f4c8f1111",
                    "displayName": "山本綾子"
                  }
                }
              }
            ],
            "replies": [
              {
                "id": "r-info-003-c1",
                "replyToId": "m-info-003",
                "createdDateTime": "2025-10-24T00:51:10Z",
                "from": {
                  "user": {
                    "id": "6a2b0d51-0d4a-4c7c-8f2a-8c6f4c8f1111",
                    "displayName": "山本綾子",
                    "userPrincipalName": "ayako.yamamoto@contoso.com"
                  }
                },
                "body": {
                  "contentType": "html",
                  "content": "<p>まずはExcelマクロ版で試しましょう。11月のテスト期間中に簡易レポート化して運用しましょう。</p>"
                }
              }
            ]
          }
        ]
      }
    ]
  }
}

```

## Teamsチーム３チームスレッドを活用
```text
💬 チャネル：一般
🧵 スレッド①：在庫APIレビュー結果共有

佐藤健（開発リーダー）
在庫APIのレビューとマージ完了しました。
共通エラーハンドリング仕様を統一する方向で進めます。
外部システム連携のトークン認証方式については @高橋純 さんの提案案（JWT署名＋有効期限制御）を採用します。

中村優（バックエンドエンジニア）
@佐藤健 さん
エラーフォーマットは "error": {"code": "E001", "message": "xxx", "trace_id": "..."} のような形式で定義する想定ですか？

佐藤健
はい、その方向です。詳細は「API共通エラーフォーマット仕様（draft）」として10/27までに整理します。

高橋純（テクニカルリード）
了解です。次回までに外部連携のトークン仕様書も併せてレビューします。

🧵 スレッド②：会計APIテスト進捗

中村優
会計APIのテストコード追加が完了しました。
モックデータ不整合が原因で一部テストが失敗していましたが修正済みです。
販売APIとの結合テストを今週中（〜10/26）に実施予定です。

伊藤萌（テスター）
@中村優 さん
結合テストのログ出力フォーマットを統一しましょうか？
テストカバレッジの再確認も一緒に進めます。

中村優
お願いします。pytest --cov-report=xml の出力をまとめて次回共有します。

佐藤健
了解。次回（10/30）の定例で報告お願いします。

🧵 スレッド③：フロントエンドとの連携確認

石川怜奈（フロントエンドエンジニア）
React UIのプロトタイプで、販売管理画面のAPI連携確認完了しました。
ただし、/sales/list のレスポンス構造が変更（items → data）されていたため、モックを修正中です。

高橋純
@石川怜奈 さん
バージョン管理ルールが曖昧なので、次回までにAPIバージョニングポリシーをまとめます（@佐藤健 さんと一緒に）。

佐藤健
了解。v1.5 から v2.0 に上がる際の互換性基準も定義しておきましょう。

石川怜奈
承知です。UI側のAPIモック更新は10/26までに完了させます。

🧵 スレッド④：APIゲートウェイ設計方針

高橋純
APIゲートウェイ設計の初回レビュー結果を共有します。
認証・認可を統合的に扱うため、AWS API Gateway + Lambda + Cognito連携案で進める予定です。
スケーラビリティ面を考慮して、将来的にエッジキャッシュ構成も検討中です。

河合亮（DevOpsエンジニア）
了解です。CI/CD経由でデプロイする際、ステージごとの環境変数はSSM経由で読み込む構成にします。

佐藤健
OK。高橋さん・河合さんで10/29までに詳細設計まとめをお願いします。
レビューは次回会議で行いましょう。

🧵 スレッド⑤：統合テストとCI/CD整備

伊藤萌
販売APIの統合テストを実施しました。80件中78件成功です。
失敗した2件はモックデータと期待値不一致によるものです。修正中。

河合亮
CI/CDパイプラインの自動デプロイ設定を本番相当環境に適用済みです。
次はSlack通知の自動化を組み込み予定。
@伊藤萌 さん、テスト完了時のSlack通知にWebhook使っていいですか？

伊藤萌
OKです。通知内容は成功率とエラー件数を入れてください。

河合亮
了解。10/28までにSlack連携完了させます。

高橋純
素晴らしい進捗です。CI実行トリガーの自動化も次フェーズで検討しましょう。

📢 チャネル：連絡
🧵 スレッド①：アクションアイテム整理

佐藤健
今週のアクションアイテムを共有します👇

No	内容	担当	期限
1	API共通エラーフォーマット定義	佐藤	10/27
2	結合テスト結果報告・網羅率確認	中村・伊藤	10/28
3	バージョニングポリシー策定	高橋・佐藤	10/29
4	APIゲートウェイ詳細設計	高橋・河合	10/29
5	UI側APIモック更新	石川	10/26
6	Slack通知連携構築	河合	10/28

高橋純
ありがとうございます。進捗は #dev_progress チャンネルで日次更新します。

🧵 スレッド②：次回会議案内

伊藤萌
📅 次回会議の予定です。
日時：10/30（木） 14:00〜15:30
議題：

統合テスト結果レビュー

APIバージョニング方針の最終確認

デプロイ手順書レビュー
URL：[Teams Meeting Link]

佐藤健
了解です。当日はゲートウェイ詳細設計とバージョン方針を共有します。

📚 チャネル：技術共有
🧵 スレッド①：API共通エラーフォーマット案共有

佐藤健
共通エラーフォーマットのドラフトを作成しました。

{
  "error": {
    "code": "E001",
    "message": "Invalid parameter",
    "trace_id": "abcd1234efgh5678"
  }
}


全APIでこの形式を返す想定です。
意見があればコメントください。

中村優
了解です。detail フィールド追加を提案します。開発ログ連携で活用できそうです。

高橋純
良いですね。正式定義時にオプション項目として追加しましょう。

🧵 スレッド②：Slack通知連携Tips

河合亮
CI/CDのSlack通知はGitHub ActionsとWebhookでつなげます。
通知例👇

✅ 統合テスト完了  
成功率: 97.5%（78/80）  
担当: 伊藤・中村


Webhook URLは devops-config/slack.env に格納します。

伊藤萌
ありがとうございます！通知テンプレート整えたらQAチームにも共有します。
```
```json
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('devteam123')/channels/messages",
  "team": {
    "id": "devteam123",
    "displayName": "設計・開発チーム"
  },
  "channels": [
    {
      "id": "19:general@thread.tacv2",
      "displayName": "一般",
      "messages": [
        {
          "id": "msg-001",
          "replyToId": null,
          "createdDateTime": "2025-10-23T05:02:00Z",
          "lastModifiedDateTime": "2025-10-23T05:02:00Z",
          "messageType": "message",
          "subject": "在庫APIレビュー結果共有",
          "from": {
            "user": {
              "id": "u-sato",
              "displayName": "佐藤健",
              "userPrincipalName": "ken.sato@contoso.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<p>在庫APIのレビューとマージ完了しました。<br/>共通エラーハンドリング仕様を統一する方向で進めます。<br/>外部システム連携のトークン認証方式については <at id=\"0\">高橋純</at> さんの提案案（JWT署名＋有効期限制御）を採用します。</p>"
          },
          "mentions": [
            {
              "id": 0,
              "mentionText": "高橋純",
              "mentioned": { "user": { "id": "u-takahashi", "displayName": "高橋純", "userPrincipalName": "jun.takahashi@contoso.com" } }
            }
          ],
          "attachments": [],
          "reactions": [],
          "replies": [
            {
              "id": "msg-001-r1",
              "replyToId": "msg-001",
              "createdDateTime": "2025-10-23T05:04:12Z",
              "from": { "user": { "id": "u-nakamura", "displayName": "中村優", "userPrincipalName": "yu.nakamura@contoso.com" } },
              "body": {
                "contentType": "html",
                "content": "<p><at id=\"0\">佐藤健</at> さん<br/>エラーフォーマットは <code>{\"error\":{\"code\":\"E001\",\"message\":\"xxx\",\"trace_id\":\"...\"}}</code> のような形式で定義する想定ですか？</p>"
              },
              "mentions": [
                { "id": 0, "mentionText": "佐藤健", "mentioned": { "user": { "id": "u-sato", "displayName": "佐藤健" } } }
              ]
            },
            {
              "id": "msg-001-r2",
              "replyToId": "msg-001",
              "createdDateTime": "2025-10-23T05:05:40Z",
              "from": { "user": { "id": "u-sato", "displayName": "佐藤健" } },
              "body": { "contentType": "html", "content": "<p>はい、その方向です。詳細は「API共通エラーフォーマット仕様（draft）」として<b>10/27</b>までに整理します。</p>" }
            },
            {
              "id": "msg-001-r3",
              "replyToId": "msg-001",
              "createdDateTime": "2025-10-23T05:07:00Z",
              "from": { "user": { "id": "u-takahashi", "displayName": "高橋純" } },
              "body": { "contentType": "html", "content": "<p>了解です。次回までに外部連携のトークン仕様書も併せてレビューします。</p>" }
            }
          ]
        },
        {
          "id": "msg-002",
          "replyToId": null,
          "createdDateTime": "2025-10-23T05:10:00Z",
          "lastModifiedDateTime": "2025-10-23T05:10:00Z",
          "messageType": "message",
          "subject": "会計APIテスト進捗",
          "from": { "user": { "id": "u-nakamura", "displayName": "中村優" } },
          "body": {
            "contentType": "html",
            "content": "<p>会計APIのテストコード追加が完了しました。<br/>モックデータ不整合が原因で一部テストが失敗していましたが修正済みです。<br/>販売APIとの結合テストを今週中（〜10/26）に実施予定です。</p>"
          },
          "mentions": [],
          "attachments": [],
          "reactions": [],
          "replies": [
            {
              "id": "msg-002-r1",
              "replyToId": "msg-002",
              "createdDateTime": "2025-10-23T05:12:05Z",
              "from": { "user": { "id": "u-ito", "displayName": "伊藤萌" } },
              "body": {
                "contentType": "html",
                "content": "<p><at id=\"0\">中村優</at> さん<br/>結合テストのログ出力フォーマットを統一しましょうか？テストカバレッジの再確認も一緒に進めます。</p>"
              },
              "mentions": [
                { "id": 0, "mentionText": "中村優", "mentioned": { "user": { "id": "u-nakamura", "displayName": "中村優" } } }
              ]
            },
            {
              "id": "msg-002-r2",
              "replyToId": "msg-002",
              "createdDateTime": "2025-10-23T05:13:10Z",
              "from": { "user": { "id": "u-nakamura", "displayName": "中村優" } },
              "body": { "contentType": "html", "content": "<p>お願いします。pytest --cov-report=xml の出力をまとめて次回共有します。</p>" }
            },
            {
              "id": "msg-002-r3",
              "replyToId": "msg-002",
              "createdDateTime": "2025-10-23T05:14:25Z",
              "from": { "user": { "id": "u-sato", "displayName": "佐藤健" } },
              "body": { "contentType": "html", "content": "<p>了解。次回（10/30）の定例で報告お願いします。</p>" }
            }
          ]
        },
        {
          "id": "msg-003",
          "replyToId": null,
          "createdDateTime": "2025-10-23T05:17:00Z",
          "lastModifiedDateTime": "2025-10-23T05:17:00Z",
          "messageType": "message",
          "subject": "フロントエンドとの連携確認",
          "from": { "user": { "id": "u-ishikawa", "displayName": "石川怜奈" } },
          "body": {
            "contentType": "html",
            "content": "<p>React UIのプロトタイプで、販売管理画面のAPI連携確認完了しました。<br/>ただし、/sales/list のレスポンス構造が変更（items → data）されていたため、モックを修正中です。</p>"
          },
          "mentions": [],
          "attachments": [],
          "reactions": [],
          "replies": [
            {
              "id": "msg-003-r1",
              "replyToId": "msg-003",
              "createdDateTime": "2025-10-23T05:18:20Z",
              "from": { "user": { "id": "u-takahashi", "displayName": "高橋純" } },
              "body": {
                "contentType": "html",
                "content": "<p><at id=\"0\">石川怜奈</at> さん<br/>バージョン管理ルールが曖昧なので、次回までにAPIバージョニングポリシーをまとめます（<at id=\"1\">佐藤健</at> さんと一緒に）。</p>"
              },
              "mentions": [
                { "id": 0, "mentionText": "石川怜奈", "mentioned": { "user": { "id": "u-ishikawa", "displayName": "石川怜奈" } } },
                { "id": 1, "mentionText": "佐藤健", "mentioned": { "user": { "id": "u-sato", "displayName": "佐藤健" } } }
              ]
            },
            {
              "id": "msg-003-r2",
              "replyToId": "msg-003",
              "createdDateTime": "2025-10-23T05:19:10Z",
              "from": { "user": { "id": "u-sato", "displayName": "佐藤健" } },
              "body": { "contentType": "html", "content": "<p>了解。v1.5 から v2.0 に上がる際の互換性基準も定義しておきましょう。</p>" }
            },
            {
              "id": "msg-003-r3",
              "replyToId": "msg-003",
              "createdDateTime": "2025-10-23T05:20:30Z",
              "from": { "user": { "id": "u-ishikawa", "displayName": "石川怜奈" } },
              "body": { "contentType": "html", "content": "<p>承知です。UI側のAPIモック更新は10/26までに完了させます。</p>" }
            }
          ]
        },
        {
          "id": "msg-004",
          "replyToId": null,
          "createdDateTime": "2025-10-23T05:23:00Z",
          "lastModifiedDateTime": "2025-10-23T05:23:00Z",
          "messageType": "message",
          "subject": "APIゲートウェイ設計方針",
          "from": { "user": { "id": "u-takahashi", "displayName": "高橋純" } },
          "body": {
            "contentType": "html",
            "content": "<p>APIゲートウェイ設計の初回レビュー結果を共有します。<br/>認証・認可を統合的に扱うため、AWS API Gateway + Lambda + Cognito連携案で進める予定です。<br/>スケーラビリティ面を考慮して、将来的にエッジキャッシュ構成も検討中です。</p>"
          },
          "mentions": [],
          "attachments": [],
          "reactions": [],
          "replies": [
            {
              "id": "msg-004-r1",
              "replyToId": "msg-004",
              "createdDateTime": "2025-10-23T05:25:10Z",
              "from": { "user": { "id": "u-kawai", "displayName": "河合亮" } },
              "body": { "contentType": "html", "content": "<p>了解です。CI/CD経由でデプロイする際、ステージごとの環境変数はSSM経由で読み込む構成にします。</p>" }
            },
            {
              "id": "msg-004-r2",
              "replyToId": "msg-004",
              "createdDateTime": "2025-10-23T05:26:20Z",
              "from": { "user": { "id": "u-sato", "displayName": "佐藤健" } },
              "body": {
                "contentType": "html",
                "content": "<p>OK。<at id=\"0\">高橋純</at> さん・<at id=\"1\">河合亮</at> さんで<b>10/29</b>までに詳細設計まとめをお願いします。レビューは次回会議で行いましょう。</p>"
              },
              "mentions": [
                { "id": 0, "mentionText": "高橋純", "mentioned": { "user": { "id": "u-takahashi", "displayName": "高橋純" } } },
                { "id": 1, "mentionText": "河合亮", "mentioned": { "user": { "id": "u-kawai", "displayName": "河合亮" } } }
              ]
            }
          ]
        },
        {
          "id": "msg-005",
          "replyToId": null,
          "createdDateTime": "2025-10-23T05:30:00Z",
          "lastModifiedDateTime": "2025-10-23T05:30:00Z",
          "messageType": "message",
          "subject": "統合テストとCI/CD整備",
          "from": { "user": { "id": "u-ito", "displayName": "伊藤萌" } },
          "body": {
            "contentType": "html",
            "content": "<p>販売APIの統合テストを実施しました。80件中78件成功です。<br/>失敗した2件はモックデータと期待値不一致によるものです。修正中。</p>"
          },
          "mentions": [],
          "attachments": [],
          "reactions": [],
          "replies": [
            {
              "id": "msg-005-r1",
              "replyToId": "msg-005",
              "createdDateTime": "2025-10-23T05:31:10Z",
              "from": { "user": { "id": "u-kawai", "displayName": "河合亮" } },
              "body": {
                "contentType": "html",
                "content": "<p>CI/CDパイプラインの自動デプロイ設定を本番相当環境に適用済みです。<br/>次はSlack通知の自動化を組み込み予定。<br/><at id=\"0\">伊藤萌</at> さん、テスト完了時のSlack通知にWebhook使っていいですか？</p>"
              },
              "mentions": [
                { "id": 0, "mentionText": "伊藤萌", "mentioned": { "user": { "id": "u-ito", "displayName": "伊藤萌" } } }
              ]
            },
            {
              "id": "msg-005-r2",
              "replyToId": "msg-005",
              "createdDateTime": "2025-10-23T05:32:00Z",
              "from": { "user": { "id": "u-ito", "displayName": "伊藤萌" } },
              "body": { "contentType": "html", "content": "<p>OKです。通知内容は成功率とエラー件数を入れてください。</p>" }
            },
            {
              "id": "msg-005-r3",
              "replyToId": "msg-005",
              "createdDateTime": "2025-10-23T05:33:00Z",
              "from": { "user": { "id": "u-kawai", "displayName": "河合亮" } },
              "body": { "contentType": "html", "content": "<p>了解。<b>10/28</b>までにSlack連携完了させます。</p>" }
            },
            {
              "id": "msg-005-r4",
              "replyToId": "msg-005",
              "createdDateTime": "2025-10-23T05:34:30Z",
              "from": { "user": { "id": "u-takahashi", "displayName": "高橋純" } },
              "body": { "contentType": "html", "content": "<p>素晴らしい進捗です。CI実行トリガーの自動化も次フェーズで検討しましょう。</p>" }
            }
          ]
        }
      ]
    },
    {
      "id": "19:notice@thread.tacv2",
      "displayName": "連絡",
      "messages": [
        {
          "id": "msg-006",
          "replyToId": null,
          "createdDateTime": "2025-10-23T05:40:00Z",
          "lastModifiedDateTime": "2025-10-23T05:40:00Z",
          "messageType": "message",
          "subject": "アクションアイテム整理",
          "from": { "user": { "id": "u-sato", "displayName": "佐藤健" } },
          "body": {
            "contentType": "html",
            "content": "<p>今週のアクションアイテムを共有します👇</p><table><tr><th>No</th><th>内容</th><th>担当</th><th>期限</th></tr><tr><td>1</td><td>API共通エラーフォーマット定義</td><td>佐藤</td><td>10/27</td></tr><tr><td>2</td><td>結合テスト結果報告・網羅率確認</td><td>中村・伊藤</td><td>10/28</td></tr><tr><td>3</td><td>バージョニングポリシー策定</td><td>高橋・佐藤</td><td>10/29</td></tr><tr><td>4</td><td>APIゲートウェイ詳細設計</td><td>高橋・河合</td><td>10/29</td></tr><tr><td>5</td><td>UI側APIモック更新</td><td>石川</td><td>10/26</td></tr><tr><td>6</td><td>Slack通知連携構築</td><td>河合</td><td>10/28</td></tr></table>"
          },
          "mentions": [],
          "attachments": [],
          "reactions": [],
          "replies": [
            {
              "id": "msg-006-r1",
              "replyToId": "msg-006",
              "createdDateTime": "2025-10-23T05:42:00Z",
              "from": { "user": { "id": "u-takahashi", "displayName": "高橋純" } },
              "body": { "contentType": "html", "content": "<p>ありがとうございます。進捗は <code>#dev_progress</code> チャンネルで日次更新します。</p>" }
            }
          ]
        },
        {
          "id": "msg-007",
          "replyToId": null,
          "createdDateTime": "2025-10-23T05:45:00Z",
          "lastModifiedDateTime": "2025-10-23T05:45:00Z",
          "messageType": "message",
          "subject": "次回会議案内",
          "from": { "user": { "id": "u-ito", "displayName": "伊藤萌" } },
          "body": {
            "contentType": "html",
            "content": "<p>📅 次回会議の予定です。<br/>日時：<b>10/30（木） 14:00〜15:30</b><br/>議題：<br/>・統合テスト結果レビュー<br/>・APIバージョニング方針の最終確認<br/>・デプロイ手順書レビュー<br/><br/><a href=\"https://teams.microsoft.com/l/meetup-join/19%3Ameeting_link\">Teams Meeting Link</a></p>"
          },
          "mentions": [],
          "attachments": [],
          "reactions": [],
          "replies": [
            {
              "id": "msg-007-r1",
              "replyToId": "msg-007",
              "createdDateTime": "2025-10-23T05:46:10Z",
              "from": { "user": { "id": "u-sato", "displayName": "佐藤健" } },
              "body": { "contentType": "html", "content": "<p>了解です。当日はゲートウェイ詳細設計とバージョン方針を共有します。</p>" }
            }
          ]
        }
      ]
    },
    {
      "id": "19:tech-share@thread.tacv2",
      "displayName": "技術共有",
      "messages": [
        {
          "id": "msg-008",
          "replyToId": null,
          "createdDateTime": "2025-10-23T05:55:00Z",
          "lastModifiedDateTime": "2025-10-23T05:55:00Z",
          "messageType": "message",
          "subject": "API共通エラーフォーマット案共有",
          "from": { "user": { "id": "u-sato", "displayName": "佐藤健" } },
          "body": {
            "contentType": "html",
            "content": "<p>共通エラーフォーマットのドラフトを作成しました。</p><pre><code>{\n  \"error\": {\n    \"code\": \"E001\",\n    \"message\": \"Invalid parameter\",\n    \"trace_id\": \"abcd1234efgh5678\"\n  }\n}\n</code></pre><p>全APIでこの形式を返す想定です。意見があればコメントください。</p>"
          },
          "mentions": [],
          "attachments": [],
          "reactions": [],
          "replies": [
            {
              "id": "msg-008-r1",
              "replyToId": "msg-008",
              "createdDateTime": "2025-10-23T05:56:20Z",
              "from": { "user": { "id": "u-nakamura", "displayName": "中村優" } },
              "body": { "contentType": "html", "content": "<p>了解です。<code>detail</code> フィールド追加を提案します。開発ログ連携で活用できそうです。</p>" }
            },
            {
              "id": "msg-008-r2",
              "replyToId": "msg-008",
              "createdDateTime": "2025-10-23T05:57:10Z",
              "from": { "user": { "id": "u-takahashi", "displayName": "高橋純" } },
              "body": { "contentType": "html", "content": "<p>良いですね。正式定義時にオプション項目として追加しましょう。</p>" }
            }
          ]
        },
        {
          "id": "msg-009",
          "replyToId": null,
          "createdDateTime": "2025-10-23T06:00:00Z",
          "lastModifiedDateTime": "2025-10-23T06:00:00Z",
          "messageType": "message",
          "subject": "Slack通知連携Tips",
          "from": { "user": { "id": "u-kawai", "displayName": "河合亮" } },
          "body": {
            "contentType": "html",
            "content": "<p>CI/CDのSlack通知はGitHub ActionsとWebhookでつなげます。通知例👇</p><pre><code>✅ 統合テスト完了\n成功率: 97.5%（78/80）\n担当: 伊藤・中村\n</code></pre><p>Webhook URLは <code>devops-config/slack.env</code> に格納します。</p>"
          },
          "mentions": [],
          "attachments": [],
          "reactions": [],
          "replies": [
            {
              "id": "msg-009-r1",
              "replyToId": "msg-009",
              "createdDateTime": "2025-10-23T06:01:30Z",
              "from": { "user": { "id": "u-ito", "displayName": "伊藤萌" } },
              "body": { "contentType": "html", "content": "<p>ありがとうございます！通知テンプレート整えたらQAチームにも共有します。</p>" }
            }
          ]
        }
      ]
    }
  ]
}

```
# outlook

## チーム1　予定表例
```text
🗓 2025年10月26日（日）
【締切】UI側APIモック更新（担当：石川怜奈）

販売管理画面のAPIモックを最新仕様に合わせて更新するタスク。
UIとバックエンドの接続確認を行い、レスポンス構造の変更に対応する。

期限：10月26日（日）

担当：石川怜奈

依頼者：佐藤健（開発リーダー）

会議・作業形態：なし（個別作業）

🗓 2025年10月27日（月）
【締切】API共通エラーフォーマット定義（担当：佐藤健）

API全体で統一的に扱うエラーレスポンス形式を定義。
code・messageを必須項目とし、内部用にtrace_idを追加予定。

期限：10月27日（月）

担当：佐藤健

目的：チーム内でのエラーハンドリング仕様統一

会議・作業形態：なし（仕様ドキュメント作成）

🗓 2025年10月28日（火）
【デモ】Slack通知連携（CI結果の自動通知）

GitHub Actions の workflow_run イベントを用いて、CI/CD実行結果をSlackの #api-ci通知 チャンネルに自動投稿する仕組みのデモ。
通知フォーマット（成功/失敗アイコンなど）を確認。

時間：11:00〜11:30

場所：Teamsオンライン会議

登壇者：河合亮

参加者：佐藤健、伊藤萌（オプション）

【締切】結合テスト結果報告・網羅率確認（中村優・伊藤萌）

販売APIと会計APIの結合テスト結果を報告。
テストケースのカバレッジ（網羅率）を再確認し、80%以上を目標とする。

期限：10月28日（火）

担当：中村優、伊藤萌

関連：会計APIテスト・販売API結合テスト

🗓 2025年10月29日（水）
【レビュー】APIバージョニングポリシー策定（高橋・佐藤）

APIのバージョン管理方針を最終決定。
URLベース（例：/api/v1/）を基本とし、内部APIのみ X-API-Version ヘッダ利用も検討。

時間：15:00〜16:00

場所：Teamsオンライン会議

出席者：高橋純、佐藤健

【レビュー】APIゲートウェイ詳細設計（高橋・河合）

認証・認可を統合的に扱うAPIゲートウェイの詳細設計レビュー。
今後のスケーラビリティ対応を見据え、AWS API Gateway＋Lambda連携も検討。

時間：16:00〜17:00

場所：Teamsオンライン会議

出席者：高橋純、河合亮

🗓 2025年10月30日（木）
【定例会議】設計・開発チーム 定例ミーティング

販売管理機能の開発進捗確認と、次フェーズの整備方針を議論。
主な議題：

統合テスト結果レビュー（全80件成功：伊藤）

APIバージョニング方針の最終確認（高橋・佐藤）

デプロイ手順書のレビュー（河合）

時間：14:00〜15:30

場所：Teamsオンライン会議

出席者：佐藤健、中村優、石川怜奈、高橋純、伊藤萌、河合亮

主催：佐藤健

```
```json
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/calendarView",
  "value": [
    {
      "id": "evt-ui-mock-deadline-20251026",
      "createdDateTime": "2025-10-24T01:40:30Z",
      "lastModifiedDateTime": "2025-10-24T01:40:30Z",
      "changeKey": "CQAAABYAAA==",
      "categories": ["Deadline"],
      "originalStartTimeZone": "Asia/Tokyo",
      "originalEndTimeZone": "Asia/Tokyo",
      "iCalUId": "040000008200E00074C5B7101A82E008000000001234abcd@contoso.com",
      "reminderMinutesBeforeStart": 60,
      "isReminderOn": true,
      "hasAttachments": false,
      "subject": "【締切】UI側APIモック更新（石川）",
      "bodyPreview": "アクション#5：10/26まで。販売管理画面のAPIモック更新。",
      "importance": "normal",
      "sensitivity": "normal",
      "isAllDay": true,
      "isCancelled": false,
      "isOrganizer": true,
      "responseRequested": false,
      "showAs": "free",
      "type": "singleInstance",
      "webLink": "https://outlook.office.com/calendar/item/evt-ui-mock-deadline-20251026",
      "onlineMeetingProvider": "unknown",
      "start": { "dateTime": "2025-10-26T00:00:00", "timeZone": "Asia/Tokyo" },
      "end": { "dateTime": "2025-10-27T00:00:00", "timeZone": "Asia/Tokyo" },
      "location": { "displayName": "" },
      "attendees": [
        {
          "type": "required",
          "status": { "response": "accepted", "time": "2025-10-24T01:41:00Z" },
          "emailAddress": { "name": "石川怜奈", "address": "ishikawa@example.com" }
        }
      ],
      "organizer": { "emailAddress": { "name": "佐藤健", "address": "sato@example.com" } }
    },
    {
      "id": "evt-error-format-deadline-20251027",
      "createdDateTime": "2025-10-24T01:42:10Z",
      "lastModifiedDateTime": "2025-10-24T01:42:10Z",
      "changeKey": "CQAAABYAAQ==",
      "categories": ["Deadline"],
      "originalStartTimeZone": "Asia/Tokyo",
      "originalEndTimeZone": "Asia/Tokyo",
      "iCalUId": "040000008200E00074C5B7101A82E00800000000abcd1234@contoso.com",
      "reminderMinutesBeforeStart": 120,
      "isReminderOn": true,
      "hasAttachments": false,
      "subject": "【締切】API共通エラーフォーマット定義（佐藤）",
      "bodyPreview": "アクション#1：10/27まで。code/message/trace_id を含む共通仕様。",
      "importance": "normal",
      "sensitivity": "normal",
      "isAllDay": true,
      "isCancelled": false,
      "isOrganizer": true,
      "responseRequested": false,
      "showAs": "free",
      "type": "singleInstance",
      "webLink": "https://outlook.office.com/calendar/item/evt-error-format-deadline-20251027",
      "onlineMeetingProvider": "unknown",
      "start": { "dateTime": "2025-10-27T00:00:00", "timeZone": "Asia/Tokyo" },
      "end": { "dateTime": "2025-10-28T00:00:00", "timeZone": "Asia/Tokyo" },
      "location": { "displayName": "" },
      "attendees": [
        {
          "type": "required",
          "status": { "response": "accepted", "time": "2025-10-24T01:43:00Z" },
          "emailAddress": { "name": "佐藤健", "address": "sato@example.com" }
        }
      ],
      "organizer": { "emailAddress": { "name": "佐藤健", "address": "sato@example.com" } }
    },
    {
      "id": "evt-slack-ci-demo-20251028-1100",
      "createdDateTime": "2025-10-24T01:45:00Z",
      "lastModifiedDateTime": "2025-10-24T01:45:00Z",
      "changeKey": "CQAAABYAAw==",
      "categories": ["Review"],
      "originalStartTimeZone": "Asia/Tokyo",
      "originalEndTimeZone": "Asia/Tokyo",
      "iCalUId": "040000008200E00074C5B7101A82E00800000000beef0001@contoso.com",
      "reminderMinutesBeforeStart": 15,
      "isReminderOn": true,
      "hasAttachments": false,
      "subject": "Slack通知連携デモ（CI結果の自動通知）",
      "body": {
        "contentType": "html",
        "content": "河合さんより GitHub Actions <code>workflow_run</code> を用いた Slack 通知のデモ。<br/>チャンネル: #api-ci通知<br/>成果物: 通知フォーマット（成功/失敗アイコン含む）"
      },
      "bodyPreview": "GitHub Actions と Slack の連携デモ。#api-ci通知 へ投稿。",
      "importance": "normal",
      "sensitivity": "normal",
      "isAllDay": false,
      "isCancelled": false,
      "isOrganizer": true,
      "responseRequested": true,
      "showAs": "busy",
      "type": "singleInstance",
      "webLink": "https://outlook.office.com/calendar/item/evt-slack-ci-demo-20251028-1100",
      "isOnlineMeeting": true,
      "onlineMeetingProvider": "teamsForBusiness",
      "onlineMeeting": {
        "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting%3Aslack-demo",
        "conferenceId": "123 456 789#",
        "tollNumber": "+81 3-1234-5678"
      },
      "start": { "dateTime": "2025-10-28T11:00:00", "timeZone": "Asia/Tokyo" },
      "end": { "dateTime": "2025-10-28T11:30:00", "timeZone": "Asia/Tokyo" },
      "location": { "displayName": "Teams 会議" },
      "attendees": [
        { "type": "required", "status": { "response": "accepted", "time": "2025-10-24T01:46:00Z" }, "emailAddress": { "name": "河合亮", "address": "kawai@example.com" } },
        { "type": "required", "status": { "response": "accepted", "time": "2025-10-24T01:46:10Z" }, "emailAddress": { "name": "佐藤健", "address": "sato@example.com" } },
        { "type": "optional", "status": { "response": "accepted", "time": "2025-10-24T01:46:20Z" }, "emailAddress": { "name": "伊藤萌", "address": "ito@example.com" } }
      ],
      "organizer": { "emailAddress": { "name": "河合亮", "address": "kawai@example.com" } }
    },
    {
      "id": "evt-it-coverage-report-20251028",
      "createdDateTime": "2025-10-24T01:47:10Z",
      "lastModifiedDateTime": "2025-10-24T01:47:10Z",
      "changeKey": "CQAAABYABQ==",
      "categories": ["Deadline"],
      "originalStartTimeZone": "Asia/Tokyo",
      "originalEndTimeZone": "Asia/Tokyo",
      "iCalUId": "040000008200E00074C5B7101A82E00800000000beef0002@contoso.com",
      "reminderMinutesBeforeStart": 120,
      "isReminderOn": true,
      "hasAttachments": false,
      "subject": "【締切】結合テスト結果報告・網羅率確認（中村・伊藤）",
      "bodyPreview": "アクション#2：10/28まで。pytestカバレッジ80%以上を目標に集計。",
      "importance": "normal",
      "sensitivity": "normal",
      "isAllDay": true,
      "isCancelled": false,
      "isOrganizer": true,
      "responseRequested": false,
      "showAs": "free",
      "type": "singleInstance",
      "webLink": "https://outlook.office.com/calendar/item/evt-it-coverage-report-20251028",
      "start": { "dateTime": "2025-10-28T00:00:00", "timeZone": "Asia/Tokyo" },
      "end": { "dateTime": "2025-10-29T00:00:00", "timeZone": "Asia/Tokyo" },
      "location": { "displayName": "" },
      "attendees": [
        { "type": "required", "status": { "response": "accepted", "time": "2025-10-24T01:47:30Z" }, "emailAddress": { "name": "中村優", "address": "nakamura@example.com" } },
        { "type": "required", "status": { "response": "accepted", "time": "2025-10-24T01:47:40Z" }, "emailAddress": { "name": "伊藤萌", "address": "ito@example.com" } }
      ],
      "organizer": { "emailAddress": { "name": "伊藤萌", "address": "ito@example.com" } }
    },
    {
      "id": "evt-api-versioning-20251029-1500",
      "createdDateTime": "2025-10-24T01:50:00Z",
      "lastModifiedDateTime": "2025-10-24T01:50:00Z",
      "changeKey": "CQAAABYABw==",
      "categories": ["Review"],
      "originalStartTimeZone": "Asia/Tokyo",
      "originalEndTimeZone": "Asia/Tokyo",
      "iCalUId": "040000008200E00074C5B7101A82E00800000000beef0003@contoso.com",
      "reminderMinutesBeforeStart": 30,
      "isReminderOn": true,
      "hasAttachments": false,
      "subject": "APIバージョニングポリシー策定（高橋・佐藤）",
      "body": {
        "contentType": "html",
        "content": "URLバージョン（/api/v1/）を基本に、内部APIは必要に応じて <code>X-API-Version</code> も検討。"
      },
      "bodyPreview": "URLバージョン基本。内部APIはヘッダ版を検討。",
      "importance": "normal",
      "sensitivity": "normal",
      "isAllDay": false,
      "isCancelled": false,
      "isOrganizer": true,
      "responseRequested": true,
      "showAs": "busy",
      "type": "singleInstance",
      "webLink": "https://outlook.office.com/calendar/item/evt-api-versioning-20251029-1500",
      "isOnlineMeeting": true,
      "onlineMeetingProvider": "teamsForBusiness",
      "onlineMeeting": {
        "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting%3Aversioning",
        "conferenceId": "222 333 444#",
        "tollNumber": "+81 3-9876-5432"
      },
      "start": { "dateTime": "2025-10-29T15:00:00", "timeZone": "Asia/Tokyo" },
      "end": { "dateTime": "2025-10-29T16:00:00", "timeZone": "Asia/Tokyo" },
      "location": { "displayName": "Teams 会議" },
      "attendees": [
        { "type": "required", "status": { "response": "accepted", "time": "2025-10-24T01:50:30Z" }, "emailAddress": { "name": "高橋純", "address": "takahashi@example.com" } },
        { "type": "required", "status": { "response": "accepted", "time": "2025-10-24T01:50:35Z" }, "emailAddress": { "name": "佐藤健", "address": "sato@example.com" } }
      ],
      "organizer": { "emailAddress": { "name": "高橋純", "address": "takahashi@example.com" } }
    },
    {
      "id": "evt-api-gateway-detail-20251029-1600",
      "createdDateTime": "2025-10-24T01:52:20Z",
      "lastModifiedDateTime": "2025-10-24T01:52:20Z",
      "changeKey": "CQAAABYACQ==",
      "categories": ["Review"],
      "originalStartTimeZone": "Asia/Tokyo",
      "originalEndTimeZone": "Asia/Tokyo",
      "iCalUId": "040000008200E00074C5B7101A82E00800000000beef0004@contoso.com",
      "reminderMinutesBeforeStart": 30,
      "isReminderOn": true,
      "hasAttachments": false,
      "subject": "APIゲートウェイ詳細設計レビュー（高橋・河合）",
      "bodyPreview": "認証・認可の統合、将来のスケーラビリティ（AWS API Gateway + Lambda）方針レビュー。",
      "importance": "normal",
      "sensitivity": "normal",
      "isAllDay": false,
      "isCancelled": false,
      "isOrganizer": true,
      "responseRequested": true,
      "showAs": "busy",
      "type": "singleInstance",
      "webLink": "https://outlook.office.com/calendar/item/evt-api-gateway-detail-20251029-1600",
      "isOnlineMeeting": true,
      "onlineMeetingProvider": "teamsForBusiness",
      "onlineMeeting": {
        "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting%3Agateway",
        "conferenceId": "555 666 777#",
        "tollNumber": "+81 3-1111-2222"
      },
      "start": { "dateTime": "2025-10-29T16:00:00", "timeZone": "Asia/Tokyo" },
      "end": { "dateTime": "2025-10-29T17:00:00", "timeZone": "Asia/Tokyo" },
      "location": { "displayName": "Teams 会議" },
      "attendees": [
        { "type": "required", "status": { "response": "accepted", "time": "2025-10-24T01:52:40Z" }, "emailAddress": { "name": "高橋純", "address": "takahashi@example.com" } },
        { "type": "required", "status": { "response": "accepted", "time": "2025-10-24T01:52:50Z" }, "emailAddress": { "name": "河合亮", "address": "kawai@example.com" } }
      ],
      "organizer": { "emailAddress": { "name": "高橋純", "address": "takahashi@example.com" } }
    },
    {
      "id": "evt-regular-meeting-20251030-1400",
      "createdDateTime": "2025-10-24T01:55:00Z",
      "lastModifiedDateTime": "2025-10-24T01:55:00Z",
      "changeKey": "CQAAABYACw==",
      "categories": ["Meeting"],
      "originalStartTimeZone": "Asia/Tokyo",
      "originalEndTimeZone": "Asia/Tokyo",
      "iCalUId": "040000008200E00074C5B7101A82E00800000000beef0005@contoso.com",
      "reminderMinutesBeforeStart": 15,
      "isReminderOn": true,
      "hasAttachments": false,
      "subject": "設計・開発チーム 定例：統合テスト結果/バージョニング/デプロイ手順レビュー",
      "body": {
        "contentType": "html",
        "content": "議題:<br/>・統合テスト結果レビュー（全80件成功：伊藤）<br/>・APIバージョニング方針の最終確認（高橋・佐藤）<br/>・デプロイ手順書レビュー（河合）"
      },
      "bodyPreview": "統合テスト結果、バージョニング最終、デプロイ手順レビュー。",
      "importance": "normal",
      "sensitivity": "normal",
      "isAllDay": false,
      "isCancelled": false,
      "isOrganizer": true,
      "responseRequested": true,
      "showAs": "busy",
      "type": "singleInstance",
      "webLink": "https://outlook.office.com/calendar/item/evt-regular-meeting-20251030-1400",
      "isOnlineMeeting": true,
      "onlineMeetingProvider": "teamsForBusiness",
      "onlineMeeting": {
        "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting%3Aregular-1400",
        "conferenceId": "888 999 000#",
        "tollNumber": "+81 3-2468-1357"
      },
      "start": { "dateTime": "2025-10-30T14:00:00", "timeZone": "Asia/Tokyo" },
      "end": { "dateTime": "2025-10-30T15:30:00", "timeZone": "Asia/Tokyo" },
      "location": { "displayName": "Teams 会議" },
      "attendees": [
        { "type": "required", "status": { "response": "accepted", "time": "2025-10-24T01:55:20Z" }, "emailAddress": { "name": "佐藤健", "address": "sato@example.com" } },
        { "type": "required", "status": { "response": "accepted", "time": "2025-10-24T01:55:25Z" }, "emailAddress": { "name": "中村優", "address": "nakamura@example.com" } },
        { "type": "required", "status": { "response": "accepted", "time": "2025-10-24T01:55:30Z" }, "emailAddress": { "name": "石川怜奈", "address": "ishikawa@example.com" } },
        { "type": "required", "status": { "response": "accepted", "time": "2025-10-24T01:55:35Z" }, "emailAddress": { "name": "高橋純", "address": "takahashi@example.com" } },
        { "type": "required", "status": { "response": "accepted", "time": "2025-10-24T01:55:40Z" }, "emailAddress": { "name": "伊藤萌", "address": "ito@example.com" } },
        { "type": "required", "status": { "response": "accepted", "time": "2025-10-24T01:55:45Z" }, "emailAddress": { "name": "河合亮", "address": "kawai@example.com" } }
      ],
      "organizer": { "emailAddress": { "name": "佐藤健", "address": "sato@example.com" } }
    }
  ]
}
```

## outlookチーム２例
```
📅 会議：「テスト・品質保証チーム 次回会議」

🕓 時間：10月28日（火）16:00〜17:00

👤 主催者：山本綾子

💬 内容：Teams会議、参加者3名（山本・藤原・岡田）

💻 ミーティング：「CI/CD連携調整MTG」

🕒 時間：10月25日（土）15:00〜15:30

👤 主催者：藤原光

💬 内容：DevOpsチームの河合とAzure Pipelineの並列実行設定を調整

📌 タスク期限：「不具合報告テンプレート共有」

🗓 日付：10月26日（日）

👤 担当：岡田奈々

💬 内容：修正版テンプレートを共有フォルダにアップロード

📌 タスク期限：「自動テスト修正・確認」

🗓 日付：10月27日（月）

👤 担当：藤原光

💬 内容：UI変更に伴うテストスクリプト修正と動作確認の完了

📋 会議：「テスト項目書更新」

🗓 日付：10月25日（土）

👤 主催者：山本綾子

💬 内容：設計・開発チームからの最新API一覧を反映後、テスト項目書をレビュー

🧪 統合テスト期間：「統合テスト（第1週〜第2週）」

🗓 期間：11月4日（月）〜11月15日（土）

👤 主催者：山本綾子

💬 内容：全機能の統合テストを実施。終日イベント（全期間対象）

🔔 リマインダー：「QA日次報告」

🕠 時間：毎日17:30（期間：11月4日〜11月15日）

👤 作成者：山本綾子

💬 内容：統合テスト期間中、日次進捗をTeamsチャンネル #qa_daily に投稿
```

```json
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#me/calendarView",
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/me/calendarView?startDateTime=2025-10-24T00:00:00Z&endDateTime=2025-11-16T00:00:00Z&$top=50&$skip=50",
  "value": [
    {
      "id": "AAMkAGQA1bYAAA==",
      "createdDateTime": "2025-10-24T00:05:33Z",
      "lastModifiedDateTime": "2025-10-24T00:05:33Z",
      "changeKey": "7k5u6pQAAk6=",
      "categories": [ "QA", "Deadline" ],
      "originalStartTimeZone": "Asia/Tokyo",
      "originalEndTimeZone": "Asia/Tokyo",
      "iCalUId": "040000008200E00074C5B7101A82E00800000000D02E3B9F5C4FD801000000000000000010000000E1",
      "reminderMinutesBeforeStart": 30,
      "isReminderOn": true,
      "hasAttachments": false,
      "subject": "アクション期限: 最新API一覧反映（テスト項目書）",
      "bodyPreview": "設計・開発チームからの最新API一覧を反映し、テスト項目書を更新する（担当：山本、期限：10/25）。",
      "importance": "normal",
      "sensitivity": "normal",
      "isAllDay": false,
      "isCancelled": false,
      "isOrganizer": true,
      "responseRequested": false,
      "seriesMasterId": null,
      "showAs": "free",
      "type": "singleInstance",
      "webLink": "https://outlook.office.com/calendar/item/AAMkAGQA1bYAAA==",
      "onlineMeetingUrl": null,
      "start": {
        "dateTime": "2025-10-25T10:00:00",
        "timeZone": "Asia/Tokyo"
      },
      "end": {
        "dateTime": "2025-10-25T10:30:00",
        "timeZone": "Asia/Tokyo"
      },
      "location": {
        "displayName": "自席/リモート",
        "locationType": "default",
        "uniqueIdType": "unknown",
        "address": {}
      },
      "locations": [],
      "recurrence": null,
      "responseStatus": {
        "response": "organizer",
        "time": "2025-10-24T00:05:33Z"
      },
      "organizer": {
        "emailAddress": {
          "name": "山本綾子",
          "address": "ayako.yamamoto@contoso.com"
        }
      },
      "attendees": [
        {
          "type": "required",
          "status": { "response": "accepted", "time": "2025-10-24T00:06:15Z" },
          "emailAddress": { "name": "山本綾子", "address": "ayako.yamamoto@contoso.com" }
        }
      ],
      "body": {
        "contentType": "html",
        "content": "<p>設計・開発チームからの最新API一覧を受領後、テスト項目書を更新（担当：山本）。<br/>期限：<b>2025/10/25</b></p>"
      }
    },
    {
      "id": "AAMkAGQA1bYAAB==",
      "createdDateTime": "2025-10-24T00:18:10Z",
      "lastModifiedDateTime": "2025-10-24T00:19:02Z",
      "changeKey": "8l2J9QpAAk9=",
      "categories": [ "QA", "DevOps" ],
      "originalStartTimeZone": "Asia/Tokyo",
      "originalEndTimeZone": "Asia/Tokyo",
      "iCalUId": "040000008200E00074C5B7101A82E00800000000D02E3B9F5C4FD801000000000000000010000000E2",
      "reminderMinutesBeforeStart": 15,
      "isReminderOn": true,
      "hasAttachments": false,
      "subject": "CI/CD連携調整ミーティング（藤原 × 河合）",
      "bodyPreview": "Azure Pipeline の並列実行設定、ジョブ分割サンプル確認。10/25 15:00（JST）。",
      "importance": "normal",
      "sensitivity": "normal",
      "isAllDay": false,
      "isCancelled": false,
      "isOrganizer": true,
      "responseRequested": true,
      "seriesMasterId": null,
      "showAs": "busy",
      "type": "singleInstance",
      "webLink": "https://outlook.office.com/calendar/item/AAMkAGQA1bYAAB==",
      "onlineMeetingUrl": "https://teams.microsoft.com/l/meetup-join/19%3Ameeting_ci_cd_sync",
      "onlineMeeting": {
        "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3Ameeting_ci_cd_sync"
      },
      "start": {
        "dateTime": "2025-10-25T15:00:00",
        "timeZone": "Asia/Tokyo"
      },
      "end": {
        "dateTime": "2025-10-25T15:30:00",
        "timeZone": "Asia/Tokyo"
      },
      "location": {
        "displayName": "Microsoft Teams 会議",
        "locationType": "online",
        "uniqueIdType": "unknown",
        "address": {}
      },
      "locations": [
        {
          "displayName": "Microsoft Teams 会議",
          "locationType": "online",
          "uniqueIdType": "unknown",
          "address": {}
        }
      ],
      "recurrence": null,
      "responseStatus": {
        "response": "organizer",
        "time": "2025-10-24T00:18:10Z"
      },
      "organizer": {
        "emailAddress": {
          "name": "藤原光",
          "address": "hikaru.fujiwara@contoso.com"
        }
      },
      "attendees": [
        {
          "type": "required",
          "status": { "response": "accepted", "time": "2025-10-24T00:22:11Z" },
          "emailAddress": { "name": "河合（DevOps）", "address": "kawai.devops@contoso.com" }
        }
      ],
      "body": {
        "contentType": "html",
        "content": "<p>目的：Azure Pipeline の並列実行設定、ジョブ分割サンプルの確認。<br/>議事：CI連携方式確認 / サンプルyaml確認 / 実行時間短縮策</p>"
      }
    },
    {
      "id": "AAMkAGQA1bYAAc==",
      "createdDateTime": "2025-10-24T00:20:45Z",
      "lastModifiedDateTime": "2025-10-24T00:21:10Z",
      "changeKey": "kKX1nQeAAk0=",
      "categories": [ "QA", "Deadline" ],
      "originalStartTimeZone": "Asia/Tokyo",
      "originalEndTimeZone": "Asia/Tokyo",
      "iCalUId": "040000008200E00074C5B7101A82E00800000000D02E3B9F5C4FD801000000000000000010000000E3",
      "reminderMinutesBeforeStart": 30,
      "isReminderOn": true,
      "hasAttachments": false,
      "subject": "アクション期限: 不具合報告テンプレート共有（岡田）",
      "bodyPreview": "不具合報告テンプレートの最終化と共有（担当：岡田、期限：10/26）。",
      "importance": "normal",
      "sensitivity": "normal",
      "isAllDay": false,
      "isCancelled": false,
      "isOrganizer": true,
      "responseRequested": false,
      "seriesMasterId": null,
      "showAs": "free",
      "type": "singleInstance",
      "webLink": "https://outlook.office.com/calendar/item/AAMkAGQA1bYAAc==",
      "onlineMeetingUrl": null,
      "start": {
        "dateTime": "2025-10-26T10:00:00",
        "timeZone": "Asia/Tokyo"
      },
      "end": {
        "dateTime": "2025-10-26T10:30:00",
        "timeZone": "Asia/Tokyo"
      },
      "location": {
        "displayName": "SharePoint/Teams 共有フォルダ",
        "locationType": "default",
        "uniqueIdType": "unknown",
        "address": {}
      },
      "locations": [],
      "recurrence": null,
      "responseStatus": {
        "response": "organizer",
        "time": "2025-10-24T00:20:45Z"
      },
      "organizer": {
        "emailAddress": {
          "name": "岡田奈々",
          "address": "nana.okada@contoso.com"
        }
      },
      "attendees": [
        {
          "type": "required",
          "status": { "response": "accepted", "time": "2025-10-24T00:22:55Z" },
          "emailAddress": { "name": "岡田奈々", "address": "nana.okada@contoso.com" }
        }
      ],
      "body": {
        "contentType": "html",
        "content": "<p>不具合報告テンプレートの必須項目（再現手順・影響範囲・環境情報・再現動画）を反映の上、共有。</p>"
      }
    },
    {
      "id": "AAMkAGQA1bYAAQ==",
      "createdDateTime": "2025-10-24T00:25:12Z",
      "lastModifiedDateTime": "2025-10-24T00:25:12Z",
      "changeKey": "p3Uk3QeAAk1=",
      "categories": [ "QA", "Deadline" ],
      "originalStartTimeZone": "Asia/Tokyo",
      "originalEndTimeZone": "Asia/Tokyo",
      "iCalUId": "040000008200E00074C5B7101A82E00800000000D02E3B9F5C4FD801000000000000000010000000E4",
      "reminderMinutesBeforeStart": 30,
      "isReminderOn": true,
      "hasAttachments": false,
      "subject": "アクション期限: 自動テスト修正・動作確認（藤原）",
      "bodyPreview": "UI変更による失敗テストの修正と動作確認。期限：10/27。",
      "importance": "normal",
      "sensitivity": "normal",
      "isAllDay": false,
      "isCancelled": false,
      "isOrganizer": true,
      "responseRequested": false,
      "seriesMasterId": null,
      "showAs": "free",
      "type": "singleInstance",
      "webLink": "https://outlook.office.com/calendar/item/AAMkAGQA1bYAAQ==",
      "onlineMeetingUrl": null,
      "start": {
        "dateTime": "2025-10-27T10:00:00",
        "timeZone": "Asia/Tokyo"
      },
      "end": {
        "dateTime": "2025-10-27T10:30:00",
        "timeZone": "Asia/Tokyo"
      },
      "location": {
        "displayName": "リポジトリ（Selenium）/CI環境",
        "locationType": "default",
        "uniqueIdType": "unknown",
        "address": {}
      },
      "locations": [],
      "recurrence": null,
      "responseStatus": {
        "response": "organizer",
        "time": "2025-10-24T00:25:12Z"
      },
      "organizer": {
        "emailAddress": {
          "name": "藤原光",
          "address": "hikaru.fujiwara@contoso.com"
        }
      },
      "attendees": [
        {
          "type": "required",
          "status": { "response": "accepted", "time": "2025-10-24T00:27:41Z" },
          "emailAddress": { "name": "藤原光", "address": "hikaru.fujiwara@contoso.com" }
        }
      ],
      "body": {
        "contentType": "html",
        "content": "<p>XPath変更対応、ログイン画面修正、CI実行での安定化確認。</p>"
      }
    },
    {
      "id": "AAMkAGQA1bYAAZ==",
      "createdDateTime": "2025-10-24T00:28:44Z",
      "lastModifiedDateTime": "2025-10-24T00:28:44Z",
      "changeKey": "uQ2l6QeAAk2=",
      "categories": [ "QA", "Meeting" ],
      "originalStartTimeZone": "Asia/Tokyo",
      "originalEndTimeZone": "Asia/Tokyo",
      "iCalUId": "040000008200E00074C5B7101A82E00800000000D02E3B9F5C4FD801000000000000000010000000E5",
      "reminderMinutesBeforeStart": 15,
      "isReminderOn": true,
      "hasAttachments": false,
      "subject": "テスト・品質保証チーム  次回会議（準備会議）",
      "bodyPreview": "テスト項目書最終確認 / 自動テストスクリプト動作報告 / 不具合報告テンプレートレビュー。10/28 16:00-17:00（JST）。",
      "importance": "normal",
      "sensitivity": "normal",
      "isAllDay": false,
      "isCancelled": false,
      "isOrganizer": true,
      "responseRequested": true,
      "seriesMasterId": null,
      "showAs": "busy",
      "type": "singleInstance",
      "webLink": "https://outlook.office.com/calendar/item/AAMkAGQA1bYAAZ==",
      "onlineMeetingUrl": "https://teams.microsoft.com/l/meetup-join/19%3Ameeting_next_prep",
      "onlineMeeting": {
        "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3Ameeting_next_prep"
      },
      "start": {
        "dateTime": "2025-10-28T16:00:00",
        "timeZone": "Asia/Tokyo"
      },
      "end": {
        "dateTime": "2025-10-28T17:00:00",
        "timeZone": "Asia/Tokyo"
      },
      "location": {
        "displayName": "Microsoft Teams 会議",
        "locationType": "online",
        "uniqueIdType": "unknown",
        "address": {}
      },
      "locations": [
        {
          "displayName": "Microsoft Teams 会議",
          "locationType": "online",
          "uniqueIdType": "unknown",
          "address": {}
        }
      ],
      "recurrence": null,
      "responseStatus": {
        "response": "organizer",
        "time": "2025-10-24T00:28:44Z"
      },
      "organizer": {
        "emailAddress": {
          "name": "山本綾子",
          "address": "ayako.yamamoto@contoso.com"
        }
      },
      "attendees": [
        {
          "type": "required",
          "status": { "response": "accepted", "time": "2025-10-24T00:30:05Z" },
          "emailAddress": { "name": "藤原光", "address": "hikaru.fujiwara@contoso.com" }
        },
        {
          "type": "required",
          "status": { "response": "accepted", "time": "2025-10-24T00:30:33Z" },
          "emailAddress": { "name": "岡田奈々", "address": "nana.okada@contoso.com" }
        }
      ],
      "body": {
        "contentType": "html",
        "content": "<p>議題：<ul><li>テスト項目書最終確認</li><li>自動テストスクリプト動作報告</li><li>不具合報告テンプレートレビュー</li></ul></p>"
      }
    },
    {
      "id": "AAMkAGQA1bYAA7==",
      "createdDateTime": "2025-10-24T00:32:50Z",
      "lastModifiedDateTime": "2025-10-24T00:33:21Z",
      "changeKey": "w9cU6QeAAk3=",
      "categories": [ "QA", "Milestone" ],
      "originalStartTimeZone": "Asia/Tokyo",
      "originalEndTimeZone": "Asia/Tokyo",
      "iCalUId": "040000008200E00074C5B7101A82E00800000000D02E3B9F5C4FD801000000000000000010000000E6",
      "reminderMinutesBeforeStart": 1440,
      "isReminderOn": true,
      "hasAttachments": false,
      "subject": "統合テスト期間（第1週～第2週）",
      "bodyPreview": "11/4（月）〜 11/15（金） 統合テスト実施期間。機能別からシナリオテストへ段階移行、日次報告を #qa_daily へ投稿。",
      "importance": "high",
      "sensitivity": "normal",
      "isAllDay": true,
      "isCancelled": false,
      "isOrganizer": true,
      "responseRequested": false,
      "seriesMasterId": null,
      "showAs": "busy",
      "type": "singleInstance",
      "webLink": "https://outlook.office.com/calendar/item/AAMkAGQA1bYAA7==",
      "onlineMeetingUrl": null,
      "start": {
        "dateTime": "2025-11-04",
        "timeZone": "Asia/Tokyo"
      },
      "end": {
        "dateTime": "2025-11-16",
        "timeZone": "Asia/Tokyo"
      },
      "location": {
        "displayName": "各自環境 / テスト環境（統合）",
        "locationType": "default",
        "uniqueIdType": "unknown",
        "address": {}
      },
      "locations": [],
      "recurrence": null,
      "responseStatus": {
        "response": "organizer",
        "time": "2025-10-24T00:32:50Z"
      },
      "organizer": {
        "emailAddress": {
          "name": "山本綾子",
          "address": "ayako.yamamoto@contoso.com"
        }
      },
      "attendees": [
        {
          "type": "resource",
          "status": { "response": "none", "time": "0001-01-01T00:00:00Z" },
          "emailAddress": { "name": "QAテスト環境", "address": "qa-lab@contoso.com" }
        }
      ],
      "body": {
        "contentType": "html",
        "content": "<p>統合テスト実施期間：<b>2025/11/4〜2025/11/15</b>（終日）。<br/>バグ報告〜修正〜再確認のサイクル短縮のため、日次進捗を Teams #qa_daily チャンネルへ投稿。</p>"
      }
    },
    {
      "id": "AAMkAGQA1bYABG==",
      "createdDateTime": "2025-10-24T00:35:12Z",
      "lastModifiedDateTime": "2025-10-24T00:36:58Z",
      "changeKey": "x1tZ8QeAAk4=",
      "categories": [ "QA", "Reminder" ],
      "originalStartTimeZone": "Asia/Tokyo",
      "originalEndTimeZone": "Asia/Tokyo",
      "iCalUId": "040000008200E00074C5B7101A82E00800000000D02E3B9F5C4FD801000000000000000010000000E7",
      "reminderMinutesBeforeStart": 10,
      "isReminderOn": true,
      "hasAttachments": false,
      "subject": "QA 日次進捗報告（#qa_daily）",
      "bodyPreview": "統合テスト期間中の毎日 17:30（JST）に日次報告を投稿。",
      "importance": "normal",
      "sensitivity": "normal",
      "isAllDay": false,
      "isCancelled": false,
      "isOrganizer": true,
      "responseRequested": false,
      "seriesMasterId": "AAMkAGQA1bYABG==",
      "showAs": "free",
      "type": "seriesMaster",
      "webLink": "https://outlook.office.com/calendar/item/AAMkAGQA1bYABG==",
      "onlineMeetingUrl": null,
      "start": {
        "dateTime": "2025-11-04T17:30:00",
        "timeZone": "Asia/Tokyo"
      },
      "end": {
        "dateTime": "2025-11-04T17:40:00",
        "timeZone": "Asia/Tokyo"
      },
      "location": {
        "displayName": "Teams チャンネル #qa_daily",
        "locationType": "default",
        "uniqueIdType": "unknown",
        "address": {}
      },
      "locations": [],
      "recurrence": {
        "pattern": {
          "type": "daily",
          "interval": 1,
          "daysOfWeek": [],
          "firstDayOfWeek": "sunday"
        },
        "range": {
          "type": "endDate",
          "startDate": "2025-11-04",
          "endDate": "2025-11-15",
          "recurrenceTimeZone": "Asia/Tokyo",
          "numberOfOccurrences": 0
        }
      },
      "responseStatus": {
        "response": "organizer",
        "time": "2025-10-24T00:35:12Z"
      },
      "organizer": {
        "emailAddress": {
          "name": "山本綾子",
          "address": "ayako.yamamoto@contoso.com"
        }
      },
      "attendees": [],
      "body": {
        "contentType": "html",
        "content": "<p>統合テスト期間中の毎日 <b>17:30（JST）</b> に日次進捗報告を Teams #qa_daily へ投稿するリマインダー。</p>"
      }
    },
    {
      "id": "AAMkAGQA1bYABQ==",
      "createdDateTime": "2025-10-24T00:38:10Z",
      "lastModifiedDateTime": "2025-10-24T00:38:10Z",
      "changeKey": "z8Er9QeAAk5=",
      "categories": [ "QA", "Deadline" ],
      "originalStartTimeZone": "Asia/Tokyo",
      "originalEndTimeZone": "Asia/Tokyo",
      "iCalUId": "040000008200E00074C5B7101A82E00800000000D02E3B9F5C4FD801000000000000000010000000E8",
      "reminderMinutesBeforeStart": 60,
      "isReminderOn": true,
      "hasAttachments": false,
      "subject": "アクション期限: テスト実施スケジュール最終確定（山本）",
      "bodyPreview": "スケジュール最終版の確定（担当：山本、期限：10/28）。",
      "importance": "normal",
      "sensitivity": "normal",
      "isAllDay": false,
      "isCancelled": false,
      "isOrganizer": true,
      "responseRequested": false,
      "seriesMasterId": null,
      "showAs": "free",
      "type": "singleInstance",
      "webLink": "https://outlook.office.com/calendar/item/AAMkAGQA1bYABQ==",
      "onlineMeetingUrl": null,
      "start": {
        "dateTime": "2025-10-28T10:00:00",
        "timeZone": "Asia/Tokyo"
      },
      "end": {
        "dateTime": "2025-10-28T10:15:00",
        "timeZone": "Asia/Tokyo"
      },
      "location": {
        "displayName": "スケジュール管理表（SharePoint）",
        "locationType": "default",
        "uniqueIdType": "unknown",
        "address": {}
      },
      "locations": [],
      "recurrence": null,
      "responseStatus": {
        "response": "organizer",
        "time": "2025-10-24T00:38:10Z"
      },
      "organizer": {
        "emailAddress": {
          "name": "山本綾子",
          "address": "ayako.yamamoto@contoso.com"
        }
      },
      "attendees": [
        {
          "type": "required",
          "status": { "response": "accepted", "time": "2025-10-24T00:39:21Z" },
          "emailAddress": { "name": "山本綾子", "address": "ayako.yamamoto@contoso.com" }
        }
      ],
      "body": {
        "contentType": "html",
        "content": "<p>11/4〜11/15 の統合テスト期間に合わせ、スケジュール最終版を確定。</p>"
      }
    }
  ]
}

```
## outlookチーム３

```text
予定一覧（Asia/Tokyo）

【期限】UI側 APIモック更新（/sales/list: items→data）

日時：2025/10/26（日）終日

担当（主催）：石川怜奈

場所：リポジトリ（frontend/mock）

概要：レスポンス構造変更（items→data）をモックに反映し、UI連携を確認。

【期限】API共通エラーフォーマット仕様（draft）

日時：2025/10/27（月）終日

担当（主催）：佐藤健

場所：設計ドキュメント（SharePoint）

概要：標準エラーフォーマット案を作成・共有（code/message/trace_id/detail など）。

【期限】Slack通知連携（GitHub Actions + Webhook）

日時：2025/10/28（火）終日

担当（主催）：河合亮

場所：DevOps 設定リポジトリ

概要：成功率・エラー件数を含む通知テンプレートを整備。Webhookは devops-config/slack.env。

【期限】結合テスト結果報告・網羅率確認

日時：2025/10/28（火）終日（※15:30〜17:00に報告準備想定）

担当（主催）：中村優

参加者：伊藤萌（必須）

場所：Teams／#dev_progress

概要：販売API×会計APIの結合テスト総括、失敗2件の是正結果、カバレッジ（--cov-report=xml）提示。

【期限】APIバージョニングポリシー策定（v1.5→v2.0 互換基準）

日時：2025/10/29（水）終日

担当（主催）：高橋純

参加者：佐藤健（必須）

場所：設計ドキュメント（SharePoint）

概要：互換性基準、破壊的変更の扱い、移行ガイドの雛形を定義。

【期限】APIゲートウェイ詳細設計まとめ（API GW + Lambda + Cognito）

日時：2025/10/29（水）終日

担当（主催）：高橋純

参加者：河合亮（必須）

場所：設計レビュー用ノート（OneNote）

概要：認証・認可統合、ステージ別変数はSSM、将来のエッジキャッシュ前提のルーティング/スロットリング設計。

会議：設計・開発チーム 定例（統合テスト結果／API方針／デプロイ手順）

日時：2025/10/30（木）14:00〜15:30

主催：伊藤萌

参加者：高橋純（承諾）、佐藤健（仮承諾）、中村優（任意）、石川怜奈（任意）、河合亮（任意）

開催方法：Microsoft Teams（参加URLあり）

議題：

統合テスト結果レビュー

APIバージョニング方針（互換性・移行）最終確認

デプロイ手順書レビュー
```
```json
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#me/calendarView",
  "generatedFrom": {
    "source": "Teams messages (Graph-like JSON provided by user)",
    "teamId": "devteam123",
    "channels": [
      "19:general@thread.tacv2",
      "19:notice@thread.tacv2",
      "19:tech-share@thread.tacv2"
    ],
    "timezone": "Asia/Tokyo",
    "extractedAt": "2025-10-24T00:00:00Z"
  },
  "value": [
    {
      "id": "ev-20251026-ui-mock-allDay",
      "createdDateTime": "2025-10-23T06:00:00Z",
      "lastModifiedDateTime": "2025-10-23T06:00:00Z",
      "changeKey": "ck-1",
      "categories": ["Deadline", "Frontend"],
      "subject": "【期限】UI側 APIモック更新（/sales/list: items→data）",
      "bodyPreview": "担当: 石川怜奈。モック更新と連携確認を完了する。",
      "importance": "normal",
      "isAllDay": true,
      "isCancelled": false,
      "isOrganizer": true,
      "showAs": "free",
      "type": "singleInstance",
      "start": { "dateTime": "2025-10-26T00:00:00", "timeZone": "Asia/Tokyo" },
      "end":   { "dateTime": "2025-10-27T00:00:00", "timeZone": "Asia/Tokyo" },
      "location": { "displayName": "リポジトリ: frontend/mock" },
      "reminderMinutesBeforeStart": 540,
      "isReminderOn": true,
      "organizer": { "emailAddress": { "name": "石川怜奈", "address": "rena.ishikawa@contoso.com" } },
      "attendees": [],
      "body": {
        "contentType": "html",
        "content": "<p>React UI プロトタイプ連携確認に合わせて、/sales/list のレスポンス構造（items→data）変更をモックへ反映。</p>"
      },
      "webLink": "https://outlook.office.com/calendar/item/ev-20251026-ui-mock-allDay"
    },
    {
      "id": "ev-20251027-error-format-allDay",
      "createdDateTime": "2025-10-23T06:01:00Z",
      "lastModifiedDateTime": "2025-10-23T06:01:00Z",
      "changeKey": "ck-2",
      "categories": ["Deadline", "API"],
      "subject": "【期限】API共通エラーフォーマット仕様（draft）",
      "bodyPreview": "担当: 佐藤健。エラーフォーマット標準案を作成し共有。",
      "importance": "normal",
      "isAllDay": true,
      "isOrganizer": true,
      "showAs": "free",
      "type": "singleInstance",
      "start": { "dateTime": "2025-10-27T00:00:00", "timeZone": "Asia/Tokyo" },
      "end":   { "dateTime": "2025-10-28T00:00:00", "timeZone": "Asia/Tokyo" },
      "location": { "displayName": "設計ドキュメント（SharePoint）" },
      "reminderMinutesBeforeStart": 540,
      "isReminderOn": true,
      "organizer": { "emailAddress": { "name": "佐藤健", "address": "ken.sato@contoso.com" } },
      "attendees": [],
      "body": {
        "contentType": "html",
        "content": "<p>例: <code>{\"error\":{\"code\":\"E001\",\"message\":\"Invalid parameter\",\"trace_id\":\"...\",\"detail\":\"...\"}}</code></p>"
      },
      "webLink": "https://outlook.office.com/calendar/item/ev-20251027-error-format-allDay"
    },
    {
      "id": "ev-20251028-slack-integration-allDay",
      "createdDateTime": "2025-10-23T06:02:00Z",
      "lastModifiedDateTime": "2025-10-23T06:02:00Z",
      "changeKey": "ck-3",
      "categories": ["Deadline", "DevOps"],
      "subject": "【期限】Slack通知連携（GitHub Actions + Webhook）",
      "bodyPreview": "担当: 河合亮。成功率/エラー件数を含む通知テンプレート。",
      "importance": "normal",
      "isAllDay": true,
      "isOrganizer": true,
      "showAs": "free",
      "type": "singleInstance",
      "start": { "dateTime": "2025-10-28T00:00:00", "timeZone": "Asia/Tokyo" },
      "end":   { "dateTime": "2025-10-29T00:00:00", "timeZone": "Asia/Tokyo" },
      "location": { "displayName": "DevOps 設定リポジトリ" },
      "reminderMinutesBeforeStart": 540,
      "isReminderOn": true,
      "organizer": { "emailAddress": { "name": "河合亮", "address": "ryo.kawai@contoso.com" } },
      "attendees": [],
      "body": {
        "contentType": "html",
        "content": "<p>Webhook: <code>devops-config/slack.env</code><br/>通知サンプル：✅ 統合テスト完了／成功率・エラー数・担当者を含む。</p>"
      },
      "webLink": "https://outlook.office.com/calendar/item/ev-20251028-slack-integration-allDay"
    },
    {
      "id": "ev-20251028-ct-report-allDay",
      "createdDateTime": "2025-10-23T06:03:00Z",
      "lastModifiedDateTime": "2025-10-23T06:03:00Z",
      "changeKey": "ck-4",
      "categories": ["Deadline", "Testing"],
      "subject": "【期限】結合テスト結果報告・網羅率確認",
      "bodyPreview": "担当: 中村優・伊藤萌。pytestのカバレッジを含めて共有。",
      "importance": "normal",
      "isAllDay": true,
      "isOrganizer": true,
      "showAs": "free",
      "type": "singleInstance",
      "start": { "dateTime": "2025-10-28T00:00:00", "timeZone": "Asia/Tokyo" },
      "end":   { "dateTime": "2025-10-29T00:00:00", "timeZone": "Asia/Tokyo" },
      "location": { "displayName": "Teams / #dev_progress" },
      "reminderMinutesBeforeStart": 540,
      "isReminderOn": true,
      "organizer": { "emailAddress": { "name": "中村優", "address": "yu.nakamura@contoso.com" } },
      "attendees": [
        {
          "type": "required",
          "status": { "response": "none", "time": "0001-01-01T00:00:00Z" },
          "emailAddress": { "name": "伊藤萌", "address": "moe.ito@contoso.com" }
        }
      ],
      "body": {
        "contentType": "html",
        "content": "<p>販売API×会計APIの結合テスト総括。失敗2件の原因（モック/期待値不一致）と是正結果、<code>--cov-report=xml</code> を添付予定。</p>"
      },
      "webLink": "https://outlook.office.com/calendar/item/ev-20251028-ct-report-allDay"
    },
    {
      "id": "ev-20251029-versioning-allDay",
      "createdDateTime": "2025-10-23T06:04:00Z",
      "lastModifiedDateTime": "2025-10-23T06:04:00Z",
      "changeKey": "ck-5",
      "categories": ["Deadline", "Architecture"],
      "subject": "【期限】APIバージョニングポリシー策定（v1.5→v2.0 互換基準）",
      "bodyPreview": "担当: 高橋純・佐藤健。破壊的変更の扱い・移行手順を定義。",
      "importance": "normal",
      "isAllDay": true,
      "isOrganizer": true,
      "showAs": "free",
      "type": "singleInstance",
      "start": { "dateTime": "2025-10-29T00:00:00", "timeZone": "Asia/Tokyo" },
      "end":   { "dateTime": "2025-10-30T00:00:00", "timeZone": "Asia/Tokyo" },
      "location": { "displayName": "設計ドキュメント（SharePoint）" },
      "reminderMinutesBeforeStart": 540,
      "isReminderOn": true,
      "organizer": { "emailAddress": { "name": "高橋純", "address": "jun.takahashi@contoso.com" } },
      "attendees": [
        {
          "type": "required",
          "status": { "response": "none", "time": "0001-01-01T00:00:00Z" },
          "emailAddress": { "name": "佐藤健", "address": "ken.sato@contoso.com" }
        }
      ],
      "body": {
        "contentType": "html",
        "content": "<p>セマンティックバージョニング準拠。非互換変更の周知・移行ガイドの雛形作成。</p>"
      },
      "webLink": "https://outlook.office.com/calendar/item/ev-20251029-versioning-allDay"
    },
    {
      "id": "ev-20251029-apigw-allDay",
      "createdDateTime": "2025-10-23T06:05:00Z",
      "lastModifiedDateTime": "2025-10-23T06:05:00Z",
      "changeKey": "ck-6",
      "categories": ["Deadline", "Architecture", "DevOps"],
      "subject": "【期限】APIゲートウェイ詳細設計まとめ（API GW + Lambda + Cognito）",
      "bodyPreview": "担当: 高橋純・河合亮。認証/認可・SSM・スケーラビリティ設計。",
      "importance": "normal",
      "isAllDay": true,
      "isOrganizer": true,
      "showAs": "free",
      "type": "singleInstance",
      "start": { "dateTime": "2025-10-29T00:00:00", "timeZone": "Asia/Tokyo" },
      "end":   { "dateTime": "2025-10-30T00:00:00", "timeZone": "Asia/Tokyo" },
      "location": { "displayName": "設計レビュー用ノート（OneNote）" },
      "reminderMinutesBeforeStart": 540,
      "isReminderOn": true,
      "organizer": { "emailAddress": { "name": "高橋純", "address": "jun.takahashi@contoso.com" } },
      "attendees": [
        {
          "type": "required",
          "status": { "response": "none", "time": "0001-01-01T00:00:00Z" },
          "emailAddress": { "name": "河合亮", "address": "ryo.kawai@contoso.com" }
        }
      ],
      "body": {
        "contentType": "html",
        "content": "<p>認証・認可の統合、ステージ別変数はSSM管理。将来的なエッジキャッシュ前提のルーティング/スロットリング設計を含む。</p>"
      },
      "webLink": "https://outlook.office.com/calendar/item/ev-20251029-apigw-allDay"
    },
    {
      "id": "ev-20251030-regular-meeting",
      "createdDateTime": "2025-10-23T06:06:00Z",
      "lastModifiedDateTime": "2025-10-23T06:06:00Z",
      "changeKey": "ck-7",
      "categories": ["Meeting", "Project"],
      "subject": "設計・開発チーム 定例（統合テスト結果／API方針／デプロイ手順）",
      "bodyPreview": "10/30（木）14:00–15:30（JST）Teams会議。",
      "importance": "normal",
      "isAllDay": false,
      "isCancelled": false,
      "isOrganizer": true,
      "responseRequested": true,
      "showAs": "busy",
      "type": "singleInstance",
      "start": { "dateTime": "2025-10-30T14:00:00", "timeZone": "Asia/Tokyo" },
      "end":   { "dateTime": "2025-10-30T15:30:00", "timeZone": "Asia/Tokyo" },
      "location": { "displayName": "Microsoft Teams 会議", "locationType": "online" },
      "onlineMeetingUrl": "https://teams.microsoft.com/l/meetup-join/19%3Ameeting_link",
      "onlineMeeting": { "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3Ameeting_link" },
      "reminderMinutesBeforeStart": 15,
      "isReminderOn": true,
      "organizer": { "emailAddress": { "name": "伊藤萌", "address": "moe.ito@contoso.com" } },
      "attendees": [
        {
          "type": "required",
          "status": { "response": "accepted", "time": "2025-10-23T07:01:00Z" },
          "emailAddress": { "name": "高橋純", "address": "jun.takahashi@contoso.com" }
        },
        {
          "type": "required",
          "status": { "response": "tentativelyAccepted", "time": "2025-10-23T07:00:00Z" },
          "emailAddress": { "name": "佐藤健", "address": "ken.sato@contoso.com" }
        },
        {
          "type": "optional",
          "status": { "response": "none", "time": "0001-01-01T00:00:00Z" },
          "emailAddress": { "name": "中村優", "address": "yu.nakamura@contoso.com" }
        },
        {
          "type": "optional",
          "status": { "response": "none", "time": "0001-01-01T00:00:00Z" },
          "emailAddress": { "name": "石川怜奈", "address": "rena.ishikawa@contoso.com" }
        },
        {
          "type": "optional",
          "status": { "response": "none", "time": "0001-01-01T00:00:00Z" },
          "emailAddress": { "name": "河合亮", "address": "ryo.kawai@contoso.com" }
        }
      ],
      "body": {
        "contentType": "html",
        "content": "<p>議題：</p><ul><li>統合テスト結果レビュー</li><li>APIバージョニング方針（互換性基準・移行）最終確認</li><li>デプロイ手順書レビュー</li></ul>"
      },
      "webLink": "https://outlook.office.com/calendar/item/ev-20251030-regular-meeting"
    }
  ]
}
```

```

# 議事録

## 議事録例チーム１
```text
📝 議事録

会議名：設計・開発チーム API設計・実装タスク 定例会議
日時：2025年10月23日（木） 14:00〜15:30
場所：Teamsオンライン会議
出席者：

佐藤健（開発リーダー）

中村優（バックエンドエンジニア）

石川怜奈（フロントエンドエンジニア）

高橋純（テクニカルリード）

伊藤萌（テスター）

河合亮（DevOpsエンジニア）

1. 会議目的

販売管理機能を中心としたREST APIの設計・実装進捗を確認し、今後の統合テスト・デプロイ手順の整備方針を決定する。

2. 議題および内容
議題①：在庫APIレビュー結果共有（佐藤）

佐藤より、在庫APIのレビューとマージが完了した旨報告。

エラーハンドリング仕様を共通化するためのルールを次回までに整理予定。

外部システム連携部分のトークン認証方式については高橋の提案を採用。

決定事項：

API共通エラーフォーマットをチーム標準として定義（10/27までに佐藤作成）。

議題②：会計APIテスト進捗（中村）

中村より、会計APIのテストコード追加が完了した旨報告。

一部モックデータの不整合により自動テストが失敗していたが修正済み。

販売APIとの結合テストを今週中に実施予定。

決定事項：

結合テスト結果を次回会議で報告。

中村・伊藤でテストシナリオの網羅率を再確認。

議題③：フロントエンドとの連携確認（石川）

石川より、ReactベースのUIプロトタイプを作成し、販売管理画面のAPI接続確認が完了した旨報告。

一部エンドポイントでレスポンス構造が変更されたため、バージョン管理ルールの明文化が必要との指摘あり。

決定事項：

バージョニングポリシーを次回までに高橋・佐藤で策定。

石川はUI側のAPIモック更新を10/26までに完了。

議題④：APIゲートウェイ設計方針（高橋）

高橋より、APIゲートウェイの設計指針レビュー結果を共有。

認証・認可を統合的に扱う仕組みを採用予定。

今後のスケーラビリティ対応を見据え、AWS API Gateway + Lambda連携も検討。

決定事項：

詳細設計を10/29までにまとめ、レビューを実施（高橋・河合）。

議題⑤：統合テストとCI/CD整備（伊藤・河合）

伊藤より、販売APIの統合テスト実施結果を共有。テストケース80件中78件成功。

河合より、CI/CDパイプラインの自動デプロイ設定を本番相当環境に適用済みと報告。

残課題として、テスト実行トリガーの自動化とSlack通知連携を検討中。

決定事項：

河合がSlack通知連携を構築（10/28まで）。

伊藤が残り2件のテスト不具合を修正。

3. アクションアイテム
No	内容	担当	期限
1	API共通エラーフォーマットの定義	佐藤	10/27
2	結合テスト結果報告・網羅率確認	中村・伊藤	10/28
3	バージョニングポリシー策定	高橋・佐藤	10/29
4	APIゲートウェイ詳細設計まとめ	高橋・河合	10/29
5	UI側APIモック更新	石川	10/26
6	Slack通知連携構築	河合	10/28
4. 次回会議

日時：2025年10月30日（木） 14:00〜15:30
議題予定：

統合テスト結果レビュー

APIバージョニング方針の最終確認

デプロイ手順書のレビュー

作成者：伊藤萌（テスター）
確認者：佐藤健（開発リーダー）
```
## 議事録例チーム２
```text
📝 議事録

会議名：テスト・品質保証チーム 統合テスト・リリース前検証タスク 準備会議
日時：2025年10月23日（木） 16:00〜17:00
場所：Teamsオンライン会議
出席者：

山本綾子（QAリーダー）

藤原光（テストエンジニア）

岡田奈々（ドキュメント担当）

1. 会議目的

統合テストおよび品質保証プロセスの準備状況を確認し、テスト計画・環境構築・報告体制の整備方針を決定する。

2. 議題および内容
議題①：テスト項目書レビュー状況（山本）

山本より、全機能を対象としたテスト項目書のレビューが完了した旨報告。

特に販売・在庫・会計連携部分のテスト観点を重点項目に設定。

他チームのAPI仕様変更点が一部未反映のため、更新を要する。

決定事項：

設計・開発チームから最新API一覧を受領後、10/25までにテスト項目書を更新。

議題②：自動テストスクリプト整備状況（藤原）

藤原より、Python + Seleniumベースの自動テストスクリプトを整備中と報告。

UI変更により一部スクリプトがエラーを出しているため、要修正。

並行実行環境（CI/CD上の自動化）についてはDevOpsチームと調整中。

決定事項：

スクリプト修正と実行確認を10/27までに完了（藤原）。

CI/CD連携は河合（DevOps）と週内にミーティング設定。

議題③：不具合報告テンプレート整備（岡田）

岡田より、不具合報告書テンプレートの初版を作成済みと報告。

山本から、再現手順・環境情報・影響範囲の明示を必須項目に追加するよう指示。

次回までにフォーマットを最終化し、テスト開始前に全員へ展開予定。

決定事項：

岡田が修正版テンプレートを10/26までに共有フォルダへアップロード。

議題④：統合テスト環境および実施スケジュール

山本より、統合テスト実施時期を11月第1週に設定する案を提示。

各APIの安定版が揃い次第、機能別テストからシナリオテストへ移行予定。

バグ報告から修正・再確認までのサイクルを迅速化するため、日次報告体制を導入。

決定事項：

テスト実施期間：11/4〜11/15

日次進捗報告をTeamsチャンネル「#qa_daily」に投稿する。

3. アクションアイテム
No	内容	担当	期限
1	最新API一覧を反映したテスト項目書更新	山本	10/25
2	自動テストスクリプト修正・動作確認	藤原	10/27
3	不具合報告テンプレート最終化・共有	岡田	10/26
4	CI/CD連携調整ミーティング設定	藤原	10/25
5	テスト実施スケジュール最終確定	山本	10/28
4. 次回会議

日時：2025年10月28日（火） 16:00〜17:00
議題予定：

テスト項目書最終確認

自動テストスクリプト動作報告

不具合報告テンプレートレビュー

作成者：岡田奈々（ドキュメント担当）
確認者：山本綾子（QAリーダー）
```
## 議事録例チーム3
```text
📝 議事録

会議名：設計・開発チーム API設計・実装タスク 定例会議
日時：2025年10月23日（木） 14:00〜15:30
場所：Teamsオンライン会議
出席者：

佐藤健（開発リーダー）

中村優（バックエンドエンジニア）

石川怜奈（フロントエンドエンジニア）

高橋純（テクニカルリード）

伊藤萌（テスター）

河合亮（DevOpsエンジニア）

1. 会議目的

販売管理機能を中心としたREST APIの設計・実装進捗を確認し、今後の統合テスト・デプロイ手順の整備方針を決定する。

2. 議題および内容
議題①：在庫APIレビュー結果共有（佐藤）

佐藤より、在庫APIのレビューとマージが完了した旨報告。

エラーハンドリング仕様を共通化するためのルールを次回までに整理予定。

外部システム連携部分のトークン認証方式については高橋の提案を採用。

決定事項：

API共通エラーフォーマットをチーム標準として定義（10/27までに佐藤作成）。

議題②：会計APIテスト進捗（中村）

中村より、会計APIのテストコード追加が完了した旨報告。

一部モックデータの不整合により自動テストが失敗していたが修正済み。

販売APIとの結合テストを今週中に実施予定。

決定事項：

結合テスト結果を次回会議で報告。

中村・伊藤でテストシナリオの網羅率を再確認。

議題③：フロントエンドとの連携確認（石川）

石川より、ReactベースのUIプロトタイプを作成し、販売管理画面のAPI接続確認が完了した旨報告。

一部エンドポイントでレスポンス構造が変更されたため、バージョン管理ルールの明文化が必要との指摘あり。

決定事項：

バージョニングポリシーを次回までに高橋・佐藤で策定。

石川はUI側のAPIモック更新を10/26までに完了。

議題④：APIゲートウェイ設計方針（高橋）

高橋より、APIゲートウェイの設計指針レビュー結果を共有。

認証・認可を統合的に扱う仕組みを採用予定。

今後のスケーラビリティ対応を見据え、AWS API Gateway + Lambda連携も検討。

決定事項：

詳細設計を10/29までにまとめ、レビューを実施（高橋・河合）。

議題⑤：統合テストとCI/CD整備（伊藤・河合）

伊藤より、販売APIの統合テスト実施結果を共有。テストケース80件中78件成功。

河合より、CI/CDパイプラインの自動デプロイ設定を本番相当環境に適用済みと報告。

残課題として、テスト実行トリガーの自動化とSlack通知連携を検討中。

決定事項：

河合がSlack通知連携を構築（10/28まで）。

伊藤が残り2件のテスト不具合を修正。

3. アクションアイテム
No	内容	担当	期限
1	API共通エラーフォーマットの定義	佐藤	10/27
2	結合テスト結果報告・網羅率確認	中村・伊藤	10/28
3	バージョニングポリシー策定	高橋・佐藤	10/29
4	APIゲートウェイ詳細設計まとめ	高橋・河合	10/29
5	UI側APIモック更新	石川	10/26
6	Slack通知連携構築	河合	10/28
4. 次回会議

日時：2025年10月30日（木） 14:00〜15:30
議題予定：

統合テスト結果レビュー

APIバージョニング方針の最終確認

デプロイ手順書のレビュー

作成者：伊藤萌（テスター）
確認者：佐藤健（開発リーダー）
```
## 議事録例チーム4
```text
議事録
会議名	システム運用チーム 障害対応フロー改善会議
作成日	2025年10月24日
■ 概要
	
日時	2025年10月24日（金） 15:00～16:00
場所	会議室B / Teams併用
出席者	加藤誠、田辺真理、井上直樹、吉田圭（計4名）
目的	障害発生時の初動対応および報告フローの見直しを行い、対応時間短縮と再発防止体制を確立する。
■ 議事
【議題】

現行障害対応フローの問題点について

自動アラート通知システムの導入検討

定期報告書フォーマットの改訂

夜間対応体制の見直し

【討議内容】

(1) 現行障害対応フローの問題点について（加藤）

現行フローでは障害発生から報告まで平均20分を要している。

一次対応担当者が特定のチャネル（Teams）での報告を失念するケースが複数発生。

対応手順書の最新化が不十分であることが原因の一つ。
→ 対応：手順書を最新版に更新し、11月中に全体周知を実施。

(2) 自動アラート通知システムの導入検討（井上）

監視ツール（Zabbix）とSlackのWebhook連携を試験的に導入。

テスト環境ではアラート遅延を平均70％削減。

本番導入に向けてサーバー負荷検証を実施予定。
→ 対応：11/5までに検証結果をまとめて次回報告（井上）。

(3) 定期報告書フォーマットの改訂（田辺）

現行報告書がExcelベースで集計に時間がかかる。

Googleスプレッドシートへの移行提案を実施。

自動集計マクロを組み込み、提出作業を15分以内に短縮可能。
→ 対応：改訂版を11/1に運用チームへ配布。

(4) 夜間対応体制の見直し（吉田）

現状は1名体制での夜間待機だが、障害発生時の負担が大きい。

当面は22:00〜翌2:00の間のみ2名体制に移行。

コスト試算の上、常時2名体制への移行は来期に検討。

【未解決・持ち越し事項】

自動アラートシステムの本番負荷検証（井上）

夜間2名体制に伴うコスト試算（吉田）

■ 次回の予定
	
日時	2025年11月6日（木） 15:00～16:00
場所	会議室B / Teams併用
議題予定	自動アラート導入報告／夜間対応体制コスト試算結果／フロー改訂版確認
```
## 議事録チーム４別日
```text
議事録
会議名	システム運用チーム クラウド運用コスト最適化検討会
作成日	2025年10月30日
■ 概要
	
日時	2025年10月30日（木） 14:00～15:00
場所	会議室B / Teams併用
出席者	加藤誠、田辺真理、井上直樹、吉田圭（計4名）
目的	クラウド利用料の増加に伴い、コスト最適化策を検討し、次期運用予算に反映する。
■ 議事
【議題】

現在のクラウドコストの内訳分析

不要リソース削減計画の立案

予約インスタンス・Savings Plan導入の可否検討

コスト可視化ダッシュボードの設計

【討議内容】

(1) クラウドコスト内訳分析（田辺）

9月度クラウド請求額は約430万円（前月比＋12％）。

開発環境のEC2・EBSが全体の54％を占める。

夜間・休日も常時稼働しているリソースが複数存在。
→ 11月以降は夜間自動停止ルールの適用を優先実施。

(2) 不要リソース削減計画（井上）

使用率が10％未満の検証用インスタンスを一括リスト化。

24台のうち15台を停止候補として選定。

ストレージスナップショットの世代管理ルールを導入予定。
→ 11/5までに停止対象を最終決定。

(3) 予約インスタンス／Savings Plan導入（吉田）

長期稼働リソースを対象にSavings Planを試算中。

年間コストを最大18％削減見込み。

決裁プロセス上、来月上旬に承認依頼を提出予定。
→ 来週、経営会議用の簡易試算資料を作成（吉田）。

(4) コスト可視化ダッシュボード設計（加藤）

Power BIを用いたクラウドコスト可視化を検討。

各サービス・部門単位で利用状況を即時参照可能にする構成を提案。

初期版を11月中に試作し、月次報告会でデモ予定。

【未解決・持ち越し事項】

Savings Plan導入の最終試算および承認申請準備（吉田）

ダッシュボード試作環境の構築（加藤・井上）

■ 次回の予定
	
日時	2025年11月7日（金） 14:00～15:00
場所	会議室B / Teams併用
議題予定	コスト削減効果試算報告／Savings Plan申請進捗／ダッシュボード試作レビュー
```
## 議事録チーム４別日２
```text
システム運用チーム システム監視高度化計画ミーティング 議事録

作成日： 2025年11月5日
担当者： 加藤誠（運用管理部）

1. 会議概要

日時： 2025年11月5日（水） 14:00～15:30

場所： 会議室B / Teams併用

出席者： 加藤誠、田辺真理、井上直樹、吉田圭（計4名）

目的： システム監視業務の精度向上と運用負荷軽減を目的に、AI分析・自動化ツール導入の方針を検討する。

2. 議事内容

【議題】

現行監視体制の課題共有

AIベース異常検知ツールの導入検討

通知閾値設定の最適化

監視担当者の業務負荷削減施策

（1）現行監視体制の課題（加藤）

現行Zabbixベースの監視では誤検知（false positive）が多く、月平均15件の無駄なアラートが発生。

通知ルールが細分化されておらず、夜間の一次対応が属人化している。

統一的なアラート基準の再設計が必要。
→ 対応：運用ドキュメント更新案を次回提示（加藤）。

（2）AIベース異常検知ツール導入検討（井上）

Datadog AIOpsとNew Relic Lookoutを比較検証。

Datadogの方が既存インフラ（AWS, Azure）との親和性が高く、導入コストも約15％低い。

まずは開発環境にて2週間のPoCを実施予定。
→ PoC結果を11/20の会議で共有（井上）。

（3）通知閾値設定の最適化（田辺）

現行設定ではCPU使用率80％超で即アラートを発報しており、短期的スパイクも拾ってしまう。

過去3か月の稼働データをもとに「5分間平均」で判定する方式に変更提案。

メモリ使用率・ディスクI/Oも同基準で調整予定。
→ 11/10までに試験環境へ反映。

（4）業務負荷軽減施策（吉田）

ナイトシフト担当の対応工数を分析した結果、平均週12時間の残業が発生している。

Slack通知をOpsgenieへ統合し、優先度別のエスカレーションルールを導入予定。

翌月から夜間対応の担当制をローテーション方式へ変更。
→ 新体制を12月度より運用開始予定。

3. 決定事項

AI異常検知ツール（Datadog AIOps）のPoCを11/6より実施（井上）

通知閾値を「5分平均判定」に変更し、11/10までに反映（田辺）

夜間対応ローテーションを12月より導入（吉田）

統一アラート設計書を次回会議でレビュー（加藤）

4. 未解決・持ち越し事項

PoC検証結果の評価および導入判断（井上）

アラート統合ルールの承認（全員）

5. 次回の予定

日時： 2025年11月20日（木） 14:00～15:30

場所： 会議室B / Teams併用

議題予定：

PoC検証結果報告

通知閾値最適化の効果検証

アラート統合ルール最終承認
```
## 議事録全体会議チーム横断新プロジェクト
```text
📝 次世代販売管理システム開発プロジェクト 全体会議 議事録

会議名：プロジェクト全体会議（PJ間連携強化ミーティング）
日時：2025年10月23日（木） 15:00〜16:30
場所：Teamsオンライン会議
作成者：岡田奈々（テスト・品質保証チーム）

1. 会議目的

各チーム（要件定義・設計開発・テストQA）間の情報共有と連携体制を強化し、
新しい横断プロジェクトを立ち上げて課題の早期発見と品質向上を図る。

2. 出席者
チーム	出席者	役職
要件定義チーム	田中宏樹（リーダー）、鈴木真由	要件定義リーダー、業務アナリスト
設計・開発チーム	佐藤健（リーダー）、高橋純、伊藤萌	開発リーダー、テクニカルリード、テスター
テスト・品質保証チーム	山本綾子（リーダー）、藤原光、岡田奈々	QAリーダー、テストエンジニア、ドキュメント担当
3. 議題

各チームの進捗・課題共有

チーム間連携における課題整理

横断的課題への対応体制検討

新規「横断タスクフォース」設立とメンバー選定

4. 各チーム報告と課題
(1) 要件定義チーム（田中）

販売・在庫・会計の要件整理が進行中。

開発チームへの要件引き渡し時に認識齟齬が一部発生。

今後はレビュー会を定期的に開催し、仕様確定を段階的に行う必要あり。

(2) 設計・開発チーム（佐藤）

API開発が順調に進行しているが、要件変更反映の遅れが課題。

QAチームとのテストケース連携が不十分で、仕様解釈の差異が発生している。

コードレビューおよびCI/CDパイプライン共有をチーム横断で実施する案を提示。

(3) テスト・品質保証チーム（山本）

統合テスト準備が進行中だが、テスト環境のデータ不整合が多く再現テストに時間を要している。

開発・要件チームとの情報伝達が手動中心で遅延気味。

自動化・文書共有のルール整備が求められる。

5. 議論内容

全体で「要件→設計→テスト」間の連携に時間差が生じており、仕様確定の遅れが全体スケジュールに影響している。

開発フェーズ中にQA観点を取り入れる“シフトレフトテスト”を導入すべきとの意見が一致。

各チームが独自に管理している情報を統合するダッシュボード構築を提案（高橋）。

定例のチーム間ミーティングを月2回に増やす案が承認された。

6. 決定事項
🟩 新プロジェクト：「Cross-Functional Taskforce（CFT）」の設立

目的：

各チーム間のコミュニケーション改善と、開発・テスト効率の最大化を図る。

プロジェクト横断的に「品質」「スピード」「情報共有」を統括する。

🔸 プロジェクトリーダー

高橋純（設計・開発チーム／テクニカルリード）
→ 技術的視点と全体最適の観点から横断的調整を担当。

🔸 メンバー構成
所属チーム	氏名	役割	主な担当
要件定義チーム	鈴木真由	業務要件統合担当	各部門の要件情報をCFTへ展開し、仕様確定支援を行う。
設計・開発チーム	河合亮	DevOps推進担当	CI/CDと自動テスト環境の整備、品質向上支援。
テスト・品質保証チーム	藤原光	QA統合担当	テスト設計・自動化方針の策定と横断レビュー実施。
ドキュメントサポート	吉岡杏奈	情報共有・議事録担当	CFTミーティングの記録・資料整備・ナレッジ共有。
🔸 今後の活動方針

毎週金曜 15:00〜 CFT定例ミーティングを開催。

全チームで共通利用する「統合管理ダッシュボード（Notion）」を構築。

各担当は初回会議（10/30）までに担当領域の現状課題リストを提出。

初期目標：

要件反映までのリードタイム30％短縮

テスト準備期間20％短縮

ドキュメント共有率100％

7. 次回全体会議

日時：2025年11月6日（木） 14:00〜15:30

議題予定：

CFT活動進捗報告

ダッシュボード初期版レビュー

チーム間課題再確認

議事録作成者

岡田奈々（テスト・品質保証チーム／CFTドキュメント担当）

確認者

田中宏樹（要件定義リーダー）
佐藤健（開発リーダー）
山本綾子（QAリーダー）
```
## 議事録チーム２に新規参画者がきた
```text
🧑‍💻 設計・開発チーム 新規参画メンバー業務割り当て・指導体制決定書

チーム名：設計・開発チーム
プロジェクト：次世代販売管理システム開発PJ
決定日：2025年10月24日
承認者：佐藤健（開発リーダー）

1. 新規参画者概要
氏名	役割	スキル背景	想定稼働領域
森田悠真（もりた ゆうま）	アプリケーションエンジニア（新規参画）	Python、Django、Reactの実務経験2年／Webシステム開発経験	API開発補助およびUI連携処理の実装・テスト
2. 業務割り当て内容
🎯 主担当業務

会計APIおよび在庫APIの機能拡張開発支援

バックエンド側：Django REST Frameworkでの新規エンドポイント追加

フロント側：React UIとのデータ連携テスト支援

🔧 サブ業務

単体テストコード（pytest）追加・修正

APIドキュメント（OpenAPI仕様）の更新作業

CI/CDテスト環境でのデプロイ確認（河合との連携）

3. 指導体制
指導担当者	役職	指導内容
中村優	バックエンドエンジニア	Django REST FrameworkによるAPI実装・命名規則・ユニットテスト方法
石川怜奈	フロントエンドエンジニア	ReactによるUIとAPIの結合実装、通信エラー処理方針
河合亮	DevOpsエンジニア	開発環境構築・Gitフロー運用ルール・CI/CD連携方法
🔹 指導責任者

佐藤健（開発リーダー）

新人の進捗確認およびコードレビュー最終承認を担当。

チーム全体方針との整合性確認、スプリントレビューで評価実施。

4. 育成・フォローアップ計画
フェーズ	期間	目標	担当者
導入期	1〜2週目	環境構築・開発ルール理解・既存コードリーディング	河合・中村
実装期	3〜6週目	API機能追加・テストコード作成	中村・石川
定着期	7週目以降	単独での機能開発・コードレビュー参加	佐藤
5. 今後のアクション

10/25（金）午前：初回オンボーディング実施（担当：佐藤・河合）

10/28（火）：既存リポジトリアクセス権付与

11/1以降：スプリント#5から正式タスクアサイン開始

💡 コメント

チームリーダー 佐藤健
「森田さんにはバックエンド〜UI間の橋渡し役として、技術的にも成長しつつ即戦力化を期待しています。
各担当は積極的にレビューやペアプログラミングでフォローをお願いします。」
```
# 基にしたjson

```json
{
  "project": "次世代販売管理システム開発プロジェクト",
  "updated_at": "2025-10-23",
  "teams": [
    {
      "id": "T01",
      "name": "要件定義チーム",
      "leader": "田中宏樹",
      "member_count": 4,
      "tasks": [
        {
          "id": "TS01",
          "name": "業務要件整理",
          "status": "進行中",
          "description": "クライアント企業の販売・在庫・会計部門の業務フローを整理し、システム要件に落とし込む。",
          "members": [
            {
              "name": "田中宏樹",
              "role": "要件定義リーダー",
              "最近の作業": "販売部門ヒアリング資料の取りまとめ",
              "業務理解度": "高",
              "PJ化開始からの在籍年数": "3年",
              "teamsの被メンション数": 42,
              "メールの非To数": 8,
              "過去の業務": "基幹システム刷新PJ 要件定義責任者"
            },
            {
              "name": "鈴木真由",
              "role": "業務アナリスト",
              "最近の作業": "在庫業務ヒアリング議事録作成",
              "業務理解度": "中",
              "PJ化開始からの在籍年数": "1年",
              "teamsの被メンション数": 15,
              "メールの非To数": 2,
              "過去の業務": "購買システム改修案件 PM補佐"
            },
            {
              "name": "大森俊",
              "role": "会計担当アナリスト",
              "最近の作業": "会計部門の要件一覧更新",
              "業務理解度": "高",
              "PJ化開始からの在籍年数": "2年",
              "teamsの被メンション数": 10,
              "メールの非To数": 1,
              "過去の業務": "ERP導入支援コンサルタント"
            },
            {
              "name": "吉岡杏奈",
              "role": "ドキュメント担当",
              "最近の作業": "要件定義書第3版の体裁修正",
              "業務理解度": "低",
              "PJ化開始からの在籍年数": "0.5年",
              "teamsの被メンション数": 5,
              "メールの非To数": 0,
              "過去の業務": "営業事務サポート"
            }
          ]
        }
      ]
    },
    {
      "id": "T02",
      "name": "設計・開発チーム",
      "leader": "佐藤健",
      "member_count": 6,
      "tasks": [
        {
          "id": "TS02",
          "name": "API設計と実装",
          "status": "開発中",
          "description": "販売管理機能を中心にREST APIの設計とPython/Djangoによる実装を行う。",
          "members": [
            {
              "name": "佐藤健",
              "role": "開発リーダー",
              "最近の作業": "在庫APIのレビューとマージ",
              "業務理解度": "高",
              "PJ化開始からの在籍年数": "3年",
              "teamsの被メンション数": 58,
              "メールの非To数": 12,
              "過去の業務": "ECサイト統合開発責任者"
            },
            {
              "name": "中村優",
              "role": "バックエンドエンジニア",
              "最近の作業": "会計APIのテストコード追加",
              "業務理解度": "中",
              "PJ化開始からの在籍年数": "1.5年",
              "teamsの被メンション数": 25,
              "メールの非To数": 6,
              "過去の業務": "人事評価システムAPI開発"
            },
            {
              "name": "石川怜奈",
              "role": "フロントエンドエンジニア",
              "最近の作業": "ReactベースのUIプロトタイプ作成",
              "業務理解度": "中",
              "PJ化開始からの在籍年数": "2年",
              "teamsの被メンション数": 30,
              "メールの非To数": 5,
              "過去の業務": "販売ダッシュボード開発"
            },
            {
              "name": "高橋純",
              "role": "テクニカルリード",
              "最近の作業": "APIゲートウェイ設計指針レビュー",
              "業務理解度": "高",
              "PJ化開始からの在籍年数": "4年",
              "teamsの被メンション数": 48,
              "メールの非To数": 10,
              "過去の業務": "大手通信会社システム統合PJ 技術顧問"
            },
            {
              "name": "伊藤萌",
              "role": "テスター",
              "最近の作業": "販売API統合テスト実施",
              "業務理解度": "中",
              "PJ化開始からの在籍年数": "0.8年",
              "teamsの被メンション数": 8,
              "メールの非To数": 1,
              "過去の業務": "QAエンジニア（CRM製品）"
            },
            {
              "name": "河合亮",
              "role": "DevOpsエンジニア",
              "最近の作業": "CI/CDパイプラインの自動デプロイ設定",
              "業務理解度": "中",
              "PJ化開始からの在籍年数": "2年",
              "teamsの被メンション数": 20,
              "メールの非To数": 3,
              "過去の業務": "クラウド移行プロジェクト DevOps担当"
            }
          ]
        }
      ]
    },
    {
      "id": "T03",
      "name": "テスト・品質保証チーム",
      "leader": "山本綾子",
      "member_count": 3,
      "tasks": [
        {
          "id": "TS03",
          "name": "統合テスト・リリース前検証",
          "status": "準備中",
          "description": "リリース前の総合テストおよび品質保証プロセスを実施し、リリース判定を行う。",
          "members": [
            {
              "name": "山本綾子",
              "role": "QAリーダー",
              "最近の作業": "テスト項目書のレビュー",
              "業務理解度": "高",
              "PJ化開始からの在籍年数": "3年",
              "teamsの被メンション数": 18,
              "メールの非To数": 5,
              "過去の業務": "ERP品質保証プロジェクト責任者"
            },
            {
              "name": "藤原光",
              "role": "テストエンジニア",
              "最近の作業": "自動テストスクリプト整備",
              "業務理解度": "中",
              "PJ化開始からの在籍年数": "1.2年",
              "teamsの被メンション数": 7,
              "メールの非To数": 2,
              "過去の業務": "EC決済システムQA"
            },
            {
              "name": "岡田奈々",
              "role": "ドキュメント担当",
              "最近の作業": "不具合報告テンプレート作成",
              "業務理解度": "低",
              "PJ化開始からの在籍年数": "0.5年",
              "teamsの被メンション数": 3,
              "メールの非To数": 0,
              "過去の業務": "事務アシスタント"
            }
          ]
        }
      ]
    }
  ]
}

```

```text
次世代販売管理システム開発プロジェクト
├─ 要件定義チーム（田中宏樹）
│   └─ 業務要件整理（進行中）
│       ├─ 鈴木真由（業務アナリスト）
│       ├─ 大森俊（会計アナリスト）
│       └─ 吉岡杏奈（ドキュメント）
├─ 設計・開発チーム（佐藤健）
│   └─ API設計と実装（開発中）
│       ├─ 中村優（バックエンド）
│       ├─ 石川怜奈（フロント）
│       ├─ 高橋純（技術統括）
│       ├─ 伊藤萌（テスト）
│       └─ 河合亮（DevOps）
└─ テスト・品質保証チーム（山本綾子）
    └─ 統合テスト・リリース前検証（準備中）
        ├─ 藤原光（QA）
        └─ 岡田奈々（ドキュメント）
```
