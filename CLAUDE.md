# CLAUDE.md - portfolio 固有ルール

> 共通ルール（ブランチ命名・コミット規約・CHANGELOG更新等）は `~/.claude/CLAUDE.md` を参照

## プロジェクト概要

GitHub Pages で公開するポートフォリオサイト

| 項目 | 値 |
|:---|:---|
| 公開URL | https://dhc4mens.github.io/portfolio/ |
| リポジトリ | https://github.com/dhc4mens/portfolio |
| デプロイ | GitHub Pages（main push後 1-2分で自動反映） |
| 構成 | index.html 単一ファイル |

---

## ディレクトリ構成

```
portfolio/
├── CLAUDE.md             # ← このファイル（固有ルール）
├── README.md             # 公開用（シンプルに保つ）
├── CHANGELOG.md
├── TODO.md
├── index.html            # メインファイル（編集対象）
├── .gitignore
├── .github/
│   ├── ISSUE_TEMPLATE/
│   └── PULL_REQUEST_TEMPLATE.md
└── scripts/
    └── setup-labels.sh
```

---

## よくある更新パターン

### 資格取得時
1. 資格ステータス: `cert-status planned` → `cert-status acquired`
2. AWS認定資格数: `pr-stat-number` の数字を +1
3. 学習セクション: 次の目標に更新

### 新規プロジェクト追加
- `id="projects"` セクション内に追加
- 最新は `project-card featured` クラスで目立たせる

### スキル追加
- `id="skills"` セクション内
- 新規は `experience-level new` クラスで赤バッジ

---

## CSSクラス一覧

| クラス | 用途 |
|:---|:---|
| `cert-status acquired` | 取得済（緑バッジ） |
| `cert-status planned` | 予定（オレンジバッジ） |
| `experience-level` | 経験年数（紫バッジ） |
| `experience-level new` | 新規スキル（赤バッジ） |
| `project-card` | 通常プロジェクト（緑ボーダー） |
| `project-card featured` | 注目案件（赤ボーダー） |
| `tech-tag` | 技術タグ（紫） |
| `tech-tag ai` | AI関連タグ（赤） |

---

## セクション構造

```html
<section id="pr">             <!-- 自己PR -->
<section id="skills">         <!-- 技術スキル -->
<section id="projects">       <!-- プロジェクト実績 -->
<section id="learning">       <!-- 学習・今後 -->
<section id="certifications"><!-- 資格・認定 -->
```

---

## 注意事項（プロジェクト固有）

- README.md は公開対象。シンプルに保つ（内部情報はこのCLAUDE.mdに）
- 反映確認時は Ctrl+Shift+R でキャッシュクリア

---

## 現在の状態

- AWS認定資格: 7個（CLF, SAA, SOA, DVA, AIF, DEA, MLA）
- 次の目標: SAP / DOP（2026年後半）

---

## 参照リンク

- [CHANGELOG.md](CHANGELOG.md)
- [TODO.md](TODO.md)
- Issues: https://github.com/dhc4mens/portfolio/issues

---

最終更新: 2026-04-17
