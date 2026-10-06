# Changelog

All notable changes to portfolio will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [Unreleased]

### Changed
- **ビジュアルを全面刷新（AI生成感の除去・#37）**
  - 原因だった紫グラデーション（`#667eea → #764ba2`）・ピンクグラデーション・Flat UI 系パレット・見出し17箇所の絵文字・全要素の角丸カードを撤去
  - 生成り地＋墨色＋朱1色のエディトリアル調に変更。書体は IBM Plex Sans JP（本文）＋ IBM Plex Mono（番号・ラベル・数字）
  - レイアウト: 左サイドバーを廃止し、上部固定ナビ＋ヒーロー（氏名・肩書き・連絡先・数字）＋「見出し左列／本文右列」の2カラムに。カードの代わりに罫線と余白で区切る
  - プロジェクト実績は「期間｜本文」の年表形式、概要・成果・役割は定義リストに。CloudLogAI の「本番運用中」に稼働ドットを追加
  - 小さい文字の色をコントラスト比 4.5 以上に調整。見出しは文節で折り返す（`word-break: auto-phrase`）
  - 文言・実績・資格は全件維持（刷新前後の表示テキストを突き合わせて確認）
  - CLAUDE.md に「デザインの約束」を追加し、CSS クラス一覧・セクション構造を新構造に更新。陳腐化していた「現在の状態」（資格7個）を削除
- **Linux / 仮想化の資格を階層別表示に変更し、VCP を「失効」表記に**
  - LPIC-3 Security (303) を最上位として枠で強調、LPIC-2 をその下に配置（従来は LPIC-2 が先頭で上下関係が読めなかった）
  - VCP2019-DCV は再認定しておらず失効しているため、削除せずグレーの「失効」バッジに変更（取得時点の知識の証明として残す）
  - 強調枠のクラスを `cert-tier professional` → `cert-tier top`（`cert-pro-item` → `cert-top-item`）に汎用化。枠色は `ai-highlight` カード内で赤、それ以外は青紫にして DOP との主従を保つ
  - CLAUDE.md の資格取得時の手順と CSS クラス一覧を更新
- **AWS認定資格を階層別（Professional / Associate / Foundational）の表示に変更**
  - 8資格を同じ重さの「取得済」バッジで並べていたため、DOP（Professional）が埋もれていた
  - Professional は赤枠カードで強調、Associate ×5 は1ブロックに圧縮、Foundational ×2 は小さめのグレーで表示。バッジは階層ごとに1つに集約
  - 資格は全件残す（SES の募集要項で「SAA 以上」などキーワード照合されるため）。見出しを「AWS認定資格（8）」に変更
  - CLAUDE.md の資格取得時の更新手順と CSS クラス一覧を新構造に合わせて更新

### Added
- **AWS Certified DevOps Engineer - Professional（DOP-C02）取得を反映（2026-09-26 合格）**
  - 資格・認定: AWS認定資格の先頭に DOP（取得済・2026年9月取得）を追加
  - 自己PR: AWS認定資格の数を 7 → 8 に更新、本文に DOP 取得の一文を追記
  - 学習・今後: DOP 目標カードを削除し、SAP-C02 を「2026年11月受験予定／Professional 2冠目へ」に更新。「SRE深化」を「SRE・DevOps深化」に改め、DOP の知見を本番運用へ展開する旨を追記

### Fixed
- **dependabot-digest.yml の startup failure を解消**（notify-on-failure ジョブを削除）
  - 7/13以降、portfolioの週次digestが "workflow file issue"（startup failure）で失敗していた
  - 根本原因: portfolioは **public** リポで、`notify-on-failure` が参照する reusable workflow は **private** の repo-setup-template にある。**public リポは private リポの reusable workflow を呼べない**（"workflow not found" でパース失敗）ため。同じ参照でも private の daihou-sre で動くのはこの差
  - 修正: portfolioから notify-on-failure ジョブを削除（public リポでは構造的に使えない）。digest本体は正常動作に戻る。※当初「stale parse」と誤診し再パース強制を試みたが無効だった経緯を経て根本原因を特定

### Changed
- **SREダッシュボードのデモリンクを外部公開版（ext-sre-dash）へ差し替え＋デモ用ログイン情報を併記**
  - リンク先を `int-sre-dash.daihou-llc.com/demo/`（内部向け）から `ext-sre-dash.daihou-llc.com/`（外部公開用・ルート配信）へ変更
  - デモ用クレデンシャル（`ext-guest@daihou-llc.com`）をカード内に併記。従来はクレデンシャルがどこにも公開されておらず、訪問者がCognitoログイン画面で止まる実質死にリンクだったため
  - 表示内容はサニタイズ済みの静的ページである旨の注記を追加
- **ポートフォリオ定期更新 2026-06（#6）**
  - SRE基盤カード成果: Issue駆動開発体制整備（Issue/PRテンプレート・ラベル・GitHub Flow統一）・標準リポジトリテンプレート作成（repo-setup-template）・GitHub Projects V2 横断管理ボード運用 を追記
  - SRE基盤カード役割: 「開発プロセス整備」を追記
  - CloudLogAI カード成果: マルチテナント対応完了・顧客管理CLI（customer-manage.fish）完成 を追記

### Fixed
- **プロジェクト表示順修正（#14）**
  - インフラエンジニア（2001-2010）とデータセンター仮想化基盤（2010-2020）の順序を修正
  - 新しい順（降順）に合わせ、データセンター仮想化基盤 → インフラエンジニアの順に変更

### Added
- **直近案件・初期キャリア追加・スキル更新（#12）**
  - プロジェクト: 直近案件（2026/02-05）オンプレプリントサービス基盤更改AWS環境構築（Terraform IaC）を追加
  - プロジェクト: 初期キャリア（2001/04-2010/04）インフラエンジニア（OS/NW/Firewall）をデータセンター仮想化基盤の前に追加
  - スキル: セキュリティ・NWにAWSセキュリティ（GuardDuty/Security Hub/WAF/Config/CloudTrail/KMS/SecretsManager）を追加
  - 学習: SRE深化の「カオスエンジニアリング実践」を削除してシンプル化

### Changed
- **SRE実績を最新化（Lambda@Edge認証・drift検知・tfstate層分離）**
  - 自己PR: SRE基盤構築実績ハイライトにinfra/app層分離・Lambda@Edge Cognito認証・週次drift検知を追記
  - プロジェクト: daihou-sre の成果にLambda@Edge Cognito認証基盤（SecretsManager統合）・OIDC IAMロール保護設計を追記
  - プロジェクト: daihou-sre の技術タグに Lambda@Edge / Cognito / SecretsManager を追加
  - 学習・今後: DOP目標を「2026年夏」に具体化・SAP-C02を新規追加・SRE深化の内容を更新

### Added
- **SRE実績・スキルセクション最新化（#8）**
  - 自己PR: だいほう合同会社創業（2025年7月）・SRE基盤構築実績ハイライト追加
  - スキル: Terraform詳細更新（tfstate層分離・drift検知CI・OIDC）・ECS Fargate・GitHub Actions追加
  - スキル: Python に FastAPI 追加
  - プロジェクト: daihou-sre SRE基盤構築事例を新規追加（最新）
  - プロジェクト: CloudLogAI を SLI/SLO・エラーバジェット・本番運用中に更新
  - 学習・今後: SageMaker/MLOps → DOP-C02取得・SRE深化・Python(boto3)・AI活用拡大 に更新

### Added
- **Issue駆動開発の土台整備（2026-04-17）**
  - `.github/ISSUE_TEMPLATE/`（bug_report / feature_request / chore / config.yml）
  - `.github/PULL_REQUEST_TEMPLATE.md`
  - `scripts/setup-labels.sh`（type/priority/status 計10ラベル一括作成）
  - CLAUDE.md を共通ルール参照形式に整理
  - CHANGELOG.md / TODO.md 新規作成
  - テンプレートリポジトリ（dhc4mens/repo-setup-template）から展開

---

## 既存の更新履歴

（GitHub Pagesリリース以降の更新は今後ここに記録）
