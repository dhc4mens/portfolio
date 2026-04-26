# Changelog

All notable changes to portfolio will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [Unreleased]

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
