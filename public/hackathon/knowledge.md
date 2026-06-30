---
title: ハッカソンを成功させるためのノウハウを書き込む
tags:
  - ハッカソン
  - 生成AI
private: true
updated_at: '2025-10-27T05:48:21+09:00'
id: beb262384c4acf59594a
organization_url_name: null
slide: false
ignorePublish: false
---

# とにかく情報の取得にはMicrosoft Graph API を使う。

teams

https://learn.microsoft.com/ja-jp/entra/identity/enterprise-apps/grant-admin-consent?pivots=portal

https://portal.azure.com
https://entra.microsoft.com/

# 💬 Microsoft Teams チャットを無料で取得する方法（会社アカウント環境向け）

以下で、  
1️⃣ 無料でできる範囲  
2️⃣ 必要な権限  
3️⃣ 実際に取得する手順  
を具体的に説明します👇

---

## ✅ 1. 無料でできる範囲

会社の Microsoft 365 テナントに **Azure AD（Microsoft Entra ID）** が含まれていれば、  
以下は **追加料金なしで利用可能** です。

| 機能 | 料金 | 備考 |
|:--|:--:|:--|
| Teams チャットメッセージの取得（Graph API） | ✅ 無料 | M365 Business / E1 / E3 / E5 ライセンスに含まれる |
| API 登録（App Registration） | ✅ 無料 | Azure Portalで登録可能 |
| トークン取得・呼び出し | ✅ 無料 | 認証後に Graph API 呼び出し可能 |

---

## 🧩 2. 必要な準備・権限

Teams のメッセージを取得するには、**Microsoft Graph API** の権限を設定します。

### 🔑 権限一覧

| 権限タイプ | 権限名 | 用途 |
|:--|:--|:--|
| Delegated | Chat.Read | サインイン中のユーザーが参加しているチャットを取得 |
| Delegated | ChannelMessage.Read.All | サインイン中のユーザーが参加しているチャンネルメッセージ取得 |
| Application | Chat.Read.All | 組織全体のチャットメッセージ取得（管理者同意必要） |
| Application | ChannelMessage.Read.All | 組織全体のTeamsチャンネルメッセージ取得（管理者同意必要） |

💡 **ポイント：**
- 自分のチャットだけ取得したい → **Delegated 権限でOK**
- 全社員のチャットを自動収集したい → **Application 権限＋管理者同意が必要**

---

## 🪜 3. 手順（無料で設定する方法）

### Step 1. Azureポータルでアプリ登録
1. [https://portal.azure.com](https://portal.azure.com) に会社アカウントでログイン  
2. 左メニュー → 「Microsoft Entra ID」 → 「アプリ登録」  
3. 「＋新しい登録」をクリック  
   - 名前：`TeamsChatReader`  
   - アカウントの種類：この組織ディレクトリ内のアカウントのみ  
   - 登録ボタンを押す  

---

### Step 2. API 権限を追加
1. 「API permissions」 → 「＋追加」  
2. 「Microsoft Graph」 → 「Delegated permissions」  
3. 以下を選択：  
   - `Chat.Read`  
   - `ChannelMessage.Read.All`  
4. 「同意」ボタンを押す（管理者であれば **admin consent** も付与）

---

### Step 3. クライアント情報を取得
アプリ登録画面で以下をコピー：
- `Application (client) ID`
- `Directory (tenant) ID`

---

### Step 4. 認証してトークンを取得（Python例）

ユーザーサインイン方式（Delegated権限）

```python
import requests
from msal import PublicClientApplication

client_id = "<YOUR_CLIENT_ID>"
tenant_id = "<YOUR_TENANT_ID>"
scopes = ["Chat.Read", "ChannelMessage.Read.All"]

app = PublicClientApplication(client_id, authority=f"https://login.microsoftonline.com/{tenant_id}")

result = app.acquire_token_interactive(scopes=scopes)
print(result["access_token"])
```
## Step 5. チャットメッセージを取得

```python
import requests

access_token = "<ACCESS_TOKEN>"
url = "https://graph.microsoft.com/v1.0/me/chats"

headers = {"Authorization": f"Bearer {access_token}"}
res = requests.get(url, headers=headers)
print(res.json())

chat_id = "<YOUR_CHAT_ID>"
res = requests.get(f"https://graph.microsoft.com/v1.0/chats/{chat_id}/messages", headers=headers)
print(res.json())

```
## 📦 まとめ

| 目的 | 必要権限 | 管理者同意 | 無料で可能か |
|:--|:--|:--:|:--:|
| 自分のチャットを取得 | Chat.Read | 不要 | ✅ 可能 |
| 自分の参加チャンネルのメッセージを取得 | ChannelMessage.Read.All | 不要 | ✅ 可能 |
| 全社チャットを取得 | Chat.Read.All | ✅ 必要 | ✅ (権限さえあれば) |
| 全社チャンネルメッセージ | ChannelMessage.Read.All | ✅ 必要 | ✅ (権限さえあれば) |


# ハッカソンで大事な考え方

参考 : https://zenn.dev/nogu66/articles/how-to-win-shipaton

# アイデアまとめ

- だれがどのプロジェクトで動いているかが分かりにくい。取次業務が増える。
- プロジェクト管理システムやタスク管理システムに登録する登録者側にメリットが少ない。
- 勤怠入力の際に無駄な手入力が必要な部分がある。
- AI技術教唆うが激しく、情報をまとめたり理解する作業が大変。新情報を素早く把握し、その位置づけを簡単に知りたい
- 交通費申請を1日単位ですることが手間
- 自分のメールやトークが客観的にどうみられるのかがわからない
- 社内問い合わせが個別に用意されていて聞くのに時間がかかる
- 社内の有益なナレッジがどこにあるかを下がることが難しい。
- 社内の検索機能が弱く必要とする情報にたどり着けない。事務作業に時間がかかる
- Chrome拡張、Edge拡張、VScode拡張などの拡張機能が使えないため他企業と比べてハンディキャップをかんじる
- 同じような質問やマニュアルに書いてある内容の質問への回答に時間がかかる
- 社内情報が探しづらく、探すのに時間がかかる
- システムがスプリントごとにどんどん複雑になっていき、新規プロジェクト参加者の作業システムの複製が難しい。
- インシデント太陽手順があいまいで顧客と事業者間で認識が一致していない。インシデント発生時の初動報告が遅く、顧客ニーズを満たせていない。
- 作業依頼・連絡手段・運用ルールがプロジェクト間で統一されておらず情報の見落としや対応遅れが発生している。
- 開発時に書いた膨大な数の設計書の変更管理作業に時間がかかり担当者の負担になっている。
- ソフトウェア開発における多数の設定値の管理及び変更内容の妥当性や使用との整合性の定期的な確認作業が煩雑かつ時間を要している。

ChatGPTによるアイデアまとめ

# 💡課題の共通テーマ

### 情報・ナレッジの分散と検索性の悪さ  
→ 情報がどこにあるかわからず、同じ質問が繰り返されている  

### 業務・管理システムの入力負担と利便性の低さ  
→ 勤怠、交通費、設定値など“登録者側のメリットが薄い”  

### 社内コミュニケーション・ナレッジ共有の非効率  
→ 問い合わせ、連絡、プロジェクト状況の可視化がバラバラ  

---

# 🎯方向性：生成AI × 業務効率化アプリケーション

以下に、ハッカソンで実装可能でインパクトのある生成AI活用案を3案提示します。  
いずれも「生成AI API（例：OpenAI API / Azure OpenAI / Claude API など）」を利用できます。

---

## 🧠 ① 「社内ナレッジ・アシスタント（Knowledge Finder）」

### コンセプト
社内のマニュアル・議事録・Q&A・Teams投稿などを横断検索し、  
生成AIが自然言語で回答・要約してくれる「社内ChatGPT」。

### 主な機能
- 社内ドキュメントを検索し、自然言語で質問できる（RAG構成）  
- 「過去の類似質問」や「関連マニュアル」を提示  
- Q&Aを自動登録しナレッジベースを拡充  

### 生成AIの使い方
- OpenAI API（gpt-4-turbo or gpt-4o-mini）をバックエンドに利用  
- RAG (Retrieval-Augmented Generation)構成  
  → 社内データを埋め込み＋ベクトル検索で回答生成  
- 自動要約・分類でナレッジタグ生成  

### 期待効果
- 問い合わせ・マニュアル探し時間の削減  
- 同じ質問への回答コストの削減  

---

## 🧾 ② 「Smart Work Entry — AI入力支援システム」

### コンセプト
勤怠・交通費・作業報告など、毎日のルーチン入力を  
AIが自動提案・入力補完してくれるツール。

### 主な機能
- 勤怠・交通費・タスク登録フォームにAI補完を導入  
- メールやスケジュール内容から自動で出勤／出張申請案を生成  
- 「前回と同じパターンですか？」の提案  

### 生成AIの使い方
- APIで自然言語から構造化データを抽出  
  （例：「今日出社して会議3件」→ 勤怠入力候補生成）  
- OpenAI function calling / JSON schema出力  
- 日報の自動生成（行動ログから要約）  

### 期待効果
- 入力作業の削減  
- 登録者側にも「提案＋自動化」でメリット発生  

---

## 🧩 ③ 「AIプロジェクトナビゲーター」

### コンセプト
社内プロジェクト状況・担当者・進捗・依頼ルートを  
一元管理＋生成AIで「誰に・何を・どこで聞けば良いか」を教えてくれる。

### 主な機能
- プロジェクト一覧・メンバー・タスク状況を可視化（自動抽出）  
- 「〇〇の設定変更は誰に依頼すればいい？」と聞ける  
- システム変更点をAIが要約してチーム共有（Gitログ・設計書変更点のサマリ）  

### 生成AIの使い方
- APIでプロジェクト文書やタスクを解析し、要約＋担当者関連付け  
- 「チームの誰が何をしているか」を自然言語検索  
- 設計書や設定変更ログを自動要約  

### 期待効果
- プロジェクト間連携の効率化  
- 情報の見落とし・重複作業を削減  

# 🚀 おすすめまとめ

| 案 | 名称 | 目的 | 生成AIの役割 | 難易度（ハッカソン向け） |
|:--:|:--|:--|:--|:--:|
| ① | 社内ナレッジアシスタント | 情報検索の効率化 | Q&A生成・要約・RAG検索 | ★★★ |
| ② | Smart Work Entry | 入力作業の自動化 | 入力補完・文脈抽出 | ★★ |
| ③ | AIプロジェクトナビゲーター | チーム間連携支援 | 要約・担当者特定 | ★★★★ |

## 具体的な計画例

# 💡 提案アプリ：「AIナレッジサーチャー（Knowledge Finder）」

社内に散らばるマニュアル・議事録・問い合わせ・FAQをまとめて検索できる  
生成AIベースの社内アシスタント

---

## 🧭 コンセプト
社内で「どこに何があるかわからない」「同じ質問を繰り返す」「社内検索が弱い」などの課題を解決。  
社員が自然言語で質問するだけで、AIがドキュメントを横断検索して回答・要約します。

---

## 🎯 想定ユーザー
- 社員・新規プロジェクト参加者  
- 社内ナレッジを効率的に探したい人  
- 問い合わせ対応を効率化したいバックオフィス・PM層  

---

## 🚀 目指す機能（MVP範囲）

| 機能 | 内容 | 技術構成 |
|:--|:--|:--|
| 🗂️ ドキュメント登録 | 社内FAQ・マニュアルなどをテキストとして登録 | CSV / PDF → テキスト抽出（PyPDF2など） |
| 🔍 質問検索（RAG） | ユーザーの質問を自然言語で入力 → 類似文書を検索して回答 | Embedding（OpenAI API）＋ FAISSベクトル検索 |
| 💬 AI回答生成 | 検索結果をもとにAIが要約・回答を生成 | GPT-4-turbo / GPT-4o-mini |
| 🧩 関連ドキュメント表示 | 回答に使われた元文書をリンクで表示 | URLリスト・タイトル参照 |
| 📈 ログ保存（任意） | 質問履歴を記録し改善 | SQLite / JSON形式保存 |

---

## ⚙️ 技術スタック

| カテゴリ | 使用技術 |
|:--|:--|
| バックエンド | Python + FastAPI |
| フロントエンド | Streamlit（簡単なUI構築） |
| ベクトルDB | FAISS（ローカルで軽量） |
| LLM API | OpenAI API（gpt-4o-mini） |
| Embedding | text-embedding-3-small |
| データ | CSV or PDFで事前準備した社内ドキュメントサンプル |
| デプロイ | ローカル実行 or Streamlit Cloud |

---

## 📅 スケジュール（3日間 × 8時間）

### 🔸 Day 1：企画・設計・環境構築
| 時間 | タスク |
|:--|:--|
| 0h–2h | チーム分担（フロント／バック／AIロジック）・要件整理 |
| 2h–5h | プロトタイプUI設計（Streamlit画面） |
| 5h–8h | OpenAI API接続テスト・ベクトルDB（FAISS）構築 |

**成果物：**
- OpenAI API連携確認  
- サンプルデータ埋め込み完了（例：マニュアル10件）  
- Streamlit UIの基本枠  

---

### 🔸 Day 2：実装フェーズ
| 時間 | タスク |
|:--|:--|
| 0h–3h | 検索→ベクトル類似検索（FAISS）処理実装 |
| 3h–5h | GPT応答生成機能（RAG構成）統合 |
| 5h–7h | フロント側から質問入力→回答表示まで連携 |
| 7h–8h | デザイン整備・エラーハンドリング調整 |

**成果物：**
- テキスト入力→AI回答まで一通り動作  
- 検索結果と参照文書を表示できる  

---

### 🔸 Day 3：ブラッシュアップ・発表準備
| 時間 | タスク |
|:--|:--|
| 0h–3h | 追加機能（質問履歴・関連文書リンク） |
| 3h–5h | デモデータ整備・応答チューニング |
| 5h–7h | プレゼン資料・デモ動画作成 |
| 7h–8h | 発表リハーサル・最終チェック |

**成果物：**
- 完成版デモ動作（質問→回答→関連文書）  
- 発表スライド（課題→解決策→デモ→効果）  

---

## 🧩 画面イメージ（Streamlit例）


---

## 🏁 成果アピールポイント（審査で強い）
- **「生成AI × 社内業務効率化」**という明確な価値  
- 社員全員が「明日から使いたい」と思える実用性  
- 3日間でMVP完成＋今後拡張可能（Teams連携・ナレッジ自動更新など）  

---

## 💬 発展アイデア（余力があれば）
- Teams Bot連携（チャットから直接質問）  
- ファイル自動クロール（OneDrive / SharePoint連携）  
- Q&A学習機能（よくある質問を自動保存）  

---

## ✅ まとめ

| 項目 | 内容 |
|:--|:--|
| プロジェクト名 | AIナレッジサーチャー（Knowledge Finder） |
| コンセプト | 生成AIで社内ナレッジを一発検索・要約 |
| 技術構成 | OpenAI API + FastAPI + Streamlit + FAISS |
| 所要時間 | 24時間（3日間） |
| 成果物 | 動作するRAG検索＋回答生成アプリ＋発表デモ |

---

もし希望があれば、  
👉 **「Day 1の具体的なコードテンプレート（OpenAI API × FAISS × Streamlit構成）」**  
をそのまま実行できる形で作成します。

### ハッカソンでの学びをメモする。

