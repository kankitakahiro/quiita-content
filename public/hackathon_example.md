---
title: ハッカソンでシステム検証のためのPJ例を作成する。
tags:
  - ハッカソン
  - 生成AI
private: true
updated_at: '2025-10-27T00:52:38+09:00'
id: 782d60db555591645e7c
organization_url_name: null
slide: false
ignorePublish: false
---

- [ハッカソンでシステム検証のためのPJ例を作成する。](#ハッカソンでシステム検証のためのpj例を作成する)
- [🏢 NEC 観光DX基盤構築プロジェクト（100名体制版）](#-nec-観光dx基盤構築プロジェクト100名体制版)
  - [🔷 全体概要](#-全体概要)
  - [🔸 構成チーム](#-構成チーム)
  - [① プロジェクトマネジメントオフィス（PMO）](#-プロジェクトマネジメントオフィスpmo)
  - [② データ基盤構築チーム（三宅チーム）](#-データ基盤構築チーム三宅チーム)
  - [③ AI分析チーム（藤原チーム）](#-ai分析チーム藤原チーム)
  - [④ システム運用・セキュリティチーム（井原チーム）](#-システム運用セキュリティチーム井原チーム)
  - [⑤ UX・顧客連携チーム（相沢チーム）](#-ux顧客連携チーム相沢チーム)
  - [⑥ 行政・自治体連携チーム（新設）](#-行政自治体連携チーム新設)
  - [⑦ 品質保証・テスト支援チーム（新設）](#-品質保証テスト支援チーム新設)
  - [🔹 合計人数](#-合計人数)
- [💬 Teams構成（NEC観光DX基盤構築PJ）](#-teams構成nec観光dx基盤構築pj)
  - [■ チーム構成（Teams上の最上位「チーム」）](#-チーム構成teams上の最上位チーム)
  - [■ チャネル構成（全体チーム配下）](#-チャネル構成全体チーム配下)
  - [■ 運用方針（抜粋）](#-運用方針抜粋)
- [① プロジェクトマネジメントオフィス（PMO）](#-プロジェクトマネジメントオフィスpmo-1)
  - [📘 第1週（10月13日週）](#-第1週10月13日週)
    - [会議①：PMO定例会議](#会議pmo定例会議)
    - [会議②：リスク対策検討ミーティング](#会議リスク対策検討ミーティング)
    - [teamsでの会話内容](#teamsでの会話内容)
    - [outlook予定表第一週](#outlook予定表第一週)
  - [📘 第2週（10月20日週）](#-第2週10月20日週)
    - [会議③：全体推進会議（行政・NEC合同）](#会議全体推進会議行政nec合同)
    - [会議④：成果物レビュー会議（PMO＋品質チーム）](#会議成果物レビュー会議pmo品質チーム)
    - [teamsでの会話内容](#teamsでの会話内容-1)
    - [outlook予定表第二週](#outlook予定表第二週)


# ハッカソンでシステム検証のためのPJ例を作成する。


# 🏢 NEC 観光DX基盤構築プロジェクト（100名体制版）

---

## 🔷 全体概要

- **総人数**： 約100名  
- **NEC本体社員**： 約60名  
- **協力会社・外部研究機関**： 約25名  
- **行政・観光事業者連携窓口**： 約15名  
- **プロジェクト期間**： 3年間（2025〜2028）

---

## 🔸 構成チーム

1. PMO（プロジェクト統括）  
2. データ基盤構築チーム  
3. AI分析チーム  
4. システム運用・セキュリティチーム  
5. UX・顧客連携チーム  
6. 行政・自治体連携チーム（新設）  
7. 品質保証・テスト支援チーム（新設）

---

## ① プロジェクトマネジメントオフィス（PMO）

**目的：**  
NECとして全体を統括し、スケジュール・品質・契約・リスク・対外報告を管理。

| 氏名 | 役職 | 主な担当 |
|------|------|----------|
| 石田 智久 | 統括PM | 全体統括、リスク・顧客対応 |
| 西川 麻衣 | 品質PM | 品質・テスト・リリース承認 |
| 森岡 翔 | 契約・調整担当 | 契約・納期・報告資料調整 |
| 松下 翔太 | スケジュール管理 | WBS・進捗ダッシュボード整備 |
| 竹田 隆 | コスト管理 | 予算・外注費・実績管理 |
| 原口 由香 | 成果物統括 | ドキュメントレビュー・納品管理 |
| 李 芳蘭（協力会社） | PMO補佐 | 資料整理・議事録・英語対応 |
| 中嶋 拓真 | リスク分析官 | リスクレジスタ更新・対応策検討 |
| 三田村 圭吾 | コミュニケーション担当 | 全体会議運営・Teams管理 |
| 宮野 里桜 | PMOアシスタント | 調整・報告書まとめ・議事録作成 |

**小計：10名**

---

## ② データ基盤構築チーム（三宅チーム）

**役割：**  
各自治体・事業者データを収集・加工・統合し、クラウド基盤（Azure）上にデータレイクとAPI群を構築。

| 氏名 | 役割 | 主な担当 |
|------|------|----------|
| 三宅 悠人 | チームリーダー | 全体設計・統括 |
| 白井 奏 | データアーキテクト | スキーマ定義・構造設計 |
| 木下 俊輔 | ETLリーダー | Airflow・ETL開発統括 |
| 青山 玲奈 | クラウド統括 | Azure環境構築・IaC整備 |
| 陳 文傑 | APIリード | APIゲートウェイ・認証方式 |
| 橋本 翼 | 品質管理 | データ品質検証・ログ整備 |
| 河野 遥 | データ連携管理 | 自治体データ調整 |
| 高柳 優 | 運用自動化 | スクリプト・自動リカバリ |
| 山岡 翔真（協力） | ETL開発支援 | ジョブ開発・テスト |
| 加賀 美雪 | データ統計担当 | 前処理・統計分析 |
| 岩城 直也 | ストレージ担当 | BLOB／SQL管理 |
| 浜田 俊 | データ品質分析 | 欠損・異常検出スクリプト |
| 神田 遼 | テスト担当 | データ連携試験 |
| 佐々木 智 | 運用支援 | クラウド監視設定 |
| 田村 知沙 | メタデータ管理 | カタログ化・データ辞書 |
| 陶 宏明（協力） | API開発 | 認証方式対応 |
| 大森 颯 | CI/CD構築 | GitHub Actions／Terraform |
| 小泉 明 | ドキュメント管理 | 設計書・構成図整理 |
| 平林 翔吾 | 調達連携 | 外部事業者データ契約 |
| 山本 航 | ネットワーク連携 | VPN／通信設定 |
| 横山 玲 | 匿名化設計 | 個人情報除去処理 |
| 水谷 里菜 | モニタリング | DataDog監視・閾値設定 |
| 福井 隆 | セキュリティ調整 | データ暗号化・キー管理 |
| 鈴村 隼 | 技術検証担当 | 新規ツール導入評価 |
| 北島 洋 | 運用統制 | バッチジョブ調整・障害報告 |

**小計：25名**

---

## ③ AI分析チーム（藤原チーム）

**役割：**  
観光需要予測、混雑分散、行動分析を行うAIモデル群の開発・運用。

| 氏名 | 役割 | 主な担当 |
|------|------|----------|
| 藤原 慎 | チーフDS | AI分析全体統括 |
| 中谷 洸 | MLリーダー | 学習基盤構築 |
| 本田 里帆 | アナリティクス | 精度評価・レポート |
| 加藤 一輝（大学研究員） | 学術連携 | 精度検証・研究支援 |
| 村井 泰正 | データ前処理 | 特徴量抽出 |
| 宮原 直美 | 可視化 | Power BI／Dash |
| 鈴木 亮 | チューニング | モデル最適化 |
| 佐久間 大地 | 再現性検証 | モデル比較・ログ追跡 |
| 南 真由 | ドキュメント | AI成果物管理 |
| 北原 翼 | モデル管理 | MLOps／バージョン管理 |
| 永田 桜 | 時系列分析 | 需要・イベント予測 |
| 中園 雅 | 評価基準整備 | 指標選定・レビュー |
| 大木 柚葉 | フィードバック反映 | 利用ログとの突合 |
| 立花 悠 | AI API開発 | 推論API構築 |
| 山下 悠真 | 推論最適化 | GPU最適化 |
| 佐野 美月 | QA担当 | 分析結果検証 |
| 坂本 昂大（協力） | クラウドAI運用 | Azure ML Ops |
| 趙 雪玲（大学院生） | 共同研究 | 外部学術検証 |
| 桑原 正義 | 外部委託調整 | データ提供契約 |
| 渡辺 彩 | 成果報告支援 | AI報告書・可視化まとめ |

**小計：20名**

---

## ④ システム運用・セキュリティチーム（井原チーム）

**役割：**  
クラウド稼働率維持・監視・脆弱性対応・アクセス管理・監査支援。

| 氏名 | 役割 | 主な担当 |
|------|------|----------|
| 井原 隼人 | 運用責任者 | 全体統括・報告書 |
| 篠原 佳奈 | セキュリティ分析 | SOC監査 |
| 村山 崇 | クラウド運用 | 監視・障害対応 |
| 大谷 翼 | ログ監査 | SIEM・権限管理 |
| 佐野 将平 | モニタリング | SLA監視 |
| 橋爪 康介 | 障害一次対応 | RCA報告 |
| 唐木 美咲 | ドキュメント | 運用手順書 |
| 山口 奈央 | バックアップ | DR計画 |
| 柴田 直人 | IAM担当 | 権限設定・統制 |
| 坂井 萌 | パッチ管理 | 定期更新 |
| 井村 謙 | 監査対応 | J-SOX・ISO27001準備 |
| 三宅 敦（協力） | SOC連携 | セキュリティ監視 |
| 阿久津 涼 | 自動化支援 | Ansible・運用スクリプト |
| 小野 真 | SLA管理 | 稼働率報告 |
| 梶原 里美 | 障害報告統括 | 顧客向け通知整理 |

**小計：15名**

---

## ⑤ UX・顧客連携チーム（相沢チーム）

**役割：**  
システム利用者（自治体・観光事業者）との接点を担当。  
UI改善、現地検証、利用者教育、広報・展示対応を行う。

| 氏名 | 役割 | 主な担当 |
|------|------|----------|
| 相沢 沙耶 | UXリーダー | UI設計・利用テスト |
| 長尾 海斗 | 顧客調整 | 自治体折衝 |
| 前田 恵 | 実証コーディネータ | 現地検証 |
| 高島 遼 | 広報・説明会 | イベント・セミナー運営 |
| 宮内 梓 | UIエンジニア | React／Power BI実装 |
| 岡村 沙良 | マニュアル作成 | 操作ガイド整備 |
| 菅原 渉 | 利用分析 | 利用統計・改善提案 |
| 藤井 凌 | 研修担当 | トレーニング資料 |
| 橘 颯太（協力） | 現地支援 | 実証現場運営 |
| 北谷 優花 | 調査員 | 利用者ヒアリング |
| 河合 健太 | UIテスター | デザイン評価 |
| 西原 勇 | 映像制作 | PR動画・教育素材 |
| 森田 早苗 | 問い合わせ対応 | サポートデスク |
| 小嶋 結 | ローカル支援 | 地域説明会補助 |
| 伊藤 悠人 | デザイン補佐 | デモUI整備 |

**小計：15名**

---

## ⑥ 行政・自治体連携チーム（新設）

**役割：**  
地方自治体・観光事業者との調整窓口。  
利用要望・データ提供契約・利用規約整備を担当。

| 氏名 | 役割 | 主な担当 |
|------|------|----------|
| 久保田 正 | チームリーダー | 自治体調整 |
| 佐川 美穂 | 契約管理 | 提携覚書・データ契約 |
| 小田 真 | 事業者窓口 | 宿泊・交通事業者連携 |
| 吉岡 陸 | 渉外担当 | 観光協会・大学連携 |
| 松永 忍 | データ提供管理 | API利用申請対応 |
| 西郷 光 | イベント連携 | 地域観光キャンペーン対応 |
| 林 千里 | 広報調整 | 行政発表・報道対応 |
| 大河内 涼 | 支援員 | 議事録・行政資料整理 |

**小計：8名**

---

## ⑦ 品質保証・テスト支援チーム（新設）

**役割：**  
各チーム横断で品質・テスト・リリース承認を担当。

| 氏名 | 役割 | 主な担当 |
|------|------|----------|
| 望月 俊 | QAリーダー | テスト計画策定 |
| 吉田 彩音 | テスト設計 | シナリオ設計 |
| 金子 健太 | 自動テスト | Selenium／Pytest運用 |
| 中野 遼 | 性能検証 | 負荷試験・応答計測 |
| 原田 美月 | 品質分析 | 不具合管理・品質指標 |
| 永田 智 | リリース管理 | バージョン統制 |
| 竹本 香 | 品質監査 | 外部監査対応・報告書作成 |

**小計：7名**

---

## 🔹 合計人数

| チーム | 人数 |
|---------|------|
| PMO | 10 |
| データ基盤 | 25 |
| AI分析 | 20 |
| 運用・セキュリティ | 15 |
| UX・顧客連携 | 15 |
| 行政・自治体連携 | 8 |
| 品質保証・テスト支援 | 7 |
| **合計** | **100名** |

# 💬 Teams構成（NEC観光DX基盤構築PJ）

---

## ■ チーム構成（Teams上の最上位「チーム」）

| チーム名（Teams単位） | 主な目的 | 主な参加者 |
|------------------------|-----------|-------------|
| 🏢 NEC観光DX基盤構築プロジェクト（全体） | 全体共有・横断連携・報告 | PMO・全チームリーダー・NEC本社報告担当 |
| 📊 データ基盤構築チーム | データレイク・API・ETL関連業務 | 三宅チーム全員＋PMO（松下・西川） |
| 🤖 AI分析チーム | モデル開発・精度評価・MLOps | 藤原チーム全員＋データ基盤チーム一部 |
| 🔐 運用・セキュリティチーム | 監視・権限管理・脆弱性対応 | 井原チーム全員＋品質保証チーム一部 |
| 👥 UX・顧客連携チーム | UI・顧客説明・実証運用 | 相沢チーム全員＋行政連携チーム一部 |
| 🏛️ 行政・自治体連携チーム | 自治体調整・契約・報道 | 久保田チーム全員＋PMO（森岡） |
| 🧪 品質保証・テスト支援チーム | テスト設計・品質承認 | 望月チーム全員＋各チームのQA担当者 |

---

## ■ チャネル構成（全体チーム配下）

> 各チームが共通で利用する主要チャネルは、プロジェクト横断の3チャネルに集約。

| チャネル名 | 目的 | 主な参加者 |
|--------------|-------|-------------|
| 📰 一般（General） | PMOからの全体連絡、アナウンス、資料共有 | 全メンバー（約100名） |
| 📅 定例・進捗報告 | 各チームの週次進捗共有、課題報告、会議記録 | PMO・各チームリーダー（約15名） |
| 💬 技術・課題共有 | 開発・AI・運用・UXなど、チーム横断の技術・課題共有 | 技術メンバー＋品質保証＋PMO |

---

## ■ 運用方針（抜粋）

- 「📅 定例・進捗報告」チャネルでは、毎週木曜の全体定例議事録と各チーム報告資料を投稿。  
- 「💬 技術・課題共有」チャネルでは、API認証、モデル精度改善、UI改善、セキュリティ対応など技術的ディスカッションを集約。  
- 各専門チームには個別のプライベートチャネルを設定（例：AI分析／UX実証／品質保証など）。  
- 重要議事録はPMOが「📅 定例・進捗報告」チャネルの上部にピン留め。

---

# ① プロジェクトマネジメントオフィス（PMO）


## 📘 第1週（10月13日週） 

### 会議①：PMO定例会議

```
日時： 2025年10月13日（月）10:00〜11:30
場所： Teams「PMO_定例」チャンネル
出席者：
石田（PM）、西川（品質）、森岡（契約）、松下（進捗）、竹田（コスト）、原口（成果物）、李（補佐）、中嶋（リスク）、三田村（コミュニケーション）、宮野（事務）

■ 議題一覧

各チーム進捗報告（AI／基盤／UX／運用）

リスク・課題管理表の更新

顧客向け月次報告書（10月分）進捗

契約・支払関連の整理

次回全体会議の準備

■ 議事概要

（1）各チーム進捗報告

三宅チーム（データ基盤）：交通事業者データの連携スキーマ確定、API v2.0テスト中。

藤原チーム（AI分析）：モデル精度（RMSE 0.18）改善、PoC2開始準備。

井原チーム（運用）：稼働率99.4％維持、バックアップ設定変更要。

相沢チーム（UX）：ダッシュボードUI改善案デモ予定（来週）。

（2）リスク・課題

自治体Bのデータ提供遅延（2週間遅れ見込み）。→ リスクレベル「中」継続。

Azureリソースコスト上昇（＋7％）。→ コスト管理チームが見積再算定。

（3）月次報告書

草案版を原口が作成済み。データ基盤チーム進捗グラフ追記予定（松下対応）。

（4）契約関連

追加PoC契約書（大学研究機関との協定）を森岡が行政側に提出。承認待ち。

（5）全体会議準備

顧客事務局との次回「全体推進会議」10/22(水)の資料作成担当を確定。

各チーム概要：石田

成果報告：西川

課題・リスク：中嶋

コスト見通し：竹田

■ 決定事項

月次報告書提出締切：10月17日（金）午前中

リスク#12「データ提供遅延」対応方針を再協議（10/20まで）

Azureコスト見直し提案を10/16の運用会議で提示

■ ToDoリスト
担当	内容	期限
松下	各チーム進捗表を最新版に更新（共有フォルダへ）	10/15
竹田	コスト試算再計算（クラウド費）	10/16
原口	月次報告書ドラフト完成	10/17
中嶋	リスクレジスタ更新（#12, #14）	10/16
石田	全体推進会議資料レビュー	10/21
```

### 会議②：リスク対策検討ミーティング

```
日時： 2025年10月16日（木）14:00〜15:00
場所： Teams「PMO_Risk」チャンネル
出席者： 石田、西川、中嶋、森岡、竹田、松下

■ 議題

自治体Bデータ遅延対応

システム監査結果報告（SOC監査）

次期リスクレビュー体制の再編

■ 議事概要

自治体Bデータ遅延

データ納品が11月初旬へ延期。AIチームの再学習工程に影響。

一時的に既存モデルでPoC継続、納品後に再学習対応。

調整窓口を森岡が担当し、自治体側に再スケジュール案を提示予定。

SOC監査結果

軽微な指摘2件（アクセス権限設定・パスワードポリシー更新漏れ）。

井原チームが10/20までに修正完了予定。

リスクレビュー体制

中嶋を中心に、週次更新から**自動レポート化（Power BI）**に移行検討。

■ 決定事項

自治体B対応を「緊急度：中」から「高」へ変更。

Power BI連携テストを10月末までに実施。

■ ToDo
担当	内容	期限
森岡	自治体Bへ新スケジュール提示	10/18
中嶋	リスクレポート自動化設計書	10/25
西川	監査指摘事項の対応完了報告	10/20
```

### teamsでの会話内容

```
📰 一般（General）
📢【PMO連絡】10月第3週 定例関連連絡

投稿者： 石田 智久（PM）
投稿日： 2025年10月13日（月）09:05

各位

おはようございます。今週のPMO定例（10:00〜）で扱う主な議題を共有します。

各チーム進捗（AI／基盤／UX／運用）

リスク#12（自治体Bデータ遅延）対応方針

10月分月次報告書進捗

次回全体会議（10/22）準備

定例後に議事録をこのチャネルへ共有予定です。

@西川麻衣 さん、品質・課題部分のサマリを会議後追記お願いします。

🟢 返信：西川 麻衣（品質PM）

承知しました。議事録フォーマットに沿って更新します。午後までに共有します。

📎【資料共有】月次報告書（草案版）

投稿者： 原口 由香（成果物統括）
投稿日： 2025年10月14日（火）16:40

月次報告書（10月分）の**草案版（v0.8）**をアップロードしました。

📁 共有フォルダへのリンク

@松下翔太 さん、進捗グラフデータ更新をお願いします。
@西川麻衣 さん、品質指標（テスト進捗）部分を追記予定で問題ありませんか？

🟢 返信：松下 翔太（スケジュール管理）

了解しました。AIチーム・基盤チームからの最新進捗（10/13時点）を反映して明朝までにグラフ更新します。

🟢 返信：西川 麻衣

はい、品質データを10/15午前中に反映します。

✅【報告】Azureコスト見直し試算完了

投稿者： 竹田 隆（コスト管理）
投稿日： 2025年10月17日（金）11:30

Azure利用料の再試算が完了しました。

コスト上昇要因：ログアーカイブ領域の肥大化（＋7%）

対策案：ストレージ階層を「Hot→Cool」へ一部移行で▲4%削減見込み

詳細レポートを添付しました。
📎 Azure_Cost_Review_20251017.xlsx

@井原 俊介 さん、10/16運用会議での提案内容と整合性を再確認お願いします。

🟢 返信：井原 俊介（運用チームリーダー）

ありがとうございます。運用側で検証済み、内容問題ありません。来週から試行導入します。

📅 定例・進捗報告
🧩【共有】10/13 PMO定例議事録（要約）

投稿者： 松下 翔太（進捗管理）
投稿日： 2025年10月13日（月）13:40

PMO定例（10:00〜11:30）の議事録を共有します。

主な決定事項：

月次報告書締切：10/17(金) 午前中

Azureコスト見直し提案：10/16 運用会議で提示

リスク#12「データ提供遅延」：10/20再協議

詳細版はこちらのリンク
をご確認ください。

🟢 返信：藤原 達也（AI分析リーダー）

ありがとうございます。AIチーム側ではデータ遅延影響を整理中。PoC工程の再スケジュール案を今週中に共有します。

🟢 返信：相沢 美帆（UXチーム）

ダッシュボードUI改善案のデモ準備進んでいます。来週月曜の全体会議で画面共有予定です。

⚠️【進捗報告】リスク#12自治体Bデータ遅延対応

投稿者： 中嶋 陽介（リスク管理）
投稿日： 2025年10月16日（木）09:00

本日のリスク対策ミーティング（14:00〜）前に現状整理します。

データ納品予定：11月初旬

影響：AI再学習スケジュール（PoC2開始延期リスク）

暫定対応：既存モデルでPoC継続

会議で「緊急度：中→高」への変更提案予定です。

@森岡 翔 さん、自治体側への再スケジュール提示資料のドラフト、準備状況教えてください。

🟢 返信：森岡 翔（契約・調整担当）

ドラフト版は完成済みです。13:00に自治体側担当へ送付予定。正式合意を週明けに見込み。

🗓️【完了報告】月次報告書ドラフト提出

投稿者： 原口 由香（成果物統括）
投稿日： 2025年10月17日（金）10:20

月次報告書（10月分）を提出完了しました。

@石田 智久 さん @西川 麻衣 さん
ご確認お願いします。10/22全体推進会議の資料への反映は完了済みです。

🟢 返信：石田 智久（PM）

確認しました。内容問題なしです。お疲れさまでした。

💬 技術・課題共有
💡【技術相談】Power BI リスクレポート自動化

投稿者： 中嶋 陽介（リスク管理）
投稿日： 2025年10月16日（木）17:10

@三宅 俊介 さん
データ基盤チームで管理している「リスク管理Excel（SharePoint）」をPower BIで自動更新できるようにしたいです。

現在の課題：

Excelファイルのパス固定ができず、更新時にデータソースが切れる

何か設定上のベストプラクティスありますか？

🟢 返信：三宅 俊介（データ基盤リーダー）

あります。SharePoint上のExcelは「ドキュメントライブラリ→Excel→接続→リンクをコピー→?web=1」を削除したURLをPower BI側に設定してください。

次回のPMOリスク会議までにサンプルレポートを作ってもOKです。

🟢 返信：中嶋 陽介

ありがとうございます！10/25までに試作レポート版を共有します。

🧠【AI分析】再学習スケジュール変更の影響確認

投稿者： 藤原 達也（AI分析リーダー）
投稿日： 2025年10月17日（金）14:00

自治体Bデータ納品遅延の件で、AIモデル再学習スケジュールを再整理しました。

既存モデルでPoC2継続（10/18〜10/31）

再学習工程を11/4開始に変更予定

@松下翔太 さん、進捗管理表への反映お願いします。
@西川麻衣 さん、精度評価KPIの追記項目を再確認お願いします。

🟢 返信：松下 翔太

承知しました。本日の進捗表に反映します。

🟢 返信：西川 麻衣

KPI定義に変更はなし。再学習後に再評価します。

🧾【完了報告】SOC監査対応

投稿者： 井原 俊介（運用チームリーダー）
投稿日： 2025年10月20日（月）09:10

@西川麻衣 さん
SOC監査で指摘のあった2件（アクセス権限／パスワードポリシー）は、10/19付で修正完了しました。

修正証跡（スクリーンショット＋設定履歴）をBoxにアップ済みです。

🟢 返信：西川 麻衣

確認しました。品質レポート更新に反映します。迅速な対応ありがとうございました。
```
```
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('team-obsdx')/channels/messages",
  "team": {
    "id": "team-obsdx",
    "displayName": "観光DX基盤構築プロジェクト（NEC主導）"
  },
  "fetchedAtUtc": "2025-10-27T16:00:00Z",
  "channels": [
    {
      "id": "19:general@thread.tacv2",
      "displayName": "一般（General）",
      "messages": [
        {
          "id": "msg-gen-001",
          "replyToId": null,
          "createdDateTime": "2025-10-13T00:05:00Z",
          "lastModifiedDateTime": "2025-10-13T00:05:00Z",
          "messageType": "message",
          "subject": "【PMO連絡】10月第3週 定例関連連絡",
          "from": {
            "user": {
              "id": "u-ishida",
              "displayName": "石田 智久（PM）",
              "userPrincipalName": "tomohisa.ishida@contoso.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<p>各位</p><p>おはようございます。今週のPMO定例（10:00〜）で扱う主な議題を共有します。</p><ul><li>各チーム進捗（AI／基盤／UX／運用）</li><li>リスク#12（自治体Bデータ遅延）対応方針</li><li>10月分月次報告書進捗</li><li>次回全体会議（10/22）準備</li></ul><p>定例後に議事録をこのチャネルへ共有予定です。</p><p><at id=\"0\">西川麻衣</at> さん、品質・課題部分のサマリを会議後追記お願いします。</p>"
          },
          "mentions": [
            {
              "id": 0,
              "mentioned": {
                "user": {
                  "id": "u-nishikawa",
                  "displayName": "西川 麻衣（品質PM）",
                  "userPrincipalName": "mai.nishikawa@contoso.com"
                }
              },
              "mentionText": "西川麻衣"
            }
          ],
          "attachments": [],
          "reactions": [],
          "replies": [
            {
              "id": "msg-gen-001-r1",
              "replyToId": "msg-gen-001",
              "createdDateTime": "2025-10-13T01:10:00Z",
              "lastModifiedDateTime": "2025-10-13T01:10:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-nishikawa",
                  "displayName": "西川 麻衣（品質PM）",
                  "userPrincipalName": "mai.nishikawa@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>承知しました。議事録フォーマットに沿って更新します。午後までに共有します。</p>"
              },
              "mentions": [],
              "attachments": [],
              "reactions": []
            }
          ]
        },
        {
          "id": "msg-gen-002",
          "replyToId": null,
          "createdDateTime": "2025-10-14T07:40:00Z",
          "lastModifiedDateTime": "2025-10-14T07:40:00Z",
          "messageType": "message",
          "subject": "【資料共有】月次報告書（草案版）",
          "from": {
            "user": {
              "id": "u-haraguchi",
              "displayName": "原口 由香（成果物統括）",
              "userPrincipalName": "yuka.haraguchi@contoso.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<p>月次報告書（10月分）の<b>草案版（v0.8）</b>をアップロードしました。</p><p><a href=\"https://contoso.sharepoint.com/sites/dx/Shared%20Documents/Reports/2025-10\">共有フォルダへのリンク</a></p><p><at id=\"0\">松下翔太</at> さん、進捗グラフデータ更新をお願いします。<br/><at id=\"1\">西川麻衣</at> さん、品質指標（テスト進捗）部分を追記予定で問題ありませんか？</p>"
          },
          "mentions": [
            {
              "id": 0,
              "mentioned": {
                "user": { "id": "u-matsushita", "displayName": "松下 翔太（スケジュール管理）", "userPrincipalName": "shota.matsushita@contoso.com" }
              },
              "mentionText": "松下翔太"
            },
            {
              "id": 1,
              "mentioned": {
                "user": { "id": "u-nishikawa", "displayName": "西川 麻衣（品質PM）", "userPrincipalName": "mai.nishikawa@contoso.com" }
              },
              "mentionText": "西川麻衣"
            }
          ],
          "attachments": [
            {
              "id": "att-001",
              "contentType": "reference",
              "name": "共有フォルダへのリンク",
              "contentUrl": "https://contoso.sharepoint.com/sites/dx/Shared%20Documents/Reports/2025-10"
            }
          ],
          "reactions": [],
          "replies": [
            {
              "id": "msg-gen-002-r1",
              "replyToId": "msg-gen-002",
              "createdDateTime": "2025-10-14T08:05:00Z",
              "lastModifiedDateTime": "2025-10-14T08:05:00Z",
              "messageType": "message",
              "from": {
                "user": { "id": "u-matsushita", "displayName": "松下 翔太（スケジュール管理）", "userPrincipalName": "shota.matsushita@contoso.com" }
              },
              "body": { "contentType": "html", "content": "<p>了解しました。AIチーム・基盤チームからの最新進捗（10/13時点）を反映して明朝までにグラフ更新します。</p>" },
              "mentions": [],
              "attachments": [],
              "reactions": []
            },
            {
              "id": "msg-gen-002-r2",
              "replyToId": "msg-gen-002",
              "createdDateTime": "2025-10-14T08:10:00Z",
              "lastModifiedDateTime": "2025-10-14T08:10:00Z",
              "messageType": "message",
              "from": {
                "user": { "id": "u-nishikawa", "displayName": "西川 麻衣（品質PM）", "userPrincipalName": "mai.nishikawa@contoso.com" }
              },
              "body": { "contentType": "html", "content": "<p>はい、品質データを10/15午前中に反映します。</p>" },
              "mentions": [],
              "attachments": [],
              "reactions": []
            }
          ]
        },
        {
          "id": "msg-gen-003",
          "replyToId": null,
          "createdDateTime": "2025-10-17T02:30:00Z",
          "lastModifiedDateTime": "2025-10-17T02:30:00Z",
          "messageType": "message",
          "subject": "【報告】Azureコスト見直し試算完了",
          "from": {
            "user": { "id": "u-takeda", "displayName": "竹田 隆（コスト管理）", "userPrincipalName": "takashi.takeda@contoso.com" }
          },
          "body": {
            "contentType": "html",
            "content": "<p>Azure利用料の再試算が完了しました。</p><p>コスト上昇要因：ログアーカイブ領域の肥大化（＋7%）<br/>対策案：ストレージ階層を「Hot→Cool」へ一部移行で▲4%削減見込み</p><p>詳細レポートを添付しました。</p><p><at id=\"0\">井原 俊介</at> さん、10/16運用会議での提案内容と整合性を再確認お願いします。</p>"
          },
          "mentions": [
            {
              "id": 0,
              "mentioned": { "user": { "id": "u-ihara", "displayName": "井原 俊介（運用チームリーダー）", "userPrincipalName": "shunsuke.ihara@contoso.com" } },
              "mentionText": "井原 俊介"
            }
          ],
          "attachments": [
            {
              "id": "att-002",
              "contentType": "fileReference",
              "name": "Azure_Cost_Review_20251017.xlsx",
              "contentUrl": "https://contoso.box.com/file/1234567890",
              "thumbnailUrl": null
            }
          ],
          "replies": [
            {
              "id": "msg-gen-003-r1",
              "replyToId": "msg-gen-003",
              "createdDateTime": "2025-10-17T03:00:00Z",
              "lastModifiedDateTime": "2025-10-17T03:00:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-ihara", "displayName": "井原 俊介（運用チームリーダー）", "userPrincipalName": "shunsuke.ihara@contoso.com" } },
              "body": { "contentType": "html", "content": "<p>ありがとうございます。運用側で検証済み、内容問題ありません。来週から試行導入します。</p>" },
              "mentions": [],
              "attachments": [],
              "reactions": []
            }
          ]
        }
      ]
    },
    {
      "id": "19:status@thread.tacv2",
      "displayName": "定例・進捗報告",
      "messages": [
        {
          "id": "msg-sta-001",
          "replyToId": null,
          "createdDateTime": "2025-10-13T04:40:00Z",
          "lastModifiedDateTime": "2025-10-13T04:40:00Z",
          "messageType": "message",
          "subject": "【共有】10/13 PMO定例議事録（要約）",
          "from": { "user": { "id": "u-matsushita", "displayName": "松下 翔太（進捗管理）", "userPrincipalName": "shota.matsushita@contoso.com" } },
          "body": {
            "contentType": "html",
            "content": "<p>PMO定例（10:00〜11:30）の議事録を共有します。</p><p><b>主な決定事項：</b></p><ul><li>月次報告書締切：10/17(金) 午前中</li><li>Azureコスト見直し提案：10/16 運用会議で提示</li><li>リスク#12「データ提供遅延」：10/20再協議</li></ul><p>詳細版はこちらのリンクをご確認ください。</p>"
          },
          "attachments": [
            {
              "id": "att-003",
              "contentType": "reference",
              "name": "議事録詳細",
              "contentUrl": "https://contoso.sharepoint.com/sites/dx/Shared%20Documents/Minutes/PMO_20251013.pdf"
            }
          ],
          "replies": [
            {
              "id": "msg-sta-001-r1",
              "replyToId": "msg-sta-001",
              "createdDateTime": "2025-10-13T05:00:00Z",
              "lastModifiedDateTime": "2025-10-13T05:00:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-fujiwara", "displayName": "藤原 達也（AI分析リーダー）", "userPrincipalName": "tatsuya.fujiwara@contoso.com" } },
              "body": { "contentType": "html", "content": "<p>ありがとうございます。AIチーム側ではデータ遅延影響を整理中。PoC工程の再スケジュール案を今週中に共有します。</p>" },
              "attachments": [],
              "reactions": []
            },
            {
              "id": "msg-sta-001-r2",
              "replyToId": "msg-sta-001",
              "createdDateTime": "2025-10-13T05:05:00Z",
              "lastModifiedDateTime": "2025-10-13T05:05:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-aizawa", "displayName": "相沢 美帆（UXチーム）", "userPrincipalName": "miho.aizawa@contoso.com" } },
              "body": { "contentType": "html", "content": "<p>ダッシュボードUI改善案のデモ準備進んでいます。来週月曜の全体会議で画面共有予定です。</p>" },
              "attachments": [],
              "reactions": []
            }
          ]
        },
        {
          "id": "msg-sta-002",
          "replyToId": null,
          "createdDateTime": "2025-10-16T00:00:00Z",
          "lastModifiedDateTime": "2025-10-16T00:00:00Z",
          "messageType": "message",
          "subject": "【進捗報告】リスク#12自治体Bデータ遅延対応",
          "from": { "user": { "id": "u-nakajima", "displayName": "中嶋 陽介（リスク管理）", "userPrincipalName": "yosuke.nakajima@contoso.com" } },
          "body": {
            "contentType": "html",
            "content": "<p>本日のリスク対策ミーティング（14:00〜）前に現状整理します。</p><ul><li>データ納品予定：11月初旬</li><li>影響：AI再学習スケジュール（PoC2開始延期リスク）</li><li>暫定対応：既存モデルでPoC継続</li></ul><p>会議で「緊急度：中→高」への変更提案予定です。</p><p><at id=\"0\">森岡 翔</at> さん、自治体側への再スケジュール提示資料のドラフト、準備状況教えてください。</p>"
          },
          "mentions": [
            {
              "id": 0,
              "mentioned": { "user": { "id": "u-morioka", "displayName": "森岡 翔（契約・調整担当）", "userPrincipalName": "sho.morioka@contoso.com" } },
              "mentionText": "森岡 翔"
            }
          ],
          "attachments": [],
          "replies": [
            {
              "id": "msg-sta-002-r1",
              "replyToId": "msg-sta-002",
              "createdDateTime": "2025-10-16T04:00:00Z",
              "lastModifiedDateTime": "2025-10-16T04:00:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-morioka", "displayName": "森岡 翔（契約・調整担当）", "userPrincipalName": "sho.morioka@contoso.com" } },
              "body": { "contentType": "html", "content": "<p>ドラフト版は完成済みです。13:00に自治体側担当へ送付予定。正式合意を週明けに見込み。</p>" },
              "attachments": [],
              "reactions": []
            }
          ]
        },
        {
          "id": "msg-sta-003",
          "replyToId": null,
          "createdDateTime": "2025-10-17T01:20:00Z",
          "lastModifiedDateTime": "2025-10-17T01:20:00Z",
          "messageType": "message",
          "subject": "【完了報告】月次報告書ドラフト提出",
          "from": { "user": { "id": "u-haraguchi", "displayName": "原口 由香（成果物統括）", "userPrincipalName": "yuka.haraguchi@contoso.com" } },
          "body": {
            "contentType": "html",
            "content": "<p>月次報告書（10月分）を提出完了しました。</p><p><at id=\"0\">石田 智久</at> さん <at id=\"1\">西川 麻衣</at> さん ご確認お願いします。10/22全体推進会議の資料への反映は完了済みです。</p>"
          },
          "mentions": [
            { "id": 0, "mentioned": { "user": { "id": "u-ishida", "displayName": "石田 智久（PM）", "userPrincipalName": "tomohisa.ishida@contoso.com" } }, "mentionText": "石田 智久" },
            { "id": 1, "mentioned": { "user": { "id": "u-nishikawa", "displayName": "西川 麻衣（品質PM）", "userPrincipalName": "mai.nishikawa@contoso.com" } }, "mentionText": "西川 麻衣" }
          ],
          "attachments": [],
          "replies": [
            {
              "id": "msg-sta-003-r1",
              "replyToId": "msg-sta-003",
              "createdDateTime": "2025-10-17T01:35:00Z",
              "lastModifiedDateTime": "2025-10-17T01:35:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-ishida", "displayName": "石田 智久（PM）", "userPrincipalName": "tomohisa.ishida@contoso.com" } },
              "body": { "contentType": "html", "content": "<p>確認しました。内容問題なしです。お疲れさまでした。</p>" },
              "attachments": [],
              "reactions": []
            }
          ]
        }
      ]
    },
    {
      "id": "19:tech@thread.tacv2",
      "displayName": "技術・課題共有",
      "messages": [
        {
          "id": "msg-tech-001",
          "replyToId": null,
          "createdDateTime": "2025-10-16T08:10:00Z",
          "lastModifiedDateTime": "2025-10-16T08:10:00Z",
          "messageType": "message",
          "subject": "【技術相談】Power BI リスクレポート自動化",
          "from": { "user": { "id": "u-nakajima", "displayName": "中嶋 陽介（リスク管理）", "userPrincipalName": "yosuke.nakajima@contoso.com" } },
          "body": {
            "contentType": "html",
            "content": "<p><at id=\"0\">三宅 俊介</at> さん</p><p>データ基盤チームで管理している「リスク管理Excel（SharePoint）」をPower BIで自動更新できるようにしたいです。</p><p><b>現在の課題：</b></p><ul><li>Excelファイルのパス固定ができず、更新時にデータソースが切れる</li><li>何か設定上のベストプラクティスありますか？</li></ul>"
          },
          "mentions": [
            { "id": 0, "mentioned": { "user": { "id": "u-miyake", "displayName": "三宅 俊介（データ基盤リーダー）", "userPrincipalName": "shunsuke.miyake@contoso.com" } }, "mentionText": "三宅 俊介" }
          ],
          "attachments": [],
          "replies": [
            {
              "id": "msg-tech-001-r1",
              "replyToId": "msg-tech-001",
              "createdDateTime": "2025-10-16T08:25:00Z",
              "lastModifiedDateTime": "2025-10-16T08:25:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-miyake", "displayName": "三宅 俊介（データ基盤リーダー）", "userPrincipalName": "shunsuke.miyake@contoso.com" } },
              "body": {
                "contentType": "html",
                "content": "<p>あります。SharePoint上のExcelは「ドキュメントライブラリ→Excel→接続→リンクをコピー→?web=1」を削除したURLをPower BI側に設定してください。</p><p>次回のPMOリスク会議までにサンプルレポートを作ってもOKです。</p>"
              },
              "attachments": [],
              "reactions": []
            },
            {
              "id": "msg-tech-001-r2",
              "replyToId": "msg-tech-001",
              "createdDateTime": "2025-10-16T08:30:00Z",
              "lastModifiedDateTime": "2025-10-16T08:30:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-nakajima", "displayName": "中嶋 陽介（リスク管理）", "userPrincipalName": "yosuke.nakajima@contoso.com" } },
              "body": { "contentType": "html", "content": "<p>ありがとうございます！10/25までに試作レポート版を共有します。</p>" },
              "attachments": [],
              "reactions": []
            }
          ]
        },
        {
          "id": "msg-tech-002",
          "replyToId": null,
          "createdDateTime": "2025-10-17T05:00:00Z",
          "lastModifiedDateTime": "2025-10-17T05:00:00Z",
          "messageType": "message",
          "subject": "【AI分析】再学習スケジュール変更の影響確認",
          "from": { "user": { "id": "u-fujiwara", "displayName": "藤原 達也（AI分析リーダー）", "userPrincipalName": "tatsuya.fujiwara@contoso.com" } },
          "body": {
            "contentType": "html",
            "content": "<p>自治体Bデータ納品遅延の件で、AIモデル再学習スケジュールを再整理しました。</p><ul><li>既存モデルでPoC2継続（10/18〜10/31）</li><li>再学習工程を11/4開始に変更予定</li></ul><p><at id=\"0\">松下翔太</at> さん、進捗管理表への反映お願いします。<br/><at id=\"1\">西川麻衣</at> さん、精度評価KPIの追記項目を再確認お願いします。</p>"
          },
          "mentions": [
            { "id": 0, "mentioned": { "user": { "id": "u-matsushita", "displayName": "松下 翔太（スケジュール管理）", "userPrincipalName": "shota.matsushita@contoso.com" } }, "mentionText": "松下翔太" },
            { "id": 1, "mentioned": { "user": { "id": "u-nishikawa", "displayName": "西川 麻衣（品質PM）", "userPrincipalName": "mai.nishikawa@contoso.com" } }, "mentionText": "西川麻衣" }
          ],
          "attachments": [],
          "replies": [
            {
              "id": "msg-tech-002-r1",
              "replyToId": "msg-tech-002",
              "createdDateTime": "2025-10-17T05:10:00Z",
              "lastModifiedDateTime": "2025-10-17T05:10:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-matsushita", "displayName": "松下 翔太（スケジュール管理）", "userPrincipalName": "shota.matsushita@contoso.com" } },
              "body": { "contentType": "html", "content": "<p>承知しました。本日の進捗表に反映します。</p>" },
              "attachments": [],
              "reactions": []
            },
            {
              "id": "msg-tech-002-r2",
              "replyToId": "msg-tech-002",
              "createdDateTime": "2025-10-17T05:12:00Z",
              "lastModifiedDateTime": "2025-10-17T05:12:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-nishikawa", "displayName": "西川 麻衣（品質PM）", "userPrincipalName": "mai.nishikawa@contoso.com" } },
              "body": { "contentType": "html", "content": "<p>KPI定義に変更はなし。再学習後に再評価します。</p>" },
              "attachments": [],
              "reactions": []
            }
          ]
        },
        {
          "id": "msg-tech-003",
          "replyToId": null,
          "createdDateTime": "2025-10-20T00:10:00Z",
          "lastModifiedDateTime": "2025-10-20T00:10:00Z",
          "messageType": "message",
          "subject": "【完了報告】SOC監査対応",
          "from": { "user": { "id": "u-ihara", "displayName": "井原 俊介（運用チームリーダー）", "userPrincipalName": "shunsuke.ihara@contoso.com" } },
          "body": {
            "contentType": "html",
            "content": "<p><at id=\"0\">西川麻衣</at> さん</p><p>SOC監査で指摘のあった2件（アクセス権限／パスワードポリシー）は、10/19付で修正完了しました。</p><p>修正証跡（スクリーンショット＋設定履歴）をBoxにアップ済みです。</p>"
          },
          "mentions": [
            { "id": 0, "mentioned": { "user": { "id": "u-nishikawa", "displayName": "西川 麻衣（品質PM）", "userPrincipalName": "mai.nishikawa@contoso.com" } }, "mentionText": "西川麻衣" }
          ],
          "attachments": [
            {
              "id": "att-004",
              "contentType": "reference",
              "name": "監査対応証跡",
              "contentUrl": "https://contoso.box.com/folder/87654321"
            }
          ],
          "replies": [
            {
              "id": "msg-tech-003-r1",
              "replyToId": "msg-tech-003",
              "createdDateTime": "2025-10-20T00:25:00Z",
              "lastModifiedDateTime": "2025-10-20T00:25:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-nishikawa", "displayName": "西川 麻衣（品質PM）", "userPrincipalName": "mai.nishikawa@contoso.com" } },
              "body": { "contentType": "html", "content": "<p>確認しました。品質レポート更新に反映します。迅速な対応ありがとうございました。</p>" },
              "attachments": [],
              "reactions": []
            }
          ]
        }
      ]
    }
  ]
}

```

### outlook予定表第一週

```
✅ 想定されるOutlook予定（抜粋）

PMO定例会議

日時: 2025-10-13 (月) 10:00–11:30

参加: 石田（主催）、西川、森岡、松下、竹田、原口、李、中嶋、三田村、宮野

開催: Microsoft Teams（PMO_定例）

メモ: 当日の議題共有・リスク#12・月次報告・10/22全体推進会議準備

リスク対策検討ミーティング

日時: 2025-10-16 (木) 14:00–15:00

参加: 石田、西川、中嶋、森岡、竹田、松下

開催: Microsoft Teams（PMO_Risk）

メモ: 自治体Bデータ遅延対応（緊急度：中→高）、SOC監査対応、リスクレポート自動化

全体推進会議

日時: 2025-10-22 (水) 10:00–11:30

参加: PMO＋各チームリーダー（約15名）

開催: Microsoft Teams（全体推進会議）

メモ: 10月分月次報告／各チーム進捗／リスク・コスト見通し／UXデモ共有

月次報告書 提出締切（ドラフト）

形式: 終日予定（リマインダー 09:00）

日付: 2025-10-17 (金)

参加: 原口（担当）、石田／西川（確認）

メモ: ドラフト提出・10/22向け資料反映
```

```json
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#me/calendarView",
  "value": [
    {
      "id": "evt-pmo-20251013",
      "subject": "PMO定例会議",
      "bodyPreview": "各チーム進捗／リスク#12／月次報告／10/22全体推進会議準備",
      "body": {
        "contentType": "html",
        "content": "<p>PMO定例。議題：各チーム進捗、リスク#12（自治体Bデータ遅延）、10月分月次報告、10/22全体推進会議準備。</p>"
      },
      "organizer": {
        "emailAddress": { "name": "石田 智久（PM）", "address": "tomohisa.ishida@contoso.com" }
      },
      "attendees": [
        { "type": "required", "emailAddress": { "name": "西川 麻衣（品質PM）", "address": "mai.nishikawa@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "森岡 翔", "address": "sho.morioka@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "松下 翔太", "address": "shota.matsushita@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "竹田 隆", "address": "takashi.takeda@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "原口 由香", "address": "yuka.haraguchi@contoso.com" } },
        { "type": "optional", "emailAddress": { "name": "李 芳蘭", "address": "foran.lee@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "中嶋 陽介", "address": "yosuke.nakajima@contoso.com" } },
        { "type": "optional", "emailAddress": { "name": "三田村 啓", "address": "kei.mitamura@contoso.com" } },
        { "type": "optional", "emailAddress": { "name": "宮野 春香", "address": "haruka.miyano@contoso.com" } }
      ],
      "start": { "dateTime": "2025-10-13T10:00:00", "timeZone": "Tokyo Standard Time" },
      "end":   { "dateTime": "2025-10-13T11:30:00", "timeZone": "Tokyo Standard Time" },
      "location": { "displayName": "Microsoft Teams（PMO_定例）" },
      "isOnlineMeeting": true,
      "onlineMeetingProvider": "teamsForBusiness",
      "onlineMeeting": {
        "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3apmo-regular%40thread.tacv2/..."
      },
      "categories": [ "PMO", "定例" },
      "transactionId": "a1b2c3d4-pmo-20251013"
    },
    {
      "id": "evt-risk-20251016",
      "subject": "リスク対策検討ミーティング",
      "bodyPreview": "自治体Bデータ遅延／SOC監査／リスクレポート自動化",
      "body": {
        "contentType": "html",
        "content": "<p>アジェンダ：自治体Bデータ遅延対応（緊急度：中→高）、SOC監査の指摘2件の対応、Power BIによるリスクレポート自動化。</p>"
      },
      "organizer": {
        "emailAddress": { "name": "石田 智久（PM）", "address": "tomohisa.ishida@contoso.com" }
      },
      "attendees": [
        { "type": "required", "emailAddress": { "name": "西川 麻衣（品質PM）", "address": "mai.nishikawa@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "中嶋 陽介", "address": "yosuke.nakajima@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "森岡 翔", "address": "sho.morioka@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "竹田 隆", "address": "takashi.takeda@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "松下 翔太", "address": "shota.matsushita@contoso.com" } }
      ],
      "start": { "dateTime": "2025-10-16T14:00:00", "timeZone": "Tokyo Standard Time" },
      "end":   { "dateTime": "2025-10-16T15:00:00", "timeZone": "Tokyo Standard Time" },
      "location": { "displayName": "Microsoft Teams（PMO_Risk）" },
      "isOnlineMeeting": true,
      "onlineMeetingProvider": "teamsForBusiness",
      "onlineMeeting": {
        "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3apmo-risk%40thread.tacv2/..."
      },
      "categories": [ "リスク", "PMO" ],
      "transactionId": "a1b2c3d4-risk-20251016"
    },
    {
      "id": "evt-allhands-20251022",
      "subject": "全体推進会議",
      "bodyPreview": "10月月次報告・各チーム進捗・リスク・コスト見通し・UXデモ",
      "body": {
        "contentType": "html",
        "content": "<p>10/22 全体推進会議。各チーム進捗・月次報告・リスク/コスト見通し、UXデモ共有。</p>"
      },
      "organizer": {
        "emailAddress": { "name": "石田 智久（PM）", "address": "tomohisa.ishida@contoso.com" }
      },
      "attendees": [
        { "type": "required", "emailAddress": { "name": "各チームリーダー", "address": "leaders@contoso.com" } },
        { "type": "optional", "emailAddress": { "name": "品質PM（西川）", "address": "mai.nishikawa@contoso.com" } }
      ],
      "start": { "dateTime": "2025-10-22T10:00:00", "timeZone": "Tokyo Standard Time" },
      "end":   { "dateTime": "2025-10-22T11:30:00", "timeZone": "Tokyo Standard Time" },
      "location": { "displayName": "Microsoft Teams（全体推進会議）" },
      "isOnlineMeeting": true,
      "onlineMeetingProvider": "teamsForBusiness",
      "onlineMeeting": {
        "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3aallhands%40thread.tacv2/..."
      },
      "categories": [ "全体会議" ],
      "transactionId": "a1b2c3d4-allhands-20251022"
    },
    {
      "id": "evt-deadline-20251017",
      "subject": "（締切）月次報告書ドラフト提出",
      "bodyPreview": "原口→提出／石田・西川→確認。10/22資料へ反映。",
      "body": {
        "contentType": "html",
        "content": "<p>原口：ドラフト提出。石田/西川：確認。10/22全体推進会議資料に反映。</p>"
      },
      "organizer": {
        "emailAddress": { "name": "原口 由香（成果物統括）", "address": "yuka.haraguchi@contoso.com" }
      },
      "attendees": [
        { "type": "optional", "emailAddress": { "name": "石田 智久（PM）", "address": "tomohisa.ishida@contoso.com" } },
        { "type": "optional", "emailAddress": { "name": "西川 麻衣（品質PM）", "address": "mai.nishikawa@contoso.com" } }
      ],
      "isAllDay": true,
      "start": { "dateTime": "2025-10-17", "timeZone": "Tokyo Standard Time" },
      "end":   { "dateTime": "2025-10-18", "timeZone": "Tokyo Standard Time" },
      "reminderMinutesBeforeStart": 60,
      "location": { "displayName": "リマインダー" },
      "categories": [ "締切", "PMO" ],
      "transactionId": "a1b2c3d4-deadline-20251017"
    }
  ]
}

```

## 📘 第2週（10月20日週）

### 会議③：全体推進会議（行政・NEC合同）

```
日時： 2025年10月22日（水）14:00〜16:00
場所： オンライン（Teams）
出席者：
行政事務局3名、NEC PMO 10名、各チームリーダー（AI／基盤／運用／UX）

■ 議題

10月進捗報告（全体進行率68％）

PoC進行計画（第2フェーズ）

リスク・コスト見通し

顧客側要望事項（分析レポート頻度・ダッシュボード機能追加）

■ 議事概要

進捗報告

データ基盤：交通系データの連携完了、宿泊データは11月へずれ込み。

AI分析：モデル精度改善（RMSE 0.15）、SHAP分析の自治体B事例を提示。

UX：利用者アンケート回答率72％、UI改善案（ナビ機能）検討中。

PoC第2フェーズ

11月〜1月実施予定。参加自治体を7→9へ拡大。

NEC側：AIモデル改修＋ダッシュボード統合（中谷・相沢担当）。

コスト見通し

クラウドコストは9月比＋5％。竹田が10月補正見積を提示。

行政側了承済み、11月請求に反映。

要望事項

行政側より「宿泊需要予測レポート」を月次から隔週配信へ要望。

藤原チームに分析サイクル短縮を指示。

■ 決定事項

PoC第2フェーズ実施期間：11/1〜1/31

ダッシュボード機能追加（ナビ・フィルタ強化）→ 12月末実装

次回合同会議：11月26日（水）14:00

■ ToDo
担当	内容	期限
石田	議事録・報告書提出（行政側へ）	10/24
藤原	レポート更新サイクル短縮案	10/30
相沢	ダッシュボード機能要件まとめ	10/27
竹田	予算補正資料提出	10/25
西川	品質計画書更新（PoC第2期版）	10/28
```

### 会議④：成果物レビュー会議（PMO＋品質チーム）

```
日時： 2025年10月24日（金）13:00〜14:30
出席者： 西川、原口、石田、宮野、李、望月（QAリーダー）

■ 議題

データ基盤API v2.0設計書レビュー

AIモデル精度報告書レビュー

ドキュメント版管理ルール更新

■ 議事概要

API v2.0設計書

REST構成→GraphQLハイブリッド案が提示。

認証部分に不備（トークン更新手順）あり。再提出依頼。

AIモデル精度報告書

本田作成版を確認。グラフ体裁修正指示。

顧客向け資料は簡略版＋技術付録形式へ変更。

版管理ルール

Teams共有→SharePointへの正式移行を決定。

原口がフォルダ構造案を10/28に提示予定。

■ 決定事項

API設計書再提出期限：10月29日（水）

モデル報告書提出：10月28日（火）

成果物格納先：SharePoint正式運用へ移行

■ ToDo
担当	内容	期限
原口	SharePointフォルダ構成案提示	10/28
西川	API設計書レビュー追記	10/29
宮野	成果物管理マニュアル更新	10/30
```
### teamsでの会話内容

```
📰 一般（General）

📢 石田 智久（統括PM）

【全体共有】10月第4週の連絡事項

・全体進捗報告資料（10月度）を共有しました。
・10/22の**全体推進会議（行政合同）**で承認されたPoC第2フェーズ計画について、各チームでのタスク登録をお願いします。
・会議資料・議事録は以下に格納済みです。
📎 SharePoint > 会議資料 > 2025_10_22_合同会議

@西川麻衣 さん、品質計画書の第2期版、10/28までにドラフト共有をお願いします。

💬 西川 麻衣（品質PM）

承知しました。第2期版のテンプレートは前回と同様のフォーマットで進めます。
10/26までに初稿をこちらのチャネルで共有予定です。

📎 原口 由香（成果物統括）

SharePoint移行に向けた**フォルダ構成案（ドラフト）**をアップしました。

📄 成果物管理構成案_v1.0.xlsx

各チームからの格納ルール意見を募集中です。@宮野 さん、ドキュメント管理マニュアルの更新版との整合も確認お願いします。

🗣️ 石田 智久（統括PM）

ありがとうございます。
SharePoint運用ルールは10/30のPMOレビュー会議で確定します。
各チーム、確認・コメントを10/28までにお願いします。

📅 定例・進捗報告

🗓️ 松下 翔太（スケジュール管理）

【進捗サマリ／10月20日週】

全体進行率：68％ → 71％へ上昇見込み

PoC第2フェーズ準備進行中（データ連携完了率 80％）

次週（10/27週）はAI・UX両チームで統合テスト開始予定

@藤原 さん、AIモデル更新スケジュールの確定版、こちらに共有お願いできますか？

🤖 藤原 慎（AI分析リーダー）

はい、こちらになります👇

AIモデル更新スケジュール（PoC第2期）

10/25〜10/29：データ再学習（交通・宿泊統合版）

10/30：RMSE検証・SHAP再解析

10/31：行政側レビュー資料作成（本田担当）

10/27に暫定モデルを共有予定です。

🧩 相沢 美里（UX・顧客連携リーダー）

@藤原 さん
SHAP解析結果の出力形式、UI側でも可視化したいので、JSON形式での出力にしてもらえますか？
ダッシュボード連携の部分（ナビ・フィルタ強化）を私と中谷で実装中です。

🤖 藤原 慎（AI分析リーダー）

承知しました。JSON出力対応は10/26夜に反映します。
UI側での描画用サンプルデータも合わせて共有します。

💰 竹田 隆（コスト管理）

【報告】
10月補正見積を本日行政側に提出済みです。
クラウドコスト上昇分（＋5％）も了承済み。
11月請求に反映されます。

📋 西川 麻衣（品質PM）

品質計画書（PoC第2期）ドラフトをアップしました。

📎 品質計画書_PoC2期draft_20251025.docx

@石田 さん、@原口 さん、レビューお願いします。
次回のPMO＋品質チーム会議（10/24）で確定予定です。

💬 技術・課題共有

💬 宮野 翔（QAチーム）

API v2.0のレビュー結果を共有します。

GraphQLハイブリッド構成：可

認証処理：トークン更新手順に不備あり（要修正）

バージョン管理：リクエストスキーマにschemaVersionを追加推奨

@中谷 さん、修正版の設計書は10/29提出で問題ないでしょうか？

🧑‍💻 中谷 悠（基盤チーム）

@宮野 さん
承知しました。修正対応中です。
schemaVersionはリクエストヘッダで対応予定。
明日（10/26）テスト環境で認証確認を行います。

💬 望月 亮（QAリーダー）

補足します。
テスト観点では、GraphQLリクエストのパラメータ検証ロジックを追加します。
QAチーム内で共通テストケースを10/27に共有予定です。

💬 本田 一樹（AIチーム）

モデル精度報告書（ドラフト）を更新しました。

📄 Model_Accuracy_Report_v2.1.pdf

RMSE: 0.152 → 0.147 に改善。
SHAP可視化グラフを刷新し、自治体Bの事例を追記しています。
@西川 さん、体裁確認お願いします。

📊 西川 麻衣（品質PM）

確認しました。
グラフ凡例の日本語化をお願いします。
併せて、顧客向け報告書は「概要＋付録」形式で提出予定なので、概要版は10/28までに共有ください。

💬 相沢 美里（UX・顧客連携リーダー）

@本田 さん、SHAP結果の可視化部分、UIデザインに反映しました。
ナビ機能のプロトタイプを今週中に共有予定です。

📎 Dashboard_NaviPrototype_v0.3.mp4

✅ 石田 智久（統括PM）

各担当ありがとうございます。
この週のタスク進捗をまとめると以下になります：

PoC第2期スケジュール確定 ✅

SharePoint運用開始準備中（原口・宮野）🔄

モデル精度報告書：最終化中（本田・西川）🔄

ダッシュボード改修：UI設計完了、実装中（相沢・中谷）🔄

次回：全体進捗レビュー 10/28（火）午前10:00〜
進捗更新をこのチャネルに投稿してください。

🔚（週末まとめ投稿）

🗓️ 松下 翔太（スケジュール管理）

【週末報告まとめ／10月25日時点】

全体進行率：71％

PoC2期タスク登録完了

成果物レビュー進行中（API・モデル）

SharePoint運用開始準備：原口チーム完了報告

来週から統合テスト移行に入ります。
各チーム、テスト観点の再確認をお願いします。
```
```
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('team-nec-kanko-dx')/channels/messages",
  "team": {
    "id": "team-nec-kanko-dx",
    "displayName": "NEC観光DX基盤構築プロジェクト（全体）"
  },
  "channels": [
    {
      "id": "19:general@thread.tacv2",
      "displayName": "📰 一般（General）",
      "messages": [
        {
          "id": "msg-gen-001",
          "replyToId": null,
          "createdDateTime": "2025-10-22T09:30:00Z",
          "lastModifiedDateTime": "2025-10-22T09:30:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "【全体共有】10月第4週の連絡事項",
          "from": {
            "user": {
              "id": "u-ishida",
              "displayName": "石田 智久（統括PM）",
              "userPrincipalName": "tomohisa.ishida@contoso.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<div>【全体共有】10月第4週の連絡事項</div><div><br/></div><div>・全体進捗報告資料（10月度）を共有しました。</div><div>・10/22の<strong>全体推進会議（行政合同）</strong>で承認されたPoC第2フェーズ計画について、各チームでのタスク登録をお願いします。</div><div>・会議資料・議事録は以下に格納済みです。</div><div>📎 <a href=\"https://sharepoint.contoso.com/pmo/meetings/20251022\">SharePoint &gt; 会議資料 &gt; 2025_10_22_合同会議</a></div><div><br/></div><div><at id=\"0\">西川 麻衣</at> さん、品質計画書の第2期版、10/28までにドラフト共有をお願いします。</div>"
          },
          "mentions": [
            {
              "id": 0,
              "mentionText": "西川 麻衣",
              "mentioned": {
                "user": {
                  "id": "u-nishikawa",
                  "displayName": "西川 麻衣（品質PM）",
                  "userPrincipalName": "mai.nishikawa@contoso.com"
                }
              }
            }
          ],
          "attachments": [
            {
              "id": "att-001",
              "contentType": "reference",
              "name": "2025_10_22_合同会議",
              "contentUrl": "https://sharepoint.contoso.com/pmo/meetings/20251022"
            }
          ],
          "replies": [
            {
              "id": "msg-gen-001-r1",
              "replyToId": "msg-gen-001",
              "createdDateTime": "2025-10-22T10:05:00Z",
              "lastModifiedDateTime": "2025-10-22T10:05:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-nishikawa",
                  "displayName": "西川 麻衣（品質PM）",
                  "userPrincipalName": "mai.nishikawa@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<div>承知しました。第2期版のテンプレートは前回と同様のフォーマットで進めます。10/26までに初稿をこちらのチャネルで共有予定です。</div>"
              }
            }
          ]
        },
        {
          "id": "msg-gen-002",
          "replyToId": null,
          "createdDateTime": "2025-10-25T01:40:00Z",
          "lastModifiedDateTime": "2025-10-25T01:40:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "SharePoint移行：フォルダ構成案（ドラフト）共有",
          "from": {
            "user": {
              "id": "u-haraguchi",
              "displayName": "原口 由香（成果物統括）",
              "userPrincipalName": "yuka.haraguchi@contoso.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<div>SharePoint移行に向けた<strong>フォルダ構成案（ドラフト）</strong>をアップしました。</div><div><br/></div><div>📄 成果物管理構成案_v1.0.xlsx</div><div><br/></div><div>各チームからの格納ルール意見を募集中です。<at id=\"0\">宮野 翔</at> さん、ドキュメント管理マニュアルの更新版との整合も確認お願いします。</div>"
          },
          "mentions": [
            {
              "id": 0,
              "mentionText": "宮野 翔",
              "mentioned": {
                "user": {
                  "id": "u-miyano",
                  "displayName": "宮野 翔（QA）",
                  "userPrincipalName": "sho.miyano@contoso.com"
                }
              }
            }
          ],
          "attachments": [
            {
              "id": "att-002",
              "contentType": "reference",
              "name": "成果物管理構成案_v1.0.xlsx",
              "contentUrl": "https://sharepoint.contoso.com/pmo/docs/成果物管理構成案_v1.0.xlsx"
            }
          ],
          "replies": [
            {
              "id": "msg-gen-002-r1",
              "replyToId": "msg-gen-002",
              "createdDateTime": "2025-10-25T02:05:00Z",
              "lastModifiedDateTime": "2025-10-25T02:05:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-ishida",
                  "displayName": "石田 智久（統括PM）",
                  "userPrincipalName": "tomohisa.ishida@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<div>ありがとうございます。SharePoint運用ルールは<strong>10/30のPMOレビュー会議</strong>で確定します。各チーム、確認・コメントを<strong>10/28</strong>までにお願いします。</div>"
              }
            }
          ]
        }
      ]
    },
    {
      "id": "19:progress@thread.tacv2",
      "displayName": "📅 定例・進捗報告",
      "messages": [
        {
          "id": "msg-prog-001",
          "replyToId": null,
          "createdDateTime": "2025-10-23T00:30:00Z",
          "lastModifiedDateTime": "2025-10-23T00:30:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "【進捗サマリ／10月20日週】",
          "from": {
            "user": {
              "id": "u-matsushita",
              "displayName": "松下 翔太（スケジュール管理）",
              "userPrincipalName": "shota.matsushita@contoso.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<div>【進捗サマリ／10月20日週】</div><div><br/></div><div>・全体進行率：68％ → 71％へ上昇見込み</div><div>・PoC第2フェーズ準備進行中（データ連携完了率 80％）</div><div>・次週（10/27週）はAI・UX両チームで<strong>統合テスト開始</strong>予定</div><div><br/></div><div><at id=\"0\">藤原 慎</at> さん、AIモデル更新スケジュールの確定版、こちらに共有お願いできますか？</div>"
          },
          "mentions": [
            {
              "id": 0,
              "mentionText": "藤原 慎",
              "mentioned": {
                "user": {
                  "id": "u-fujiwara",
                  "displayName": "藤原 慎（AI分析リーダー）",
                  "userPrincipalName": "makoto.fujiwara@contoso.com"
                }
              }
            }
          ],
          "replies": [
            {
              "id": "msg-prog-001-r1",
              "replyToId": "msg-prog-001",
              "createdDateTime": "2025-10-23T01:00:00Z",
              "lastModifiedDateTime": "2025-10-23T01:00:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-fujiwara",
                  "displayName": "藤原 慎（AI分析リーダー）",
                  "userPrincipalName": "makoto.fujiwara@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<div>はい、こちらになります👇</div><div><br/></div><div><strong>AIモデル更新スケジュール（PoC第2期）</strong></div><div>・10/25〜10/29：データ再学習（交通・宿泊統合版）</div><div>・10/30：RMSE検証・SHAP再解析</div><div>・10/31：行政側レビュー資料作成（本田担当）</div><div><br/></div><div>10/27に暫定モデルを共有予定です。</div>"
              }
            },
            {
              "id": "msg-prog-001-r2",
              "replyToId": "msg-prog-001",
              "createdDateTime": "2025-10-23T01:12:00Z",
              "lastModifiedDateTime": "2025-10-23T01:12:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-aizawa",
                  "displayName": "相沢 美里（UX・顧客連携リーダー）",
                  "userPrincipalName": "misato.aizawa@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<div><at id=\"0\">藤原 慎</at> さん</div><div>SHAP解析結果の出力形式、UI側でも可視化したいので、<strong>JSON形式</strong>での出力にしてもらえますか？</div><div>ダッシュボード連携の部分（ナビ・フィルタ強化）を私と中谷で実装中です。</div>"
              },
              "mentions": [
                {
                  "id": 0,
                  "mentionText": "藤原 慎",
                  "mentioned": {
                    "user": {
                      "id": "u-fujiwara",
                      "displayName": "藤原 慎（AI分析リーダー）",
                      "userPrincipalName": "makoto.fujiwara@contoso.com"
                    }
                  }
                }
              ]
            },
            {
              "id": "msg-prog-001-r3",
              "replyToId": "msg-prog-001",
              "createdDateTime": "2025-10-23T01:25:00Z",
              "lastModifiedDateTime": "2025-10-23T01:25:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-fujiwara",
                  "displayName": "藤原 慎（AI分析リーダー）",
                  "userPrincipalName": "makoto.fujiwara@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<div>承知しました。JSON出力対応は<strong>10/26夜</strong>に反映します。UI側での描画用サンプルデータも合わせて共有します。</div>"
              }
            },
            {
              "id": "msg-prog-001-r4",
              "replyToId": "msg-prog-001",
              "createdDateTime": "2025-10-23T02:10:00Z",
              "lastModifiedDateTime": "2025-10-23T02:10:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-takeda",
                  "displayName": "竹田 隆（コスト管理）",
                  "userPrincipalName": "takashi.takeda@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<div>【報告】10月補正見積を本日行政側に提出済みです。クラウドコスト上昇分（＋5％）も了承済み。11月請求に反映されます。</div>"
              }
            },
            {
              "id": "msg-prog-001-r5",
              "replyToId": "msg-prog-001",
              "createdDateTime": "2025-10-25T03:20:00Z",
              "lastModifiedDateTime": "2025-10-25T03:20:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-nishikawa",
                  "displayName": "西川 麻衣（品質PM）",
                  "userPrincipalName": "mai.nishikawa@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<div>品質計画書（PoC第2期）ドラフトをアップしました。</div><div><br/></div><div>📎 品質計画書_PoC2期draft_20251025.docx</div><div><br/></div><div><at id=\"0\">石田 智久</at> さん、<at id=\"1\">原口 由香</at> さん、レビューお願いします。次回のPMO＋品質チーム会議（10/24）で確定予定です。</div>"
              },
              "mentions": [
                {
                  "id": 0,
                  "mentionText": "石田 智久",
                  "mentioned": {
                    "user": {
                      "id": "u-ishida",
                      "displayName": "石田 智久（統括PM）",
                      "userPrincipalName": "tomohisa.ishida@contoso.com"
                    }
                  }
                },
                {
                  "id": 1,
                  "mentionText": "原口 由香",
                  "mentioned": {
                    "user": {
                      "id": "u-haraguchi",
                      "displayName": "原口 由香（成果物統括）",
                      "userPrincipalName": "yuka.haraguchi@contoso.com"
                    }
                  }
                }
              ],
              "attachments": [
                {
                  "id": "att-003",
                  "contentType": "reference",
                  "name": "品質計画書_PoC2期draft_20251025.docx",
                  "contentUrl": "https://sharepoint.contoso.com/pmo/quality/品質計画書_PoC2期draft_20251025.docx"
                }
              ]
            }
          ]
        },
        {
          "id": "msg-prog-002",
          "replyToId": null,
          "createdDateTime": "2025-10-25T08:00:00Z",
          "lastModifiedDateTime": "2025-10-25T08:00:00Z",
          "messageType": "message",
          "subject": "【週末報告まとめ／10月25日時点】",
          "from": {
            "user": {
              "id": "u-matsushita",
              "displayName": "松下 翔太（スケジュール管理）",
              "userPrincipalName": "shota.matsushita@contoso.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<div>【週末報告まとめ／10月25日時点】</div><div><br/></div><div>・全体進行率：71％</div><div>・PoC2期タスク登録完了</div><div>・成果物レビュー進行中（API・モデル）</div><div>・SharePoint運用開始準備：原口チーム完了報告</div><div><br/></div><div>来週から統合テスト移行に入ります。各チーム、テスト観点の再確認をお願いします。</div>"
          },
          "replies": []
        }
      ]
    },
    {
      "id": "19:tech-issues@thread.tacv2",
      "displayName": "💬 技術・課題共有",
      "messages": [
        {
          "id": "msg-tech-001",
          "replyToId": null,
          "createdDateTime": "2025-10-24T04:10:00Z",
          "lastModifiedDateTime": "2025-10-24T04:10:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "API v2.0レビュー結果共有",
          "from": {
            "user": {
              "id": "u-miyano",
              "displayName": "宮野 翔（QAチーム）",
              "userPrincipalName": "sho.miyano@contoso.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<div>API v2.0のレビュー結果を共有します。</div><div><br/></div><div>・GraphQLハイブリッド構成：可</div><div>・認証処理：トークン更新手順に不備あり（要修正）</div><div>・バージョン管理：リクエストスキーマに<code>schemaVersion</code>を追加推奨</div><div><br/></div><div><at id=\"0\">中谷 悠</at> さん、修正版の設計書は<strong>10/29</strong>提出で問題ないでしょうか？</div>"
          },
          "mentions": [
            {
              "id": 0,
              "mentionText": "中谷 悠",
              "mentioned": {
                "user": {
                  "id": "u-nakatani",
                  "displayName": "中谷 悠（基盤チーム）",
                  "userPrincipalName": "haruka.nakatani@contoso.com"
                }
              }
            }
          ],
          "replies": [
            {
              "id": "msg-tech-001-r1",
              "replyToId": "msg-tech-001",
              "createdDateTime": "2025-10-24T04:35:00Z",
              "lastModifiedDateTime": "2025-10-24T04:35:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-nakatani",
                  "displayName": "中谷 悠（基盤チーム）",
                  "userPrincipalName": "haruka.nakatani@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<div><at id=\"0\">宮野 翔</at> さん</div><div>承知しました。修正対応中です。<code>schemaVersion</code>は<strong>リクエストヘッダ</strong>で対応予定。明日（10/26）テスト環境で認証確認を行います。</div>"
              },
              "mentions": [
                {
                  "id": 0,
                  "mentionText": "宮野 翔",
                  "mentioned": {
                    "user": {
                      "id": "u-miyano",
                      "displayName": "宮野 翔（QAチーム）",
                      "userPrincipalName": "sho.miyano@contoso.com"
                    }
                  }
                }
              ]
            },
            {
              "id": "msg-tech-001-r2",
              "replyToId": "msg-tech-001",
              "createdDateTime": "2025-10-24T05:00:00Z",
              "lastModifiedDateTime": "2025-10-24T05:00:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-mochizuki",
                  "displayName": "望月 亮（QAリーダー）",
                  "userPrincipalName": "ryo.mochizuki@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<div>補足します。テスト観点では、GraphQLリクエストの<strong>パラメータ検証ロジック</strong>を追加します。QAチーム内で共通テストケースを<strong>10/27</strong>に共有予定です。</div>"
              }
            }
          ]
        },
        {
          "id": "msg-tech-002",
          "replyToId": null,
          "createdDateTime": "2025-10-24T06:10:00Z",
          "lastModifiedDateTime": "2025-10-24T06:10:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "モデル精度報告書（ドラフト）更新",
          "from": {
            "user": {
              "id": "u-honda",
              "displayName": "本田 一樹（AIチーム）",
              "userPrincipalName": "kazuki.honda@contoso.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<div>モデル精度報告書（ドラフト）を更新しました。</div><div><br/></div><div>📄 Model_Accuracy_Report_v2.1.pdf</div><div><br/></div><div>RMSE: 0.152 → <strong>0.147</strong> に改善。SHAP可視化グラフを刷新し、自治体Bの事例を追記しています。<at id=\"0\">西川 麻衣</at> さん、体裁確認お願いします。</div>"
          },
          "mentions": [
            {
              "id": 0,
              "mentionText": "西川 麻衣",
              "mentioned": {
                "user": {
                  "id": "u-nishikawa",
                  "displayName": "西川 麻衣（品質PM）",
                  "userPrincipalName": "mai.nishikawa@contoso.com"
                }
              }
            }
          ],
          "attachments": [
            {
              "id": "att-004",
              "contentType": "reference",
              "name": "Model_Accuracy_Report_v2.1.pdf",
              "contentUrl": "https://sharepoint.contoso.com/ai/reports/Model_Accuracy_Report_v2.1.pdf"
            }
          ],
          "replies": [
            {
              "id": "msg-tech-002-r1",
              "replyToId": "msg-tech-002",
              "createdDateTime": "2025-10-24T06:28:00Z",
              "lastModifiedDateTime": "2025-10-24T06:28:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-nishikawa",
                  "displayName": "西川 麻衣（品質PM）",
                  "userPrincipalName": "mai.nishikawa@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<div>確認しました。グラフ凡例の日本語化をお願いします。併せて、顧客向け報告書は<strong>「概要＋付録」</strong>形式で提出予定なので、概要版は<strong>10/28</strong>までに共有ください。</div>"
              }
            },
            {
              "id": "msg-tech-002-r2",
              "replyToId": "msg-tech-002",
              "createdDateTime": "2025-10-24T07:05:00Z",
              "lastModifiedDateTime": "2025-10-24T07:05:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-aizawa",
                  "displayName": "相沢 美里（UX・顧客連携リーダー）",
                  "userPrincipalName": "misato.aizawa@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<div><at id=\"0\">本田 一樹</at> さん、SHAP結果の可視化部分、UIデザインに反映しました。ナビ機能のプロトタイプを今週中に共有予定です。</div><div>📎 Dashboard_NaviPrototype_v0.3.mp4</div>"
              },
              "mentions": [
                {
                  "id": 0,
                  "mentionText": "本田 一樹",
                  "mentioned": {
                    "user": {
                      "id": "u-honda",
                      "displayName": "本田 一樹（AIチーム）",
                      "userPrincipalName": "kazuki.honda@contoso.com"
                    }
                  }
                }
              ],
              "attachments": [
                {
                  "id": "att-005",
                  "contentType": "reference",
                  "name": "Dashboard_NaviPrototype_v0.3.mp4",
                  "contentUrl": "https://sharepoint.contoso.com/ux/prototype/Dashboard_NaviPrototype_v0.3.mp4"
                }
              ]
            }
          ]
        },
        {
          "id": "msg-tech-003",
          "replyToId": null,
          "createdDateTime": "2025-10-24T08:30:00Z",
          "lastModifiedDateTime": "2025-10-24T08:30:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "今週タスク進捗まとめ",
          "from": {
            "user": {
              "id": "u-ishida",
              "displayName": "石田 智久（統括PM）",
              "userPrincipalName": "tomohisa.ishida@contoso.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<div>各担当ありがとうございます。この週のタスク進捗をまとめると以下になります：</div><div><br/></div><div>・PoC第2期スケジュール確定 ✅</div><div>・SharePoint運用開始準備中（原口・宮野）🔄</div><div>・モデル精度報告書：最終化中（本田・西川）🔄</div><div>・ダッシュボード改修：UI設計完了、実装中（相沢・中谷）🔄</div><div><br/></div><div>次回：<strong>全体進捗レビュー 10/28（火）午前10:00〜</strong><br/>進捗更新をこのチャネルに投稿してください。</div>"
          },
          "replies": []
        }
      ]
    }
  ]
}

```
### outlook予定表第二週

```
✅ 想定されるOutlook予定（抜粋）

PMO定例会議

日時: 2025-10-13 (月) 10:00–11:30

参加: 石田（主催）、西川、森岡、松下、竹田、原口、李、中嶋、三田村、宮野

開催: Microsoft Teams（PMO_定例）

メモ: 当日の議題共有・リスク#12・月次報告・10/22全体推進会議準備

リスク対策検討ミーティング

日時: 2025-10-16 (木) 14:00–15:00

参加: 石田、西川、中嶋、森岡、竹田、松下

開催: Microsoft Teams（PMO_Risk）

メモ: 自治体Bデータ遅延対応（緊急度：中→高）、SOC監査対応、リスクレポート自動化

全体推進会議

日時: 2025-10-22 (水) 10:00–11:30

参加: PMO＋各チームリーダー（約15名）

開催: Microsoft Teams（全体推進会議）

メモ: 10月分月次報告／各チーム進捗／リスク・コスト見通し／UXデモ共有

月次報告書 提出締切（ドラフト）

形式: 終日予定（リマインダー 09:00）

日付: 2025-10-17 (金)

参加: 原口（担当）、石田／西川（確認）

メモ: ドラフト提出・10/22向け資料反映
```

```json
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#me/calendarView",
  "value": [
    {
      "id": "evt-pmo-20251013",
      "subject": "PMO定例会議",
      "bodyPreview": "各チーム進捗／リスク#12／月次報告／10/22全体推進会議準備",
      "body": {
        "contentType": "html",
        "content": "<p>PMO定例。議題：各チーム進捗、リスク#12（自治体Bデータ遅延）、10月分月次報告、10/22全体推進会議準備。</p>"
      },
      "organizer": {
        "emailAddress": { "name": "石田 智久（PM）", "address": "tomohisa.ishida@contoso.com" }
      },
      "attendees": [
        { "type": "required", "emailAddress": { "name": "西川 麻衣（品質PM）", "address": "mai.nishikawa@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "森岡 翔", "address": "sho.morioka@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "松下 翔太", "address": "shota.matsushita@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "竹田 隆", "address": "takashi.takeda@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "原口 由香", "address": "yuka.haraguchi@contoso.com" } },
        { "type": "optional", "emailAddress": { "name": "李 芳蘭", "address": "foran.lee@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "中嶋 陽介", "address": "yosuke.nakajima@contoso.com" } },
        { "type": "optional", "emailAddress": { "name": "三田村 啓", "address": "kei.mitamura@contoso.com" } },
        { "type": "optional", "emailAddress": { "name": "宮野 春香", "address": "haruka.miyano@contoso.com" } }
      ],
      "start": { "dateTime": "2025-10-13T10:00:00", "timeZone": "Tokyo Standard Time" },
      "end":   { "dateTime": "2025-10-13T11:30:00", "timeZone": "Tokyo Standard Time" },
      "location": { "displayName": "Microsoft Teams（PMO_定例）" },
      "isOnlineMeeting": true,
      "onlineMeetingProvider": "teamsForBusiness",
      "onlineMeeting": {
        "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3apmo-regular%40thread.tacv2/..."
      },
      "categories": [ "PMO", "定例" },
      "transactionId": "a1b2c3d4-pmo-20251013"
    },
    {
      "id": "evt-risk-20251016",
      "subject": "リスク対策検討ミーティング",
      "bodyPreview": "自治体Bデータ遅延／SOC監査／リスクレポート自動化",
      "body": {
        "contentType": "html",
        "content": "<p>アジェンダ：自治体Bデータ遅延対応（緊急度：中→高）、SOC監査の指摘2件の対応、Power BIによるリスクレポート自動化。</p>"
      },
      "organizer": {
        "emailAddress": { "name": "石田 智久（PM）", "address": "tomohisa.ishida@contoso.com" }
      },
      "attendees": [
        { "type": "required", "emailAddress": { "name": "西川 麻衣（品質PM）", "address": "mai.nishikawa@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "中嶋 陽介", "address": "yosuke.nakajima@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "森岡 翔", "address": "sho.morioka@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "竹田 隆", "address": "takashi.takeda@contoso.com" } },
        { "type": "required", "emailAddress": { "name": "松下 翔太", "address": "shota.matsushita@contoso.com" } }
      ],
      "start": { "dateTime": "2025-10-16T14:00:00", "timeZone": "Tokyo Standard Time" },
      "end":   { "dateTime": "2025-10-16T15:00:00", "timeZone": "Tokyo Standard Time" },
      "location": { "displayName": "Microsoft Teams（PMO_Risk）" },
      "isOnlineMeeting": true,
      "onlineMeetingProvider": "teamsForBusiness",
      "onlineMeeting": {
        "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3apmo-risk%40thread.tacv2/..."
      },
      "categories": [ "リスク", "PMO" ],
      "transactionId": "a1b2c3d4-risk-20251016"
    },
    {
      "id": "evt-allhands-20251022",
      "subject": "全体推進会議",
      "bodyPreview": "10月月次報告・各チーム進捗・リスク・コスト見通し・UXデモ",
      "body": {
        "contentType": "html",
        "content": "<p>10/22 全体推進会議。各チーム進捗・月次報告・リスク/コスト見通し、UXデモ共有。</p>"
      },
      "organizer": {
        "emailAddress": { "name": "石田 智久（PM）", "address": "tomohisa.ishida@contoso.com" }
      },
      "attendees": [
        { "type": "required", "emailAddress": { "name": "各チームリーダー", "address": "leaders@contoso.com" } },
        { "type": "optional", "emailAddress": { "name": "品質PM（西川）", "address": "mai.nishikawa@contoso.com" } }
      ],
      "start": { "dateTime": "2025-10-22T10:00:00", "timeZone": "Tokyo Standard Time" },
      "end":   { "dateTime": "2025-10-22T11:30:00", "timeZone": "Tokyo Standard Time" },
      "location": { "displayName": "Microsoft Teams（全体推進会議）" },
      "isOnlineMeeting": true,
      "onlineMeetingProvider": "teamsForBusiness",
      "onlineMeeting": {
        "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3aallhands%40thread.tacv2/..."
      },
      "categories": [ "全体会議" ],
      "transactionId": "a1b2c3d4-allhands-20251022"
    },
    {
      "id": "evt-deadline-20251017",
      "subject": "（締切）月次報告書ドラフト提出",
      "bodyPreview": "原口→提出／石田・西川→確認。10/22資料へ反映。",
      "body": {
        "contentType": "html",
        "content": "<p>原口：ドラフト提出。石田/西川：確認。10/22全体推進会議資料に反映。</p>"
      },
      "organizer": {
        "emailAddress": { "name": "原口 由香（成果物統括）", "address": "yuka.haraguchi@contoso.com" }
      },
      "attendees": [
        { "type": "optional", "emailAddress": { "name": "石田 智久（PM）", "address": "tomohisa.ishida@contoso.com" } },
        { "type": "optional", "emailAddress": { "name": "西川 麻衣（品質PM）", "address": "mai.nishikawa@contoso.com" } }
      ],
      "isAllDay": true,
      "start": { "dateTime": "2025-10-17", "timeZone": "Tokyo Standard Time" },
      "end":   { "dateTime": "2025-10-18", "timeZone": "Tokyo Standard Time" },
      "reminderMinutesBeforeStart": 60,
      "location": { "displayName": "リマインダー" },
      "categories": [ "締切", "PMO" ],
      "transactionId": "a1b2c3d4-deadline-20251017"
    }
  ]
}
```
