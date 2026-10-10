# docs/

ポートフォリオサイトに関するドキュメント。

## 構成

| フォルダ/ファイル | 内容 |
|:---|:---|
| `adr/` | Architecture Decision Records — 設計判断の記録 |

## 更新タイミング

- 重要な設計判断が発生したら `adr/` に ADR を追加する
- このファイルに新しいフォルダ/ファイルを追記する

## リポの構成

```
portfolio/
├── index.html            # サイト本体（CSS・JS もインライン。編集はほぼここだけ）
├── README.md             # 公開用（シンプルに保つ）
├── CLAUDE.md             # Claude Code 向けの作法（これも公開される）
├── CHANGELOG.md
├── TODO.md               # GitHub Issue への導線
├── .gitignore
├── .claude/
│   └── settings.json     # Claude Code のプロジェクト設定
├── docs/
│   ├── README.md         # このファイル
│   └── adr/              # 設計判断の記録
├── scripts/
│   ├── README.md
│   └── setup-labels.sh
└── .github/
    ├── ISSUE_TEMPLATE/
    ├── PULL_REQUEST_TEMPLATE.md
    └── workflows/        # pr-gate・release・dependabot-digest
```

## index.html のセクション構造

`site-header` の後に次の順で並ぶ。各セクションには `class="section"` が付く。

```html
<header class="hero">         <!-- 氏名・肩書き・連絡先・数字（pr-stats） -->
<section id="pr">             <!-- 自己PR -->
<section id="skills">         <!-- 技術スキル -->
<section id="projects">       <!-- プロジェクト実績 -->
<section id="learning">       <!-- 学習・今後 -->
<section id="certifications"><!-- 資格・認定 -->
```

## CSS クラスの一覧

正本は index.html。クラスを足したり意味を変えたりした時は、この表も直す。

| クラス | 用途 |
|:---|:---|
| `section-head` / `section-no` / `section-en` | セクション見出し（左列・番号・英字ラベル） |
| `pr-stats` / `pr-stat-number` | ヒーロー下の数字4つ |
| `pr-highlight` / `pr-highlight-label` | 自己PR内の実績ハイライト |
| `ai-highlight` | AI関連カードの強調色（朱）。**資格欄では先頭カードの2行ぶち抜き（`grid-row: span 2`）も兼ねる**ので、他の資格カードに付け外ししない |
| `cert-status acquired` | 取得済（細枠のラベル） |
| `cert-status planned` | 予定（朱色の枠） |
| `cert-status expired` | 失効（点線枠・グレー） |
| `cert-tier` | 資格の階層ブロック（Associate・LPIC Level 2 等） |
| `cert-tier top` | 最上位階層の強調枠（`ai-highlight` カード内は朱、それ以外は墨色の左線） |
| `cert-tier foundational` | Foundational 階層（小さめ・グレー） |
| `cert-top-item` | 最上位階層内の資格1件 |
| `cert-tier-list` | 階層内の資格名リスト |
| `experience-level` | 経験年数（等幅・グレー） |
| `experience-level new` | 新規スキル（朱色） |
| `project-card` | プロジェクト1件（期間｜本文の2列） |
| `project-body` / `project-meta` | プロジェクトの本文（右列）／期間・体制・領域（左列） |
| `project-card featured` | 注目案件（期間が朱色） |
| `featured-badge` / `featured-badge live` | 状態ラベル（`live` は点滅ドット付き） |
| `link-btn` / `link-btn primary` | デモ等へのリンクボタン |
| `tech-tag` | 技術タグ（等幅・細枠） |
| `tech-tag ai` | AI関連タグ（朱色） |

## 反映の確かめ方

main にマージすると GitHub Pages に1〜2分で出る。ブラウザのキャッシュが残るので、Ctrl+Shift+R で読み直して確かめる。
