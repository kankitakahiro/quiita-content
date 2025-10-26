---
title: ハッカソンでシステム検証のためのPJ例を作成する。
tags:
  - ハッカソン
  - 生成AI
private: true
updated_at: '2025-10-27T02:32:46+09:00'
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
- [② データ基盤構築チーム（三宅チーム）](#-データ基盤構築チーム三宅チーム-1)
  - [📘 第1週（10月13日週）](#-第1週10月13日週-1)
    - [会議①：データ基盤チーム週次定例（第3週）](#会議データ基盤チーム週次定例第3週)
    - [🗓 会議②：API・匿名化方式 技術分科会](#-会議api匿名化方式-技術分科会)
  - [teamsでの会話内容](#teamsでの会話内容-2)
    - [outlook予定表第一週](#outlook予定表第一週-1)
  - [📘 第2週（10月20日週）](#-第2週10月20日週-1)
    - [🗓 会議③：AI分析チーム合同データ連携会議](#-会議ai分析チーム合同データ連携会議)
    - [🗓 会議④：第4週チーム定例](#-会議第4週チーム定例)
  - [teamsでの会話内容](#teamsでの会話内容-3)
  - [outlook予定表第二週](#outlook予定表第二週-1)


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

# ② データ基盤構築チーム（三宅チーム）

## 📘 第1週（10月13日週）

### 会議①：データ基盤チーム週次定例（第3週）

```
🗓 会議①：データ基盤チーム週次定例（第3週）

日時： 2025年10月15日（水）10:00〜11:30
場所： Teams（オンライン）
出席者：
三宅、白井、木下、青山、陳、橋本、河野、横山、福井、山岡、浜田、田村、大森、小泉、水谷（計15名）

■ 議題

進捗報告（各サブリーダー）

自治体Bデータ遅延対応

Azure監視設計進捗

次回AIチーム連携（データ提供範囲）確認

■ 議事概要
1. 進捗報告

白井（データアーキテクト）
　スキーマ定義v2完成。属性名の英語化対応完了。

木下（ETL）
　Airflow DAG構成のテスト環境反映済み。運用環境へ移行予定（10/17）。

青山（クラウド）
　Azure BLOBストレージ構築完了、RBAC設定も反映済み。

陳（API）
　API Gateway側の認証方式（OAuth2）でトークン有効期限延長対応を実施。

横山（匿名化）
　識別子マスキング処理で地方自治体データの一部仕様差分を発見、調整中。

2. 自治体Bデータ遅延対応

河野より報告：B市観光課からCSV形式変更の通知あり、10/18に再送予定。

三宅判断：受領次第、橋本・浜田が検証→木下がETL再実行。

3. Azure監視設計

水谷：DataDog連携は完了。バッチ監視はジョブ単位で閾値設定中。

福井：監視ログに暗号化情報を含まないよう再設定を要請。

4. AIチーム連携

三宅→藤原AIチームと連携、10/21の全体会で「分析対象データ提供条件」を共有予定。

■ 決定事項

ETL移行は10/17夜間実施（木下・山岡担当）。

自治体Bデータは10/18再取得、20日までに反映。

次回会議（10/22）はAIチーム合同で開催。

■ アクションアイテム
担当	内容	期限
橋本・浜田	B市データ品質検証	10/20
木下	ETL再実行・Airflow更新	10/21
青山	VPN接続確認・BLOB再配置	10/20
水谷・福井	DataDogアラート調整	10/19
```

### 🗓 会議②：API・匿名化方式 技術分科会

```
🗓 会議②：API・匿名化方式 技術分科会

日時： 2025年10月17日（金）16:00〜17:30
場所： Teams小会議室「API分科会」
出席者： 陳、横山、陶、福井、青山、橋本、三宅

■ 議題

API Gateway 認証トークン更新方式

個人情報マスキング仕様統一

セキュリティ審査提出資料レビュー

■ 議事概要
1. 認証トークン更新

陳：OAuth2トークン有効期限を2時間→6時間に変更済。

福井：運用監視側でトークン切れのログを追えるように設定要。

2. 匿名化仕様

横山：SHA256＋ソルト方式を採用。ソルトキーはKeyVault管理。

青山：KeyVaultのバックアップポリシー設定を確認。

3. セキュリティ資料

三宅：NEC社内セキュリティレビューへ10/23提出。

福井：暗号化方式、アクセス制御図の再チェック担当。

■ 決定事項

匿名化仕様（SHA256＋ソルト）正式採用。

KeyVault保守権限は福井に一本化。

次回、セキュリティレビュー報告会を10/24に設定。
```

## teamsでの会話内容

```
💬 技術・課題共有（チャネル）
💬 スレッド①：自治体Bデータ再送対応について

投稿者：河野 遥（データ連携管理）｜2025年10月15日 13:20

各位
B市観光課からデータ形式変更の件、正式に連絡がありました。
10/18（土）午前に CSV再送 の予定とのことです。
新形式のサンプル（1万件分）をもらったので、共有しておきます。
📎 B_city_sample_20251015.csv

@橋本翼 さん @浜田真帆 さん
検証の観点で注意すべき点があればコメントお願いします。

🟢 橋本 翼（品質管理）｜10/15 14:05

確認しました。
「利用日付」列が visit_date → used_date に変わってますね。
そのままだとETLスキーマでマッピング落ちします。
@木下俊輔 さん、この部分、再送時にスキーマv2対応できますか？

🟢 木下 俊輔（ETLリーダー）｜10/15 14:18

対応可能です。
Airflow側のDAG修正をローカルで済ませてますので、
再送データ受領後に v2.1 にアップデートして流します。

実行タイミングは 10/18（土）夜間（23:00〜）を想定しています。
@山岡 さん、その時間、モニタリング入れられますか？

🟢 山岡 健（ETL運用）｜10/15 14:21

はい、対応します。DataDog側のジョブ監視も追加しておきます。
実行完了後、#📅定例・進捗報告 に報告します。

🟢 浜田 真帆（品質検証）｜10/15 14:35

B市データの旧形式との差分検証、私の方で比較スクリプト準備中です。
diff_col_check.py の更新を今日中にpushします。
（@橋本 さん レビューお願いします🙏）

🟢 三宅 悠人（リーダー）｜10/15 15:00

ありがとうございます。
本件、20日までに反映が必要なのでスケジュール厳守でお願いします。

進捗は次回のAIチーム合同会議（10/22）で共有予定です。

💬 スレッド②：API Gatewayのトークン更新確認

投稿者：陳 文傑（APIリード）｜2025年10月16日 09:15

@青山玲奈 さん
OAuth2 トークンの有効期限を 6時間 に延ばしました。
DataDog で 401エラーを拾ってるログが少し増えてるようです。
Azure App Gateway 側のキャッシュ残りの影響かもしれません。
いったんキャッシュクリアお願いできますか？

🟢 青山 玲奈（クラウド統括）｜10/16 09:32

承知しました。
今夜のメンテ枠（22:00〜23:00）でキャッシュクリア＋再デプロイします。
終わったらこのスレッドに報告します。

🟢 福井 大介（セキュリティ）｜10/16 09:48

@陳 さん
トークン切れ時の監査ログですが、Azure Monitor の DiagnosticSetting で
すべてのAPI呼出しを追跡する設定にしました。
SecurityReview用のサンプルログも取っておきます。

🟢 陳 文傑｜10/16 10:05

助かります！
では、10/17のAPI分科会までに最新ログを整理しておきます。

（参考）OAuthトークン延長の設定差分
📎 auth_config_diff_20251016.json

🟢 青山 玲奈｜10/16 22:42（夜）

✅ キャッシュクリア＋App Gateway再デプロイ完了しました。
DataDogログも正常化しています。
@陳 さん、念のためAPI疎通確認お願いします。

🟢 陳 文傑｜10/17 08:50

問題なしでした。
/api/v2/tourdata エンドポイント含め、全件正常応答。
ありがとうございます🙆‍♂️

💬 スレッド③：匿名化処理の仕様統一

投稿者：横山 翔（匿名化担当）｜2025年10月17日 13:15

@福井 さん
SHA256＋ソルト化仕様で進めて良いとのことでしたので、
KeyVaultの設定詳細を再確認させてください。

現在は keyvault-prod-datakey に mask_salt_v1 が登録されていますが、
バックアップの自動スナップショットがOFFになっています。
これは意図的ですか？

🟢 福井 大介｜10/17 13:28

はい、現状はセキュリティポリシー上OFFです。
来週のセキュリティレビュー（10/24）でON/OFFポリシーを再検討予定。
一時的に手動バックアップを取ってもらってOKです。

🟢 青山 玲奈｜10/17 13:45

手動バックアップ対応します。
KeyVaultの状態を確認して、バックアップファイルを
secure_storage/20251017/ に格納予定です。
@横山 さん 完了したらSlackでDMします。

🟢 三宅 悠人｜10/17 17:30

皆さんお疲れさまです。
本日の分科会議事録は @横山 さん から共有あり次第、
Generalチャネルにも転載します。
特に匿名化仕様（SHA256＋ソルト）は正式採用とします。

📅 定例・進捗報告（チャネル）
📅 スレッド①：10/15 定例（データ基盤チーム）進捗まとめ

投稿者：三宅 悠人（チームリーダー）｜2025年10月15日 17:45

本日の定例内容を共有します。

✅ スキーマv2完成（@白井）
✅ Airflowテスト環境→運用移行10/17予定（@木下）
✅ Azure監視構築完了（@青山・@水谷）
✅ B市データ遅延対応（再送10/18予定）
✅ 次回（10/22）はAIチーム合同開催

アクションアイテムの進捗は以下のスレッドに追記してください👇

🟢 橋本 翼｜10/16 09:10

✅ B市データ品質チェックスクリプト更新済
check_bcity_v2.py → Gitリポジトリ data_validation にコミット済み。

🟢 青山 玲奈｜10/16 18:30

VPN接続確認完了。
Azure BLOB再配置も無事に完了しています。
DataDogでの監視アラート調整は @水谷 さんに引き継ぎ済み。

🟢 水谷 翔太｜10/17 09:45

DataDog閾値調整完了しました。
重大度「Critical」を5分連続エラー時にのみ発報するよう変更。

🔔 テスト発報も成功しています。

🟢 木下 俊輔｜10/18 23:45

ETL移行完了しました！
Airflowジョブも問題なし。
実行ログ：/logs/etl_20251018_run.log
@三宅 さん、@橋本 さん、B市データ再投入フェーズに入ります。

🟢 浜田 真帆｜10/19 10:20

データ品質OKです。
Null率、桁数、ユニーク制約ともに正常範囲内でした。

@木下 さん、再ETL実行OKです。

🟢 木下 俊輔｜10/19 11:15

了解しました。再ETL流しました。
結果：レコード件数 1,285,432件（旧版と+2.3%）

ETL完了後、DataLakeに反映済みです。

🟢 三宅 悠人｜10/19 12:00

完璧です。
全体連携報告に反映しておきます。
来週の合同会議でAIチーム側へのデータ提供範囲を説明予定です。

皆さん、週末対応ありがとうございました。👏

📰 一般（General）

投稿者：西川 麻衣（品質PM）｜2025年10月20日 09:00

各チームへ
10/22（水）全体会議（AIチーム合同）にて
「データ提供ルール」「監視ログ運用方針」について
データ基盤チームからも説明をお願いします。

@三宅 さん、発表スライド（5分想定）を10/21午前までにご共有ください。

🟢 三宅 悠人｜10/20 09:22

承知しました。
白井さん、スキーマ図とAPI連携フローをスライドに入れましょう。
@白井 奏 さん、今日中に素材共有いただけますか？

🟢 白井 奏｜10/20 11:00

了解です。
schema_v2_diagram.pptx をTeamsファイルにアップしました。
これをベースに @三宅 さん で最終調整お願いします。

🟢 三宅 悠人｜10/20 11:15

確認しました。
👌 完成版は明日朝にPMOへ提出します。
```

```json
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('team-nec-kanko-dx')/channels/messages",
  "team": {
    "id": "team-nec-kanko-dx",
    "displayName": "NEC観光DX基盤構築プロジェクト（全体）"
  },
  "fetchedAtUtc": "2025-10-27T17:00:00Z",
  "channels": [
    {
      "id": "19:general@thread.tacv2",
      "displayName": "📰 一般（General）",
      "messages": [
        {
          "id": "gen-msg-20251020-0900",
          "replyToId": null,
          "createdDateTime": "2025-10-20T00:00:00Z",
          "lastModifiedDateTime": "2025-10-20T00:00:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "【PMO】10/22 全体会議（AIチーム合同）依頼",
          "from": {
            "user": {
              "id": "u-nishikawa",
              "displayName": "西川 麻衣（品質PM）",
              "userPrincipalName": "mai.nishikawa@contoso.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<p>各チームへ<br/>10/22（水）全体会議（AIチーム合同）にて<br/>「データ提供ルール」「監視ログ運用方針」についてデータ基盤チームからも説明をお願いします。<br/><at id=\"0\">三宅 悠人</at> さん、発表スライド（5分想定）を10/21午前までにご共有ください。</p>"
          },
          "mentions": [
            {
              "id": 0,
              "mentionText": "三宅 悠人",
              "mentioned": {
                "user": {
                  "id": "u-miyake",
                  "displayName": "三宅 悠人",
                  "userIdentityType": "aadUser"
                }
              }
            }
          ],
          "attachments": [],
          "reactions": [],
          "replies": [
            {
              "id": "gen-rep-20251020-0922",
              "replyToId": "gen-msg-20251020-0900",
              "createdDateTime": "2025-10-20T00:22:00Z",
              "lastModifiedDateTime": "2025-10-20T00:22:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-miyake",
                  "displayName": "三宅 悠人",
                  "userPrincipalName": "yuto.miyake@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>承知しました。<br/>スキーマ図とAPI連携フローを反映します。<br/><at id=\"0\">白井 奏</at> さん、今日中に素材共有いただけますか？</p>"
              },
              "mentions": [
                {
                  "id": 0,
                  "mentionText": "白井 奏",
                  "mentioned": {
                    "user": {
                      "id": "u-shirai",
                      "displayName": "白井 奏",
                      "userIdentityType": "aadUser"
                    }
                  }
                }
              ],
              "attachments": []
            },
            {
              "id": "gen-rep-20251020-1100",
              "replyToId": "gen-msg-20251020-0900",
              "createdDateTime": "2025-10-20T02:00:00Z",
              "lastModifiedDateTime": "2025-10-20T02:00:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-shirai",
                  "displayName": "白井 奏",
                  "userPrincipalName": "kanade.shirai@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>了解です。<br/>資料をアップしました：<strong>schema_v2_diagram.pptx</strong></p>"
              },
              "attachments": [
                {
                  "id": "att-20251020-1100-1",
                  "name": "schema_v2_diagram.pptx",
                  "contentType": "application/vnd.openxmlformats-officedocument.presentationml.presentation",
                  "contentUrl": "https://contoso.sharepoint.com/sites/nec-kanko-dx/Shared%20Documents/schema_v2_diagram.pptx"
                }
              ]
            },
            {
              "id": "gen-rep-20251020-1115",
              "replyToId": "gen-msg-20251020-0900",
              "createdDateTime": "2025-10-20T02:15:00Z",
              "lastModifiedDateTime": "2025-10-20T02:15:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-miyake",
                  "displayName": "三宅 悠人",
                  "userPrincipalName": "yuto.miyake@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>確認しました。明日朝にPMOへ提出します。</p>"
              },
              "attachments": []
            }
          ]
        }
      ]
    },
    {
      "id": "19:weekly@thread.tacv2",
      "displayName": "📅 定例・進捗報告",
      "messages": [
        {
          "id": "wkly-msg-20251015-1745",
          "replyToId": null,
          "createdDateTime": "2025-10-15T08:45:00Z",
          "lastModifiedDateTime": "2025-10-15T08:45:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "10/15 定例（データ基盤チーム）進捗まとめ",
          "from": {
            "user": {
              "id": "u-miyake",
              "displayName": "三宅 悠人",
              "userPrincipalName": "yuto.miyake@contoso.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<p>本日の定例内容を共有します。</p><ul><li>✅ スキーマv2完成（<at id=\"0\">白井 奏</at>）</li><li>✅ Airflowテスト環境→運用移行10/17予定（<at id=\"1\">木下 俊輔</at>）</li><li>✅ Azure監視構築完了（<at id=\"2\">青山 玲奈</at>・<at id=\"3\">水谷 翔太</at>）</li><li>✅ B市データ遅延対応（再送10/18予定）</li><li>✅ 次回（10/22）はAIチーム合同開催</li></ul><p>アクションアイテムの進捗はこのスレッドに追記してください👇</p>"
          },
          "mentions": [
            { "id": 0, "mentionText": "白井 奏", "mentioned": { "user": { "id": "u-shirai", "displayName": "白井 奏", "userIdentityType": "aadUser" } } },
            { "id": 1, "mentionText": "木下 俊輔", "mentioned": { "user": { "id": "u-kinoshita", "displayName": "木下 俊輔", "userIdentityType": "aadUser" } } },
            { "id": 2, "mentionText": "青山 玲奈", "mentioned": { "user": { "id": "u-aoyama", "displayName": "青山 玲奈", "userIdentityType": "aadUser" } } },
            { "id": 3, "mentionText": "水谷 翔太", "mentioned": { "user": { "id": "u-mizutani", "displayName": "水谷 翔太", "userIdentityType": "aadUser" } } }
          ],
          "attachments": [],
          "replies": [
            {
              "id": "wkly-rep-20251016-0910",
              "replyToId": "wkly-msg-20251015-1745",
              "createdDateTime": "2025-10-16T00:10:00Z",
              "lastModifiedDateTime": "2025-10-16T00:10:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-hashimoto",
                  "displayName": "橋本 翼",
                  "userPrincipalName": "tsubasa.hashimoto@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>✅ B市データ品質チェックスクリプト更新済<br/>`check_bcity_v2.py` を <code>data_validation</code> リポジトリにコミットしました。</p>"
              },
              "attachments": []
            },
            {
              "id": "wkly-rep-20251016-1830",
              "replyToId": "wkly-msg-20251015-1745",
              "createdDateTime": "2025-10-16T09:30:00Z",
              "lastModifiedDateTime": "2025-10-16T09:30:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-aoyama",
                  "displayName": "青山 玲奈",
                  "userPrincipalName": "rena.aoyama@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>VPN接続確認完了。Azure BLOB再配置も完了。DataDogアラート調整は <at id=\"0\">水谷 翔太</at> に引き継ぎ済み。</p>"
              },
              "mentions": [
                { "id": 0, "mentionText": "水谷 翔太", "mentioned": { "user": { "id": "u-mizutani", "displayName": "水谷 翔太", "userIdentityType": "aadUser" } } }
              ],
              "attachments": []
            },
            {
              "id": "wkly-rep-20251017-0945",
              "replyToId": "wkly-msg-20251015-1745",
              "createdDateTime": "2025-10-17T00:45:00Z",
              "lastModifiedDateTime": "2025-10-17T00:45:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-mizutani",
                  "displayName": "水谷 翔太",
                  "userPrincipalName": "shota.mizutani@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>DataDog閾値調整完了。重大度「Critical」は5分連続エラー時のみ発報に変更。テスト発報も成功。</p>"
              },
              "attachments": []
            },
            {
              "id": "wkly-rep-20251018-2345",
              "replyToId": "wkly-msg-20251015-1745",
              "createdDateTime": "2025-10-18T14:45:00Z",
              "lastModifiedDateTime": "2025-10-18T14:45:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-kinoshita",
                  "displayName": "木下 俊輔",
                  "userPrincipalName": "shunsuke.kinoshita@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>ETL移行完了！Airflowジョブも問題なし。<br/>実行ログ：<code>/logs/etl_20251018_run.log</code><br/><at id=\"0\">三宅 悠人</at> さん、<at id=\"1\">橋本 翼</at> さん、B市データ再投入フェーズに入ります。</p>"
              },
              "mentions": [
                { "id": 0, "mentionText": "三宅 悠人", "mentioned": { "user": { "id": "u-miyake", "displayName": "三宅 悠人", "userIdentityType": "aadUser" } } },
                { "id": 1, "mentionText": "橋本 翼", "mentioned": { "user": { "id": "u-hashimoto", "displayName": "橋本 翼", "userIdentityType": "aadUser" } } }
              ],
              "attachments": []
            },
            {
              "id": "wkly-rep-20251019-1020",
              "replyToId": "wkly-msg-20251015-1745",
              "createdDateTime": "2025-10-19T01:20:00Z",
              "lastModifiedDateTime": "2025-10-19T01:20:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-hamada",
                  "displayName": "浜田 真帆",
                  "userPrincipalName": "maho.hamada@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>データ品質OK。Null率、桁数、ユニーク制約ともに正常範囲内。<br/><at id=\"0\">木下 俊輔</at> さん、再ETL実行OKです。</p>"
              },
              "mentions": [
                { "id": 0, "mentionText": "木下 俊輔", "mentioned": { "user": { "id": "u-kinoshita", "displayName": "木下 俊輔", "userIdentityType": "aadUser" } } }
              ],
              "attachments": []
            },
            {
              "id": "wkly-rep-20251019-1115",
              "replyToId": "wkly-msg-20251015-1745",
              "createdDateTime": "2025-10-19T02:15:00Z",
              "lastModifiedDateTime": "2025-10-19T02:15:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-kinoshita",
                  "displayName": "木下 俊輔",
                  "userPrincipalName": "shunsuke.kinoshita@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>了解しました。再ETL実行。結果：レコード件数 <strong>1,285,432</strong> 件（旧版比 +2.3%）。DataLakeへ反映済み。</p>"
              },
              "attachments": []
            },
            {
              "id": "wkly-rep-20251019-1200",
              "replyToId": "wkly-msg-20251015-1745",
              "createdDateTime": "2025-10-19T03:00:00Z",
              "lastModifiedDateTime": "2025-10-19T03:00:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-miyake",
                  "displayName": "三宅 悠人",
                  "userPrincipalName": "yuto.miyake@contoso.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>完璧です。全体連携報告に反映。10/22の合同会議でAIチームへのデータ提供範囲を説明します。<br/>週末対応ありがとうございました。👏</p>"
              },
              "attachments": []
            }
          ]
        }
      ]
    },
    {
      "id": "19:tech@thread.tacv2",
      "displayName": "💬 技術・課題共有",
      "messages": [
        {
          "id": "tech-msg-20251015-1320",
          "replyToId": null,
          "createdDateTime": "2025-10-15T04:20:00Z",
          "lastModifiedDateTime": "2025-10-15T04:20:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "スレッド①：自治体Bデータ再送対応について",
          "from": {
            "user": {
              "id": "u-kono",
              "displayName": "河野 遥",
              "userPrincipalName": "haruka.kono@contoso.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<p>各位<br/>B市観光課からデータ形式変更の件、正式に連絡がありました。10/18（土）午前に <strong>CSV再送</strong> の予定とのことです。新形式のサンプル（1万件分）を共有します。<br/>📎 <em>B_city_sample_20251015.csv</em><br/><at id=\"0\">橋本 翼</at> さん <at id=\"1\">浜田 真帆</at> さん、検証観点の注意点があればお願いします。</p>"
          },
          "mentions": [
            { "id": 0, "mentionText": "橋本 翼", "mentioned": { "user": { "id": "u-hashimoto", "displayName": "橋本 翼", "userIdentityType": "aadUser" } } },
            { "id": 1, "mentionText": "浜田 真帆", "mentioned": { "user": { "id": "u-hamada", "displayName": "浜田 真帆", "userIdentityType": "aadUser" } } }
          ],
          "attachments": [
            {
              "id": "att-20251015-1320-1",
              "name": "B_city_sample_20251015.csv",
              "contentType": "text/csv",
              "contentUrl": "https://contoso.sharepoint.com/sites/nec-kanko-dx/Shared%20Documents/B_city_sample_20251015.csv"
            }
          ],
          "replies": [
            {
              "id": "tech-rep-20251015-1405",
              "replyToId": "tech-msg-20251015-1320",
              "createdDateTime": "2025-10-15T05:05:00Z",
              "lastModifiedDateTime": "2025-10-15T05:05:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-hashimoto", "displayName": "橋本 翼", "userPrincipalName": "tsubasa.hashimoto@contoso.com" } },
              "body": {
                "contentType": "html",
                "content": "<p>確認しました。列名 <code>visit_date</code> → <code>used_date</code> に変更あり。ETLスキーマでマッピング落ちします。<br/><at id=\"0\">木下 俊輔</at> さん、スキーマv2対応可能でしょうか？</p>"
              },
              "mentions": [
                { "id": 0, "mentionText": "木下 俊輔", "mentioned": { "user": { "id": "u-kinoshita", "displayName": "木下 俊輔", "userIdentityType": "aadUser" } } }
              ],
              "attachments": []
            },
            {
              "id": "tech-rep-20251015-1418",
              "replyToId": "tech-msg-20251015-1320",
              "createdDateTime": "2025-10-15T05:18:00Z",
              "lastModifiedDateTime": "2025-10-15T05:18:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-kinoshita", "displayName": "木下 俊輔", "userPrincipalName": "shunsuke.kinoshita@contoso.com" } },
              "body": {
                "contentType": "html",
                "content": "<p>対応可能です。再送受領後に <strong>v2.1</strong> で流します。実行は 10/18（土）23:00〜 を想定。<br/><at id=\"0\">山岡 健</at> さん、モニタリングお願いできますか？</p>"
              },
              "mentions": [
                { "id": 0, "mentionText": "山岡 健", "mentioned": { "user": { "id": "u-yamaoka", "displayName": "山岡 健", "userIdentityType": "aadUser" } } }
              ]
            },
            {
              "id": "tech-rep-20251015-1421",
              "replyToId": "tech-msg-20251015-1320",
              "createdDateTime": "2025-10-15T05:21:00Z",
              "lastModifiedDateTime": "2025-10-15T05:21:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-yamaoka", "displayName": "山岡 健", "userPrincipalName": "ken.yamaoka@contoso.com" } },
              "body": { "contentType": "html", "content": "<p>対応します。DataDogジョブ監視も追加します。完了後 #📅 定例・進捗報告 に報告します。</p>" }
            },
            {
              "id": "tech-rep-20251015-1435",
              "replyToId": "tech-msg-20251015-1320",
              "createdDateTime": "2025-10-15T05:35:00Z",
              "lastModifiedDateTime": "2025-10-15T05:35:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-hamada", "displayName": "浜田 真帆", "userPrincipalName": "maho.hamada@contoso.com" } },
              "body": {
                "contentType": "html",
                "content": "<p>旧形式との差分検証スクリプト <code>diff_col_check.py</code> を今日中にpushします。<br/><at id=\"0\">橋本 翼</at> さん、レビューお願いします🙏</p>"
              },
              "mentions": [
                { "id": 0, "mentionText": "橋本 翼", "mentioned": { "user": { "id": "u-hashimoto", "displayName": "橋本 翼", "userIdentityType": "aadUser" } } }
              ]
            },
            {
              "id": "tech-rep-20251015-1500",
              "replyToId": "tech-msg-20251015-1320",
              "createdDateTime": "2025-10-15T06:00:00Z",
              "lastModifiedDateTime": "2025-10-15T06:00:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-miyake", "displayName": "三宅 悠人", "userPrincipalName": "yuto.miyake@contoso.com" } },
              "body": { "contentType": "html", "content": "<p>ありがとうございます。20日までに反映必須。進捗は 10/22 のAI合同会議で共有します。</p>" }
            }
          ]
        },
        {
          "id": "tech-msg-20251016-0915",
          "replyToId": null,
          "createdDateTime": "2025-10-16T00:15:00Z",
          "lastModifiedDateTime": "2025-10-16T00:15:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "スレッド②：API Gatewayのトークン更新確認",
          "from": {
            "user": {
              "id": "u-chen",
              "displayName": "陳 文傑",
              "userPrincipalName": "wenjie.chen@contoso.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<p><at id=\"0\">青山 玲奈</at> さん<br/>OAuth2 トークン有効期限を <strong>6時間</strong> に延長しました。DataDogで 401 がやや増加。App Gateway キャッシュ残りの可能性があるので、キャッシュクリアお願いします。</p>"
          },
          "mentions": [
            { "id": 0, "mentionText": "青山 玲奈", "mentioned": { "user": { "id": "u-aoyama", "displayName": "青山 玲奈", "userIdentityType": "aadUser" } } }
          ],
          "attachments": [],
          "replies": [
            {
              "id": "tech-rep-20251016-0932",
              "replyToId": "tech-msg-20251016-0915",
              "createdDateTime": "2025-10-16T00:32:00Z",
              "lastModifiedDateTime": "2025-10-16T00:32:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-aoyama", "displayName": "青山 玲奈", "userPrincipalName": "rena.aoyama@contoso.com" } },
              "body": { "contentType": "html", "content": "<p>承知しました。今夜（22:00〜23:00）にキャッシュクリア＋再デプロイします。完了後に報告します。</p>" }
            },
            {
              "id": "tech-rep-20251016-0948",
              "replyToId": "tech-msg-20251016-0915",
              "createdDateTime": "2025-10-16T00:48:00Z",
              "lastModifiedDateTime": "2025-10-16T00:48:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-fukui", "displayName": "福井 大介", "userPrincipalName": "daisuke.fukui@contoso.com" } },
              "body": { "contentType": "html", "content": "<p>監査ログは Azure Monitor の DiagnosticSetting で全呼出しを追跡に設定。SecurityReview 用サンプルログも採取します。</p>" }
            },
            {
              "id": "tech-rep-20251016-1005",
              "replyToId": "tech-msg-20251016-0915",
              "createdDateTime": "2025-10-16T01:05:00Z",
              "lastModifiedDateTime": "2025-10-16T01:05:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-chen", "displayName": "陳 文傑", "userPrincipalName": "wenjie.chen@contoso.com" } },
              "body": {
                "contentType": "html",
                "content": "<p>ありがとうございます。10/17 の API 分科会までに最新ログを整理しておきます。<br/>参考：設定差分を添付します。</p>"
              },
              "attachments": [
                {
                  "id": "att-20251016-1005-1",
                  "name": "auth_config_diff_20251016.json",
                  "contentType": "application/json",
                  "contentUrl": "https://contoso.sharepoint.com/sites/nec-kanko-dx/Shared%20Documents/auth_config_diff_20251016.json"
                }
              ]
            },
            {
              "id": "tech-rep-20251016-2242",
              "replyToId": "tech-msg-20251016-0915",
              "createdDateTime": "2025-10-16T13:42:00Z",
              "lastModifiedDateTime": "2025-10-16T13:42:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-aoyama", "displayName": "青山 玲奈", "userPrincipalName": "rena.aoyama@contoso.com" } },
              "body": { "contentType": "html", "content": "<p>✅ キャッシュクリア＋App Gateway再デプロイ完了。DataDogログも正常化しています。<br/><at id=\"0\">陳 文傑</at> さん、疎通確認お願いします。</p>" },
              "mentions": [
                { "id": 0, "mentionText": "陳 文傑", "mentioned": { "user": { "id": "u-chen", "displayName": "陳 文傑", "userIdentityType": "aadUser" } } }
              ]
            },
            {
              "id": "tech-rep-20251017-0850",
              "replyToId": "tech-msg-20251016-0915",
              "createdDateTime": "2025-10-16T23:50:00Z",
              "lastModifiedDateTime": "2025-10-16T23:50:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-chen", "displayName": "陳 文傑", "userPrincipalName": "wenjie.chen@contoso.com" } },
              "body": { "contentType": "html", "content": "<p>疎通問題なし。<code>/api/v2/tourdata</code> 含む全エンドポイント正常です。ありがとうございます🙆‍♂️</p>" }
            }
          ]
        },
        {
          "id": "tech-msg-20251017-1315",
          "replyToId": null,
          "createdDateTime": "2025-10-17T04:15:00Z",
          "lastModifiedDateTime": "2025-10-17T04:15:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "スレッド③：匿名化処理の仕様統一",
          "from": {
            "user": {
              "id": "u-yokoyama",
              "displayName": "横山 翔",
              "userPrincipalName": "sho.yokoyama@contoso.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<p><at id=\"0\">福井 大介</at> さん<br/>SHA256＋ソルト化仕様で進めます。KeyVault の <code>keyvault-prod-datakey</code> に <code>mask_salt_v1</code> が登録済ですが、自動スナップショットが OFF です。意図的でしょうか？</p>"
          },
          "mentions": [
            { "id": 0, "mentionText": "福井 大介", "mentioned": { "user": { "id": "u-fukui", "displayName": "福井 大介", "userIdentityType": "aadUser" } } }
          ],
          "attachments": [],
          "replies": [
            {
              "id": "tech-rep-20251017-1328",
              "replyToId": "tech-msg-20251017-1315",
              "createdDateTime": "2025-10-17T04:28:00Z",
              "lastModifiedDateTime": "2025-10-17T04:28:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-fukui", "displayName": "福井 大介", "userPrincipalName": "daisuke.fukui@contoso.com" } },
              "body": { "contentType": "html", "content": "<p>現状はポリシー上 OFF にしています。10/24 のセキュリティレビューで再検討。一時的に手動バックアップを取ってOKです。</p>" }
            },
            {
              "id": "tech-rep-20251017-1345",
              "replyToId": "tech-msg-20251017-1315",
              "createdDateTime": "2025-10-17T04:45:00Z",
              "lastModifiedDateTime": "2025-10-17T04:45:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-aoyama", "displayName": "青山 玲奈", "userPrincipalName": "rena.aoyama@contoso.com" } },
              "body": {
                "contentType": "html",
                "content": "<p>手動バックアップ対応します。バックアップファイルは <code>secure_storage/20251017/</code> に格納予定。完了したらDMします。</p>"
              }
            },
            {
              "id": "tech-rep-20251017-1730",
              "replyToId": "tech-msg-20251017-1315",
              "createdDateTime": "2025-10-17T08:30:00Z",
              "lastModifiedDateTime": "2025-10-17T08:30:00Z",
              "messageType": "message",
              "from": { "user": { "id": "u-miyake", "displayName": "三宅 悠人", "userPrincipalName": "yuto.miyake@contoso.com" } },
              "body": {
                "contentType": "html",
                "content": "<p>分科会議事録は共有あり次第 General に転載します。匿名化仕様（SHA256＋ソルト）は正式採用とします。</p>"
              }
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
想定されるOutlook予定（JST）
2025-10-16（木）

22:00–23:00｜App Gateway キャッシュクリア＆再デプロイ（メンテ）
参加：青山、陳、福井（監査ログ確認）
場所：Teams 会議（オンライン）
備考：作業後に疎通確認

2025-10-17（金）

09:00–10:00｜API 分科会（トークン更新ログ確認）
主催：陳
参加：青山、福井、三宅 ほか
場所：Teams 会議（オンライン）

2025-10-18（土）

09:00–10:00｜自治体B：CSV再送 受領確認
主催：河野
参加：橋本、浜田、木下
場所：Teams 会議（オンライン）

23:00–24:00｜ETL v2.1 再投入（監視付き）
主催：木下
参加：山岡（監視）、橋本、浜田、三宅
場所：Teams 会議（オンライン）
備考：DataDog アラート監視、完了後 #定例・進捗報告 に投稿

2025-10-21（火）

09:00–09:30｜全体会議スライド提出締切（データ基盤パート）
主催：西川（品質PM）
参加：三宅、白井
場所：—（期限リマインダー）

2025-10-22（水）

10:00–11:00｜全体会議（AIチーム合同）
主催：西川（品質PM）
参加：PMO、データ基盤（三宅・白井・木下・青山・水谷・橋本・浜田・陳 ほか）、AIチーム
場所：Teams 会議（オンライン）
議題：データ提供ルール／監視ログ運用方針（データ基盤から5分説明）

2025-10-24（金）

10:00–11:00｜セキュリティレビュー（KeyVault運用・匿名化仕様）
主催：福井
参加：横山、青山、三宅 ほか
場所：Teams 会議（オンライン）
議題：匿名化（SHA256+ソルト）、KeyVaultバックアップ方針

定例（参考：データ基盤チーム）

毎週水曜 17:30–18:00｜データ基盤 定例（進捗共有）
主催：三宅
場所：Teams 会議（オンライン）
備考：10/22 は「AIチーム合同」で置き換え
```

```json
{
  "id": "AAMkADkya...-22ai-allhands",
  "subject": "【全体】AIチーム合同：データ提供ルール／監視ログ運用",
  "bodyPreview": "データ基盤から5分説明（スキーマ図・API連携フロー）",
  "start": { "dateTime": "2025-10-22T10:00:00", "timeZone": "Asia/Tokyo" },
  "end":   { "dateTime": "2025-10-22T11:00:00", "timeZone": "Asia/Tokyo" },
  "location": { "displayName": "Microsoft Teams 会議" },
  "isOnlineMeeting": true,
  "onlineMeetingProvider": "teamsForBusiness",
  "attendees": [
    { "type": "required", "emailAddress": { "name": "西川 麻衣", "address": "mai.nishikawa@contoso.com" } },
    { "type": "required", "emailAddress": { "name": "三宅 悠人", "address": "yuto.miyake@contoso.com" } },
    { "type": "required", "emailAddress": { "name": "白井 奏", "address": "kanade.shirai@contoso.com" } }
  ],
  "organizer": { "emailAddress": { "name": "西川 麻衣", "address": "mai.nishikawa@contoso.com" } },
  "reminderMinutesBeforeStart": 15,
  "sensitivity": "normal",
  "categories": ["全体会議","AI合同"]
}
{
  "id": "AAMkADkya...-17api-wg",
  "subject": "API分科会：トークン更新ログ・監査設定確認",
  "bodyPreview": "10/16の再デプロイ後ログ確認、DiagnosticSetting見直し",
  "start": { "dateTime": "2025-10-17T09:00:00", "timeZone": "Asia/Tokyo" },
  "end":   { "dateTime": "2025-10-17T10:00:00", "timeZone": "Asia/Tokyo" },
  "location": { "displayName": "Microsoft Teams 会議" },
  "isOnlineMeeting": true,
  "onlineMeetingProvider": "teamsForBusiness",
  "attendees": [
    { "type": "required", "emailAddress": { "name": "陳 文傑", "address": "wenjie.chen@contoso.com" } },
    { "type": "required", "emailAddress": { "name": "青山 玲奈", "address": "rena.aoyama@contoso.com" } },
    { "type": "optional", "emailAddress": { "name": "福井 大介", "address": "daisuke.fukui@contoso.com" } }
  ],
  "organizer": { "emailAddress": { "name": "陳 文傑", "address": "wenjie.chen@contoso.com" } },
  "reminderMinutesBeforeStart": 10,
  "categories": ["分科会","API"]
}
{
  "id": "AAMkADkya...-16agw-maint",
  "subject": "【メンテ】App Gateway キャッシュクリア＋再デプロイ",
  "bodyPreview": "作業後に疎通確認。401増加解消の最終確認。",
  "start": { "dateTime": "2025-10-16T22:00:00", "timeZone": "Asia/Tokyo" },
  "end":   { "dateTime": "2025-10-16T23:00:00", "timeZone": "Asia/Tokyo" },
  "location": { "displayName": "オンライン（Teams）" },
  "attendees": [
    { "type": "required", "emailAddress": { "name": "青山 玲奈", "address": "rena.aoyama@contoso.com" } },
    { "type": "optional", "emailAddress": { "name": "陳 文傑", "address": "wenjie.chen@contoso.com" } },
    { "type": "optional", "emailAddress": { "name": "福井 大介", "address": "daisuke.fukui@contoso.com" } }
  ],
  "isOnlineMeeting": true,
  "onlineMeetingProvider": "teamsForBusiness",
  "organizer": { "emailAddress": { "name": "青山 玲奈", "address": "rena.aoyama@contoso.com" } },
  "reminderMinutesBeforeStart": 30,
  "importance": "high",
  "categories": ["メンテナンス"]
}
{
  "id": "AAMkADkya...-18bcity-recv",
  "subject": "自治体B：CSV再送 受領確認ミーティング",
  "bodyPreview": "列名変更（visit_date→used_date）影響、差分チェック進行確認",
  "start": { "dateTime": "2025-10-18T09:00:00", "timeZone": "Asia/Tokyo" },
  "end":   { "dateTime": "2025-10-18T10:00:00", "timeZone": "Asia/Tokyo" },
  "location": { "displayName": "Microsoft Teams 会議" },
  "isOnlineMeeting": true,
  "attendees": [
    { "type": "required", "emailAddress": { "name": "河野 遥", "address": "haruka.kono@contoso.com" } },
    { "type": "required", "emailAddress": { "name": "橋本 翼", "address": "tsubasa.hashimoto@contoso.com" } },
    { "type": "required", "emailAddress": { "name": "浜田 真帆", "address": "maho.hamada@contoso.com" } },
    { "type": "optional", "emailAddress": { "name": "木下 俊輔", "address": "shunsuke.kinoshita@contoso.com" } }
  ],
  "organizer": { "emailAddress": { "name": "河野 遥", "address": "haruka.kono@contoso.com" } },
  "reminderMinutesBeforeStart": 10,
  "categories": ["データ連携"]
}
{
  "id": "AAMkADkya...-18etl-reingest",
  "subject": "ETL v2.1 再投入（監視付き）",
  "bodyPreview": "DataDog 監視、ジョブ閾値Critical=5分持続時のみ発報",
  "start": { "dateTime": "2025-10-18T23:00:00", "timeZone": "Asia/Tokyo" },
  "end":   { "dateTime": "2025-10-19T00:00:00", "timeZone": "Asia/Tokyo" },
  "location": { "displayName": "オンライン（Teams）" },
  "attendees": [
    { "type": "required", "emailAddress": { "name": "木下 俊輔", "address": "shunsuke.kinoshita@contoso.com" } },
    { "type": "required", "emailAddress": { "name": "山岡 健", "address": "ken.yamaoka@contoso.com" } },
    { "type": "optional", "emailAddress": { "name": "橋本 翼", "address": "tsubasa.hashimoto@contoso.com" } },
    { "type": "optional", "emailAddress": { "name": "浜田 真帆", "address": "maho.hamada@contoso.com" } }
  ],
  "isOnlineMeeting": true,
  "organizer": { "emailAddress": { "name": "木下 俊輔", "address": "shunsuke.kinoshita@contoso.com" } },
  "reminderMinutesBeforeStart": 60,
  "categories": ["ETL","運用"]
}
{
  "id": "AAMkADkya...-21deck-deadline",
  "subject": "〆切：全体会議スライド提出（データ基盤）",
  "bodyPreview": "三宅→西川へ。素材：schema_v2_diagram.pptx ほか",
  "start": { "dateTime": "2025-10-21T09:00:00", "timeZone": "Asia/Tokyo" },
  "end":   { "dateTime": "2025-10-21T09:30:00", "timeZone": "Asia/Tokyo" },
  "location": { "displayName": "—" },
  "attendees": [
    { "type": "required", "emailAddress": { "name": "三宅 悠人", "address": "yuto.miyake@contoso.com" } },
    { "type": "optional", "emailAddress": { "name": "白井 奏", "address": "kanade.shirai@contoso.com" } }
  ],
  "organizer": { "emailAddress": { "name": "西川 麻衣", "address": "mai.nishikawa@contoso.com" } },
  "reminderMinutesBeforeStart": 60,
  "categories": ["締切"]
}
{
  "id": "AAMkADkya...-24sec-review",
  "subject": "セキュリティレビュー：匿名化仕様／KeyVault運用",
  "bodyPreview": "SHA256+ソルト、KeyVault自動スナップショット方針再検討",
  "start": { "dateTime": "2025-10-24T10:00:00", "timeZone": "Asia/Tokyo" },
  "end":   { "dateTime": "2025-10-24T11:00:00", "timeZone": "Asia/Tokyo" },
  "location": { "displayName": "Microsoft Teams 会議" },
  "isOnlineMeeting": true,
  "attendees": [
    { "type": "required", "emailAddress": { "name": "福井 大介", "address": "daisuke.fukui@contoso.com" } },
    { "type": "required", "emailAddress": { "name": "横山 翔", "address": "sho.yokoyama@contoso.com" } },
    { "type": "optional", "emailAddress": { "name": "青山 玲奈", "address": "rena.aoyama@contoso.com" } },
    { "type": "optional", "emailAddress": { "name": "三宅 悠人", "address": "yuto.miyake@contoso.com" } }
  ],
  "organizer": { "emailAddress": { "name": "福井 大介", "address": "daisuke.fukui@contoso.com" } },
  "reminderMinutesBeforeStart": 15,
  "categories": ["セキュリティ"]
}
{
  "id": "AAMkADkya...-wkly-dp-standup",
  "subject": "データ基盤 定例（進捗共有）",
  "bodyPreview": "進捗・リスク・アクション更新。10/22はAI合同へ置換。",
  "start": { "dateTime": "2025-10-15T17:30:00", "timeZone": "Asia/Tokyo" },
  "end":   { "dateTime": "2025-10-15T18:00:00", "timeZone": "Asia/Tokyo" },
  "location": { "displayName": "Microsoft Teams 会議" },
  "isOnlineMeeting": true,
  "onlineMeetingProvider": "teamsForBusiness",
  "recurrence": {
    "pattern": { "type": "weekly", "interval": 1, "daysOfWeek": ["wednesday"] },
    "range": { "type": "noEnd", "startDate": "2025-10-15" }
  },
  "attendees": [
    { "type": "required", "emailAddress": { "name": "三宅 悠人", "address": "yuto.miyake@contoso.com" } },
    { "type": "required", "emailAddress": { "name": "白井 奏", "address": "kanade.shirai@contoso.com" } },
    { "type": "required", "emailAddress": { "name": "木下 俊輔", "address": "shunsuke.kinoshita@contoso.com" } }
  ],
  "organizer": { "emailAddress": { "name": "三宅 悠人", "address": "yuto.miyake@contoso.com" } },
  "reminderMinutesBeforeStart": 10,
  "categories": ["定例"]
}

```

## 📘 第2週（10月20日週）

### 🗓 会議③：AI分析チーム合同データ連携会議

```
🗓 会議③：AI分析チーム合同データ連携会議

日時： 2025年10月22日（水）14:00〜15:30
場所： Teams「全体推進会議／AI-基盤合同」
出席者： 三宅、藤原（AI）、白井、木下、青山、加賀、陳、相沢（UX代表）ほか

■ 議題

データ提供スキーマの最終確認

SHAP分析用データセット範囲

APIエンドポイントの試験公開スケジュール

次期PoC連携方針

■ 議事概要
1. データスキーマ

白井：最新スキーマv2.1を提示。AI側の必要カラム「stay_duration」「traffic_type」追加済。

2. SHAP分析用データ

加賀：匿名化済サンプルを10万件単位で準備。AI側での前処理要。

3. API試験公開

陳：内部向けAPIを10/25に試験公開予定。

青山：Azure側ロードバランサ設定を10/24完了予定。

4. PoC方針

藤原（AI）：次期PoCでは自治体Cの宿泊データを活用。ETL負荷見積りを基盤側に依頼。

■ 決定事項

API試験公開：10/25（土）

AIチームへのデータ提供：10/26（日）

ETLリソース見積：木下・山岡が10/24までに提示。

■ アクションアイテム
担当	内容	期限
白井	スキーマv2.1最終化	10/23
木下・山岡	ETL負荷見積作成	10/24
青山	Azure LB設定	10/24
陳	API試験公開	10/25
加賀	SHAP分析用データ提供	10/26
```

### 🗓 会議④：第4週チーム定例

```
🗓 会議④：第4週チーム定例

日時： 2025年10月24日（金）10:00〜11:30
場所： Teams（定例チャンネル）
出席者： 三宅、白井、木下、青山、陳、橋本、河野、横山、浜田、福井、水谷、大森、小泉、田村（計14名）

■ 議題

今週の進捗確認（AI連携後の反映）

監視アラート・エラー発生状況

ドキュメント整理状況

次回リリース（v1.2）準備

■ 議事概要
1. 進捗

ETL再実行成功。B市データ取り込み完了（10/21）。

API試験公開済（10/25予定を前倒し10/24午後に実施）。

データレイク格納件数：計4,120万件（前週比+8%）。

2. 監視・アラート

水谷：夜間ジョブ1件でタイムアウト発生（リトライ成功）。閾値を調整予定。

福井：監視ログから暗号化キー漏洩の恐れなし。確認済み。

3. ドキュメント整理

小泉：設計書・ETL構成図をConfluenceに統合。

田村：メタデータ辞書を更新、来週AIチームにも共有。

4. 次回リリース

三宅：v1.2リリースを10/28予定で進行。

大森：GitHub Actionsで自動テスト導入予定。

青山：Terraform IaC更新を反映。

■ 決定事項

v1.2リリース：10/28（火）夜間。

Confluenceでドキュメント一元管理へ移行。

来週は「運用自動化」分科会を新設予定。

■ アクションアイテム
担当	内容	期限
水谷	ジョブ監視閾値再設定	10/27
小泉・田村	Confluence統合完了報告	10/27
大森	GitHub Actionsテスト導入	10/28
青山	Terraform更新反映	10/28
三宅	リリースチェック・報告書提出	10/29
```

## teamsでの会話内容

```
💬 技術・課題共有（チャネル）
🧩 スレッド①：API試験公開準備（10/21〜10/25）

投稿者：陳 文傑（APIリード）｜2025年10月21日 09:20

各位
API試験公開（10/25予定）に向け、テスト用エンドポイント /api/v1/visits/summary の疎通確認を開始しました。
@青山 玲奈 さん、Azure側ロードバランサ設定は予定通り24日中に反映で問題なさそうですか？
@木下 俊輔 さん、ETL出力フォーマット（CSV→Parquet変換）のサンプルをAPI側で確認したいです。

📎 api_test_request.json（テストリクエスト例）を添付しました。

返信：青山 玲奈（クラウド統括）｜10/21 10:05

@陳 さん
LB設定は昨晩ステージング環境でテスト済みです。
本番側への反映は 10/23午前中 に前倒しで行います。
Terraform更新も feature/lb_rule_v2 ブランチにpush済みです。

返信：木下 俊輔（ETLリーダー）｜10/21 11:10

@陳 さん
Parquet出力の最新フォーマットを /etl/output/preview_20251021/ に配置しました。
カラム名もスキーマv2.1に合わせて修正済み（stay_duration, traffic_type 含む）。
@白井 奏 さん にも最終チェックお願いしたいです。

返信：白井 奏（データアーキテクト）｜10/21 12:02

確認しました。
stay_duration の型はfloat→int変換で統一お願いします。
traffic_type は文字列カテゴリで問題なし。
→ 修正版を10/22午前までに再出力いただければOKです。

返信：木下 俊輔｜10/22 09:40

再出力完了しました。
parquet_v2.1_20251022 を共有済み。
@陳 さん API側で再確認お願いします。

返信：陳 文傑｜10/22 13:15

受領しました。
動作問題なしです。
予定通り 10/24午後に試験公開 へ切り替えます。
@青山 さん LB側ルーティング変更タイミングだけ、Slackでも通知いただけると助かります。

🧮 スレッド②：SHAP分析用データ提供（10/22〜10/24）

投稿者：加賀 亮（AIチーム）｜2025年10月22日 15:10

@白井 さん
SHAP分析用データ10万件×3セットの匿名化処理が完了しました。
/ai_input/shap_dataset_v2.1.zip に格納済です。
ETL側での整形（null埋め・日付正規化）をお願いできますか？
AI側では週末から学習テストに入ります。

返信：白井 奏｜10/22 16:00

ありがとうございます。
ETL整形スクリプトを修正中です（etl_shap_cleaner.py）。
used_date 列の変換仕様だけ確認したいのですが、YYYY-MM-DD形式で統一で良いですか？

返信：加賀 亮｜10/22 16:12

はい、それでOKです。
used_date はAIモデル入力時に時系列特徴量として扱うので、フォーマット統一助かります。

返信：木下 俊輔｜10/23 10:00

整形完了しました。
ファイルは /shared/etl/shap_ready_20251023.parquet に配置済。
サイズ：2.8GB。
@加賀 さん、@藤原 さん（AIリーダー）こちらで取り込み可能かご確認ください。

返信：藤原 大輝（AIリーダー）｜10/23 11:05

確認OKです。
本日夜からSHAPトレーニングを実施します。
GPU環境（A100）で動かすため、バッチ単位で分割して取り込みます。
ETL側の迅速対応ありがとうございました！

⚙️ スレッド③：夜間ジョブの監視アラート（10/23〜10/25）

投稿者：水谷 翔（運用担当）｜2025年10月23日 22:30

昨夜のジョブ実行ログで etl_nightly_traffic_20251023 がタイムアウト。
再実行で正常終了しましたが、閾値設定を調整します。
@橋本 翼 さん、品質管理ログ上も異常検知なしで良いでしょうか？

返信：橋本 翼（品質管理）｜10/24 08:15

@水谷 さん
はい、該当ジョブはリトライ後に全件処理されているのを確認しました。
セキュリティログ側にも異常はありません。
閾値調整のPR作成時、threshold_reconfig.yaml の変更点だけレビュー依頼お願いします。

返信：水谷 翔｜10/24 11:05

PR出しました（#245）。
処理時間上限を「15分→25分」に拡張。
@大森 さん 自動テストのジョブ連携に影響しないか確認お願いします。

返信：大森 直人（CI/CD担当）｜10/24 13:45

問題なしです。
GitHub Actions側のタイムアウトは別設定（30分）なので影響なし。
今夜自動テストフロー追加も併せてマージ予定です。

📅 定例・進捗報告（チャネル）
スレッド①：第4週リリース進行管理（10/24〜10/28）

投稿者：三宅 悠人（チームリーダー）｜2025年10月24日 17:30

皆さん、お疲れ様です。
定例会で決定した通り、v1.2リリースは 10/28（火）夜間 で進行します。
以下、作業項目を再掲します。

@青山 さん：Terraform更新反映（IaC調整）

@大森 さん：GitHub Actions自動テスト導入

@小泉 さん・@田村 さん：Confluence統合報告

@水谷 さん：監視閾値再設定

@木下 さん：ETL負荷見積最終化（PoC対応）

それぞれ進捗をこのスレッドで報告してください。

返信：青山 玲奈｜10/25 09:10

Terraform更新反映済です。
main にマージ完了。
Azure側のリソースグループ整備も完了しました。
LB設定変更も合わせて確認OKです。

返信：大森 直人｜10/25 12:00

GitHub Actionsによる自動テストフロー導入完了。
pytest結果をSlack通知する仕組みを追加しました。
明日（10/26）の夜間ジョブで初回動作を確認予定。

返信：小泉 愛実｜10/25 15:15

Confluence統合完了しました。
ETL・API設計書、構成図、メタデータ辞書を統合済。
@田村 さん、AIチーム共有用ページの公開権限だけ再チェックお願いします。

返信：田村 亮介｜10/25 17:00

権限設定修正しました。
/AI_shared/metadata_v2.1 ページをAIチームメンバーに公開済です。

返信：水谷 翔｜10/26 09:00

ジョブ監視閾値を25分に変更済。
異常検知テストも完了しました。
来週から新しき閾値で監視運用を開始します。

返信：木下 俊輔｜10/26 13:30

ETL負荷見積作成完了。
自治体Cの宿泊データ（約900万件）でCPU使用率平均65%、GPU処理時短効果15%。
詳細レポートを @藤原 さん にも共有済です。

返信：三宅 悠人｜10/27 10:15

各担当、迅速な対応ありがとうございます。
本日夜、リリースリハーサルを実施し、
10/28夜間の本番反映 に備えます。
報告書は10/29にPMO宛提出予定です。

スレッド②：運用自動化分科会の準備（10/27〜10/28）

投稿者：橋本 翼（品質管理）｜2025年10月27日 11:20

来週開始予定の「運用自動化分科会」について、初回議題案をまとめました。
@三宅 さん、@青山 さん、@大森 さん ご確認ください。

ジョブ監視の自動リカバリ（再実行フロー）

成果物（ETLログ・テスト結果）の自動アーカイブ

IaC更新時の自動差分通知（GitOps連携）

資料ドラフト👇
📎 automation_wg_agenda_v1.docx

返信：三宅 悠人｜10/27 13:05

確認しました。良い内容です。
第1回は10/30（木）15:00〜で調整中。
PMO側（@松下 さん）にも展開します。

返信：青山 玲奈｜10/27 13:30

GitOps連携はAzure DevOpsでもPoC進めているので、その部分担当します。
Terraform差分検知スクリプトもサンプル共有します。

返信：大森 直人｜10/27 14:10

了解しました。
CI/CD観点での改善点（ログ整形・Slack通知）も発表パートでまとめておきます。
```

```json
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('team-nec-kanko-dx')/channels/messages",
  "team": {
    "id": "team-nec-kanko-dx",
    "displayName": "NEC観光DX基盤構築プロジェクト（全体）"
  },
  "fetchedAtUtc": "2025-10-27T17:30:00Z",
  "channels": [
    {
      "id": "19:general@thread.tacv2",
      "displayName": "📰 一般（General）",
      "messages": [
        {
          "id": "msg-gen-001",
          "replyToId": null,
          "createdDateTime": "2025-10-22T00:05:00Z",
          "lastModifiedDateTime": "2025-10-22T00:05:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "【全体共有】10月第4週の連絡事項",
          "from": {
            "user": {
              "id": "u-ishida",
              "displayName": "石田 智久（PM）",
              "userPrincipalName": "tomohisa.ishida@example.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<p>今週の全体会議は10/24（金）10:00〜です。議題：進捗、リスク#12対応、v1.2リリース準備。</p>"
          },
          "attachments": [],
          "replies": [
            {
              "id": "msg-gen-001-r1",
              "replyToId": "msg-gen-001",
              "createdDateTime": "2025-10-22T00:20:00Z",
              "lastModifiedDateTime": "2025-10-22T00:20:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-matsushita",
                  "displayName": "松下 翔太（PMO）",
                  "userPrincipalName": "shota.matsushita@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>議事録テンプレートを更新しました。定例後にアップします。</p>"
              },
              "attachments": []
            }
          ]
        }
      ]
    },
    {
      "id": "19:weekly@thread.tacv2",
      "displayName": "📅 定例・進捗報告",
      "messages": [
        {
          "id": "msg-prog-001",
          "replyToId": null,
          "createdDateTime": "2025-10-24T08:30:00Z",
          "lastModifiedDateTime": "2025-10-24T08:30:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "第4週リリース進行管理（10/24〜10/28）",
          "from": {
            "user": {
              "id": "u-miyake",
              "displayName": "三宅 悠人（チームリーダー）",
              "userPrincipalName": "yuto.miyake@example.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<p>定例会で決定した通り、v1.2リリースは <b>10/28（火）夜間</b> で進行します。各担当は本スレで進捗共有をお願いします。</p><ul><li>@青山：Terraform更新反映（IaC調整）</li><li>@大森：GitHub Actions自動テスト導入</li><li>@小泉・@田村：Confluence統合報告</li><li>@水谷：監視閾値再設定</li><li>@木下：ETL負荷見積最終化（PoC対応）</li></ul>"
          },
          "attachments": [],
          "replies": [
            {
              "id": "msg-prog-001-r1",
              "replyToId": "msg-prog-001",
              "createdDateTime": "2025-10-25T00:10:00Z",
              "lastModifiedDateTime": "2025-10-25T00:10:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-aoyama",
                  "displayName": "青山 玲奈（クラウド統括）",
                  "userPrincipalName": "rena.aoyama@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>Terraform更新反映済。<code>main</code>にマージ、LB設定も確認完了です。</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-prog-001-r2",
              "replyToId": "msg-prog-001",
              "createdDateTime": "2025-10-25T03:00:00Z",
              "lastModifiedDateTime": "2025-10-25T03:00:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-omori",
                  "displayName": "大森 直人（CI/CD担当）",
                  "userPrincipalName": "naoto.omori@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>GitHub Actions自動テスト導入完了。<code>pytest</code>結果をSlack通知する設定を追加しました。</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-prog-001-r3",
              "replyToId": "msg-prog-001",
              "createdDateTime": "2025-10-25T06:15:00Z",
              "lastModifiedDateTime": "2025-10-25T06:15:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-koizumi",
                  "displayName": "小泉 愛実",
                  "userPrincipalName": "manami.koizumi@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>Confluence統合完了。設計書・構成図・メタデータ辞書を統合済です。@田村 さん、AI共有ページの権限確認お願いします。</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-prog-001-r4",
              "replyToId": "msg-prog-001",
              "createdDateTime": "2025-10-25T08:00:00Z",
              "lastModifiedDateTime": "2025-10-25T08:00:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-tamura",
                  "displayName": "田村 亮介",
                  "userPrincipalName": "ryosuke.tamura@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>権限設定修正完了。<code>/AI_shared/metadata_v2.1</code> をAIチームに公開しました。</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-prog-001-r5",
              "replyToId": "msg-prog-001",
              "createdDateTime": "2025-10-26T00:00:00Z",
              "lastModifiedDateTime": "2025-10-26T00:00:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-mizutani",
                  "displayName": "水谷 翔（運用）",
                  "userPrincipalName": "sho.mizutani@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>ジョブ監視閾値を25分に変更、異常検知テストも完了。来週から新閾値で運用します。</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-prog-001-r6",
              "replyToId": "msg-prog-001",
              "createdDateTime": "2025-10-26T04:30:00Z",
              "lastModifiedDateTime": "2025-10-26T04:30:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-kinoshita",
                  "displayName": "木下 俊輔（ETL）",
                  "userPrincipalName": "shunsuke.kinoshita@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>ETL負荷見積完了。自治体C宿泊データ約900万件：CPU平均65%、GPU時短効果15%。詳細レポートを@藤原 さんに共有済。</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-prog-001-r7",
              "replyToId": "msg-prog-001",
              "createdDateTime": "2025-10-27T01:15:00Z",
              "lastModifiedDateTime": "2025-10-27T01:15:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-miyake",
                  "displayName": "三宅 悠人（チームリーダー）",
                  "userPrincipalName": "yuto.miyake@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>各担当、迅速な対応に感謝。本日夜にリリースリハーサルを実施し、<b>10/28夜間</b>の本番反映に備えます。報告書は10/29にPMO宛提出。</p>"
              },
              "attachments": []
            }
          ]
        },
        {
          "id": "msg-prog-002",
          "replyToId": null,
          "createdDateTime": "2025-10-27T02:20:00Z",
          "lastModifiedDateTime": "2025-10-27T02:20:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "運用自動化分科会の準備（10/27〜10/28）",
          "from": {
            "user": {
              "id": "u-hashimoto",
              "displayName": "橋本 翼（品質管理）",
              "userPrincipalName": "tsubasa.hashimoto@example.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<p>来週開始予定の「運用自動化分科会」初回議題案を共有します。</p><ul><li>ジョブ監視の自動リカバリ（再実行フロー）</li><li>成果物の自動アーカイブ</li><li>IaC更新時の自動差分通知（GitOps連携）</li></ul>"
          },
          "attachments": [
            {
              "id": "att-automation-agenda",
              "name": "automation_wg_agenda_v1.docx",
              "contentType": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
              "contentUrl": "https://example.sharepoint.com/sites/nec-kanko-dx/Shared%20Documents/automation_wg_agenda_v1.docx"
            }
          ],
          "replies": [
            {
              "id": "msg-prog-002-r1",
              "replyToId": "msg-prog-002",
              "createdDateTime": "2025-10-27T04:05:00Z",
              "lastModifiedDateTime": "2025-10-27T04:05:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-miyake",
                  "displayName": "三宅 悠人（チームリーダー）",
                  "userPrincipalName": "yuto.miyake@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>確認済。初回は10/30（木）15:00〜で調整します。PMO（@松下）にも展開します。</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-prog-002-r2",
              "replyToId": "msg-prog-002",
              "createdDateTime": "2025-10-27T04:30:00Z",
              "lastModifiedDateTime": "2025-10-27T04:30:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-aoyama",
                  "displayName": "青山 玲奈（クラウド統括）",
                  "userPrincipalName": "rena.aoyama@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>GitOps連携（Azure DevOps）パート担当します。Terraform差分検知サンプルを共有します。</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-prog-002-r3",
              "replyToId": "msg-prog-002",
              "createdDateTime": "2025-10-27T05:10:00Z",
              "lastModifiedDateTime": "2025-10-27T05:10:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-omori",
                  "displayName": "大森 直人（CI/CD担当）",
                  "userPrincipalName": "naoto.omori@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>CI/CD改善点（ログ整形・Slack通知）を発表資料にまとめます。</p>"
              },
              "attachments": []
            }
          ]
        }
      ]
    },
    {
      "id": "19:tech@thread.tacv2",
      "displayName": "💬 技術・課題共有",
      "messages": [
        {
          "id": "msg-tech-001",
          "replyToId": null,
          "createdDateTime": "2025-10-21T00:20:00Z",
          "lastModifiedDateTime": "2025-10-21T00:20:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "API試験公開準備（10/21〜10/25）",
          "from": {
            "user": {
              "id": "u-chen",
              "displayName": "陳 文傑（APIリード）",
              "userPrincipalName": "wenjie.chen@example.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<p>各位<br/>API試験公開（10/25予定）に向け、テスト用エンドポイント <code>/api/v1/visits/summary</code> の疎通確認を開始しました。@青山 玲奈 さん、LB設定は24日中反映で問題ないでしょうか？ @木下 俊輔 さん、ETL出力（CSV→Parquet）のサンプル確認希望です。<br/>📎 <i>api_test_request.json</i> を添付。</p>"
          },
          "attachments": [
            {
              "id": "att-api-test",
              "name": "api_test_request.json",
              "contentType": "application/json",
              "contentUrl": "https://example.sharepoint.com/sites/nec-kanko-dx/Shared%20Documents/api_test_request.json"
            }
          ],
          "replies": [
            {
              "id": "msg-tech-001-r1",
              "replyToId": "msg-tech-001",
              "createdDateTime": "2025-10-21T01:05:00Z",
              "lastModifiedDateTime": "2025-10-21T01:05:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-aoyama",
                  "displayName": "青山 玲奈（クラウド統括）",
                  "userPrincipalName": "rena.aoyama@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>ステージングでLBテスト済。本番反映は <b>10/23午前</b> に前倒しします。Terraform更新は <code>feature/lb_rule_v2</code> にpush済。</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-tech-001-r2",
              "replyToId": "msg-tech-001",
              "createdDateTime": "2025-10-21T02:10:00Z",
              "lastModifiedDateTime": "2025-10-21T02:10:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-kinoshita",
                  "displayName": "木下 俊輔（ETLリーダー）",
                  "userPrincipalName": "shunsuke.kinoshita@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>Parquetサンプルを <code>/etl/output/preview_20251021/</code> に配置。スキーマv2.1（<code>stay_duration</code>, <code>traffic_type</code>）に対応済。@白井 さん最終チェックお願いします。</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-tech-001-r3",
              "replyToId": "msg-tech-001",
              "createdDateTime": "2025-10-21T03:02:00Z",
              "lastModifiedDateTime": "2025-10-21T03:02:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-shirai",
                  "displayName": "白井 奏（データアーキテクト）",
                  "userPrincipalName": "kanade.shirai@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>確認しました。<code>stay_duration</code> は float→int へ統一をお願いします。<code>traffic_type</code> は文字列カテゴリでOK。10/22午前までに再出力で問題なし。</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-tech-001-r4",
              "replyToId": "msg-tech-001",
              "createdDateTime": "2025-10-22T00:40:00Z",
              "lastModifiedDateTime": "2025-10-22T00:40:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-kinoshita",
                  "displayName": "木下 俊輔（ETLリーダー）",
                  "userPrincipalName": "shunsuke.kinoshita@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>再出力完了。<code>parquet_v2.1_20251022</code> を共有しました。@陳 さん、API側でご確認を。</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-tech-001-r5",
              "replyToId": "msg-tech-001",
              "createdDateTime": "2025-10-22T04:15:00Z",
              "lastModifiedDateTime": "2025-10-22T04:15:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-chen",
                  "displayName": "陳 文傑（APIリード）",
                  "userPrincipalName": "wenjie.chen@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>受領。動作問題なし。<b>10/24午後</b>に試験公開へ切替ます。@青山 さん、LBルーティング変更タイミングをSlackでも連携ください。</p>"
              },
              "attachments": []
            }
          ]
        },
        {
          "id": "msg-tech-002",
          "replyToId": null,
          "createdDateTime": "2025-10-22T06:10:00Z",
          "lastModifiedDateTime": "2025-10-22T06:10:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "SHAP分析用データ提供（10/22〜10/24）",
          "from": {
            "user": {
              "id": "u-kaga",
              "displayName": "加賀 亮（AIチーム）",
              "userPrincipalName": "ryo.kaga@example.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<p>@白井 さん、SHAP分析用データ10万件×3セットの匿名化完了。<code>/ai_input/shap_dataset_v2.1.zip</code> に格納。ETL側で null 埋め・日付正規化をお願いします。週末から学習テスト開始予定。</p>"
          },
          "attachments": [],
          "replies": [
            {
              "id": "msg-tech-002-r1",
              "replyToId": "msg-tech-002",
              "createdDateTime": "2025-10-22T07:00:00Z",
              "lastModifiedDateTime": "2025-10-22T07:00:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-shirai",
                  "displayName": "白井 奏（データアーキテクト）",
                  "userPrincipalName": "kanade.shirai@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>対応中（<code>etl_shap_cleaner.py</code> 修正）。<code>used_date</code> のフォーマットは <code>YYYY-MM-DD</code> 統一で良いですか？</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-tech-002-r2",
              "replyToId": "msg-tech-002",
              "createdDateTime": "2025-10-22T07:12:00Z",
              "lastModifiedDateTime": "2025-10-22T07:12:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-kaga",
                  "displayName": "加賀 亮（AIチーム）",
                  "userPrincipalName": "ryo.kaga@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>はい、<code>YYYY-MM-DD</code> 統一でお願いします。時系列特徴量で使用します。</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-tech-002-r3",
              "replyToId": "msg-tech-002",
              "createdDateTime": "2025-10-23T01:00:00Z",
              "lastModifiedDateTime": "2025-10-23T01:00:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-kinoshita",
                  "displayName": "木下 俊輔（ETLリーダー）",
                  "userPrincipalName": "shunsuke.kinoshita@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>整形完了。<code>/shared/etl/shap_ready_20251023.parquet</code>（2.8GB）を配置。@加賀 さん、@藤原 さん取り込み可か確認お願いします。</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-tech-002-r4",
              "replyToId": "msg-tech-002",
              "createdDateTime": "2025-10-23T02:05:00Z",
              "lastModifiedDateTime": "2025-10-23T02:05:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-fujiwara",
                  "displayName": "藤原 大輝（AIリーダー）",
                  "userPrincipalName": "daiki.fujiwara@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>取り込みOK。今夜からSHAPトレーニングを実施。A100でバッチ分割して回します。迅速対応ありがとうございます。</p>"
              },
              "attachments": []
            }
          ]
        },
        {
          "id": "msg-tech-003",
          "replyToId": null,
          "createdDateTime": "2025-10-23T13:30:00Z",
          "lastModifiedDateTime": "2025-10-23T13:30:00Z",
          "messageType": "message",
          "importance": "normal",
          "subject": "夜間ジョブの監視アラート（10/23〜10/25）",
          "from": {
            "user": {
              "id": "u-mizutani",
              "displayName": "水谷 翔（運用担当）",
              "userPrincipalName": "sho.mizutani@example.com"
            }
          },
          "body": {
            "contentType": "html",
            "content": "<p>昨夜のジョブログで <code>etl_nightly_traffic_20251023</code> がタイムアウト。再実行で正常終了。閾値設定を見直します。@橋本 さん、品質ログ上も異常なしで良いでしょうか？</p>"
          },
          "attachments": [],
          "replies": [
            {
              "id": "msg-tech-003-r1",
              "replyToId": "msg-tech-003",
              "createdDateTime": "2025-10-24T23:15:00Z",
              "lastModifiedDateTime": "2025-10-24T23:15:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-hashimoto",
                  "displayName": "橋本 翼（品質管理）",
                  "userPrincipalName": "tsubasa.hashimoto@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>リトライ後に全件処理を確認。セキュリティログも異常なし。PR時に <code>threshold_reconfig.yaml</code> のレビュー依頼をお願いします。</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-tech-003-r2",
              "replyToId": "msg-tech-003",
              "createdDateTime": "2025-10-24T02:05:00Z",
              "lastModifiedDateTime": "2025-10-24T02:05:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-mizutani",
                  "displayName": "水谷 翔（運用担当）",
                  "userPrincipalName": "sho.mizutani@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>PR #245 を作成。処理時間上限を <b>15→25分</b> に拡張。@大森 さん、自動テスト連携の影響有無を確認お願いします。</p>"
              },
              "attachments": []
            },
            {
              "id": "msg-tech-003-r3",
              "replyToId": "msg-tech-003",
              "createdDateTime": "2025-10-24T04:45:00Z",
              "lastModifiedDateTime": "2025-10-24T04:45:00Z",
              "messageType": "message",
              "from": {
                "user": {
                  "id": "u-omori",
                  "displayName": "大森 直人（CI/CD担当）",
                  "userPrincipalName": "naoto.omori@example.com"
                }
              },
              "body": {
                "contentType": "html",
                "content": "<p>影響なし。GitHub Actionsのタイムアウトは30分設定。今夜、自動テストフロー追加をマージ予定です。</p>"
              },
              "attachments": []
            }
          ]
        }
      ]
    }
  ]
}
```

## outlook予定表第二週
```
想定されるOutlook予定（JST）
2025-10-23（木）

21:00–23:00｜SHAPトレーニング初回実行ウィンドウ
主催：AIチーム（藤原）／参加：加賀・白井・木下
備考：「今夜からSHAPトレーニング」宣言に基づく初回回し

2025-10-24（金）

10:00–11:00｜全体会議（第4週・進捗／リスク#12／v1.2準備）
主催：石田（PM）／参加：全体

15:00–16:00｜API試験公開・切替ウィンドウ
主催：陳（API）／参加：青山（LB）、木下、白井 ほか
備考：LBルーティング変更と疎通確認

2025-10-27（月）

21:00–22:00｜v1.2 リリース・リハーサル
主催：三宅（データ基盤）／参加：青山・大森・水谷・木下 ほか

2025-10-28（火）

09:00–09:30｜監視閾値切替（25分へ）運用切替ブリーフィング
主催：水谷（運用）／参加：橋本・大森

22:00–24:00｜v1.2 リリース本番（夜間反映）
主催：三宅／参加：青山・大森・水谷・木下・PMO（松下）
備考：作業・検証・ロールバック手順確認、完了報告は10/29提出

2025-10-30（木）

15:00–16:00｜運用自動化分科会 #1（キックオフ）
主催：三宅／参加：橋本（品質）、青山（IaC/GitOps）、大森（CI/CD）
議題：自動リカバリ／成果物自動アーカイブ／IaC差分通知（GitOps）
```
```json
{
  "id": "AAMkADkya...-allhands-20251024",
  "subject": "【全体】第4週 全体会議：進捗／リスク#12／v1.2準備",
  "bodyPreview": "議事：進捗、リスク#12対応、v1.2リリース準備。",
  "start": { "dateTime": "2025-10-24T10:00:00", "timeZone": "Asia/Tokyo" },
  "end":   { "dateTime": "2025-10-24T11:00:00", "timeZone": "Asia/Tokyo" },
  "location": { "displayName": "Microsoft Teams 会議" },
  "isOnlineMeeting": true,
  "onlineMeetingProvider": "teamsForBusiness",
  "attendees": [
    { "type": "required", "emailAddress": { "name": "石田 智久", "address": "tomohisa.ishida@example.com" } },
    { "type": "required", "emailAddress": { "name": "三宅 悠人", "address": "yuto.miyake@example.com" } },
    { "type": "optional", "emailAddress": { "name": "松下 翔太", "address": "shota.matsushita@example.com" } }
  ],
  "organizer": { "emailAddress": { "name": "石田 智久", "address": "tomohisa.ishida@example.com" } },
  "reminderMinutesBeforeStart": 15,
  "categories": ["全体会議"]
}
{
  "id": "AAMkADkya...-api-trial-20251024",
  "subject": "API試験公開・切替（/api/v1/visits/summary）",
  "bodyPreview": "LBルーティング変更・疎通確認。Slack併用連絡。",
  "start": { "dateTime": "2025-10-24T15:00:00", "timeZone": "Asia/Tokyo" },
  "end":   { "dateTime": "2025-10-24T16:00:00", "timeZone": "Asia/Tokyo" },
  "location": { "displayName": "オンライン（Teams）" },
  "isOnlineMeeting": true,
  "onlineMeetingProvider": "teamsForBusiness",
  "attendees": [
    { "type": "required", "emailAddress": { "name": "陳 文傑", "address": "wenjie.chen@example.com" } },
    { "type": "required", "emailAddress": { "name": "青山 玲奈", "address": "rena.aoyama@example.com" } },
    { "type": "optional", "emailAddress": { "name": "木下 俊輔", "address": "shunsuke.kinoshita@example.com" } },
    { "type": "optional", "emailAddress": { "name": "白井 奏", "address": "kanade.shirai@example.com" } }
  ],
  "organizer": { "emailAddress": { "name": "陳 文傑", "address": "wenjie.chen@example.com" } },
  "reminderMinutesBeforeStart": 10,
  "categories": ["API","リリース"]
}
{
  "id": "AAMkADkya...-rehearsal-20251027",
  "subject": "v1.2 リリース・リハーサル",
  "bodyPreview": "手順確認・自動テスト・ロールバック演習。",
  "start": { "dateTime": "2025-10-27T21:00:00", "timeZone": "Asia/Tokyo" },
  "end":   { "dateTime": "2025-10-27T22:00:00", "timeZone": "Asia/Tokyo" },
  "location": { "displayName": "Microsoft Teams 会議" },
  "isOnlineMeeting": true,
  "attendees": [
    { "type": "required", "emailAddress": { "name": "三宅 悠人", "address": "yuto.miyake@example.com" } },
    { "type": "required", "emailAddress": { "name": "大森 直人", "address": "naoto.omori@example.com" } },
    { "type": "required", "emailAddress": { "name": "水谷 翔", "address": "sho.mizutani@example.com" } },
    { "type": "optional", "emailAddress": { "name": "青山 玲奈", "address": "rena.aoyama@example.com" } }
  ],
  "organizer": { "emailAddress": { "name": "三宅 悠人", "address": "yuto.miyake@example.com" } },
  "reminderMinutesBeforeStart": 30,
  "categories": ["リリース準備"]
}
{
  "id": "AAMkADkya...-release-20251028",
  "subject": "【本番】v1.2 リリース（夜間反映）",
  "bodyPreview": "反映・検証・監視。完了報告は10/29 PMO提出。",
  "start": { "dateTime": "2025-10-28T22:00:00", "timeZone": "Asia/Tokyo" },
  "end":   { "dateTime": "2025-10-29T00:00:00", "timeZone": "Asia/Tokyo" },
  "location": { "displayName": "オンライン（Teams）" },
  "isOnlineMeeting": true,
  "onlineMeetingProvider": "teamsForBusiness",
  "attendees": [
    { "type": "required", "emailAddress": { "name": "三宅 悠人", "address": "yuto.miyake@example.com" } },
    { "type": "required", "emailAddress": { "name": "青山 玲奈", "address": "rena.aoyama@example.com" } },
    { "type": "required", "emailAddress": { "name": "大森 直人", "address": "naoto.omori@example.com" } },
    { "type": "required", "emailAddress": { "name": "水谷 翔", "address": "sho.mizutani@example.com" } },
    { "type": "optional", "emailAddress": { "name": "松下 翔太", "address": "shota.matsushita@example.com" } }
  ],
  "organizer": { "emailAddress": { "name": "三宅 悠人", "address": "yuto.miyake@example.com" } },
  "reminderMinutesBeforeStart": 60,
  "categories": ["本番リリース"]
}
{
  "id": "AAMkADkya...-threshold-20251028",
  "subject": "監視閾値切替（15→25分）ブリーフィング",
  "bodyPreview": "夜間ジョブの閾値変更に伴う運用切替説明。",
  "start": { "dateTime": "2025-10-28T09:00:00", "timeZone": "Asia/Tokyo" },
  "end":   { "dateTime": "2025-10-28T09:30:00", "timeZone": "Asia/Tokyo" },
  "location": { "displayName": "Microsoft Teams 会議" },
  "isOnlineMeeting": true,
  "attendees": [
    { "type": "required", "emailAddress": { "name": "水谷 翔", "address": "sho.mizutani@example.com" } },
    { "type": "required", "emailAddress": { "name": "橋本 翼", "address": "tsubasa.hashimoto@example.com" } },
    { "type": "optional", "emailAddress": { "name": "大森 直人", "address": "naoto.omori@example.com" } }
  ],
  "organizer": { "emailAddress": { "name": "水谷 翔", "address": "sho.mizutani@example.com" } },
  "reminderMinutesBeforeStart": 10,
  "categories": ["運用"]
}
{
  "id": "AAMkADkya...-automationwg-20251030",
  "subject": "運用自動化分科会 #1（キックオフ）",
  "bodyPreview": "自動リカバリ／成果物自動アーカイブ／IaC差分通知。",
  "start": { "dateTime": "2025-10-30T15:00:00", "timeZone": "Asia/Tokyo" },
  "end":   { "dateTime": "2025-10-30T16:00:00", "timeZone": "Asia/Tokyo" },
  "location": { "displayName": "Microsoft Teams 会議" },
  "isOnlineMeeting": true,
  "attendees": [
    { "type": "required", "emailAddress": { "name": "三宅 悠人", "address": "yuto.miyake@example.com" } },
    { "type": "required", "emailAddress": { "name": "橋本 翼", "address": "tsubasa.hashimoto@example.com" } },
    { "type": "required", "emailAddress": { "name": "青山 玲奈", "address": "rena.aoyama@example.com" } },
    { "type": "optional", "emailAddress": { "name": "大森 直人", "address": "naoto.omori@example.com" } }
  ],
  "organizer": { "emailAddress": { "name": "三宅 悠人", "address": "yuto.miyake@example.com" } },
  "reminderMinutesBeforeStart": 15,
  "categories": ["分科会","運用自動化"]
}
{
  "id": "AAMkADkya...-shap-20251023",
  "subject": "SHAPトレーニング初回実行",
  "bodyPreview": "A100でバッチ分割。データ：shap_ready_20251023.parquet。",
  "start": { "dateTime": "2025-10-23T21:00:00", "timeZone": "Asia/Tokyo" },
  "end":   { "dateTime": "2025-10-23T23:00:00", "timeZone": "Asia/Tokyo" },
  "location": { "displayName": "リモート（GPUノード）" },
  "attendees": [
    { "type": "required", "emailAddress": { "name": "藤原 大輝", "address": "daiki.fujiwara@example.com" } },
    { "type": "required", "emailAddress": { "name": "加賀 亮", "address": "ryo.kaga@example.com" } },
    { "type": "optional", "emailAddress": { "name": "白井 奏", "address": "kanade.shirai@example.com" } },
    { "type": "optional", "emailAddress": { "name": "木下 俊輔", "address": "shunsuke.kinoshita@example.com" } }
  ],
  "organizer": { "emailAddress": { "name": "藤原 大輝", "address": "daiki.fujiwara@example.com" } },
  "reminderMinutesBeforeStart": 10,
  "categories": ["AI","学習"]
}
```
