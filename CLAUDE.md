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
1. 資格は階層別（`cert-tier top` / `cert-tier` / `cert-tier foundational`）に置く
   - 最上位（AWS Professional・LPIC-3 等）: `cert-tier top` 内に `cert-top-item` を1つ追加（資格名＋`cert-status acquired`＋補足）
   - AWS Associate / Foundational: 該当 `cert-tier-list` に `<li>` を追加し、ラベルの `×N` を +1
   - 失効した資格は消さず `cert-status expired`（グレーの「失効」バッジ）にする
2. AWS認定資格数: `pr-stat-number` と見出し「AWS認定資格（N）」の数字を +1
3. 学習セクション: 次の目標に更新

### 新規プロジェクト追加
- 並び順: **featured（進行中）を先頭、その後は終了日の新しい順**（開始日順ではない）
- 構成: `<article class="project-card">` の中に `div.project-body`（`h3` ＋ `dl.project-description`（概要・成果・役割）＋ `tech-tags`）→ `div.project-meta`（`project-period` ＋ 体制・領域の `<span>`）の順で書く
  - 本文を先に書くのは読み上げ順のため。期間はグリッド指定で左列に出る
  - `project-body` で包み忘れると、h3・dl・タグがグリッドに直接並んで崩れる
- 最新・注目は `project-card featured`（期間が朱色になる）。状態は `featured-badge`、稼働中は `featured-badge live`（点滅ドット付き）

### スキル追加
- `id="skills"` セクション内
- 新規は `experience-level new`（経験年数の表示が朱色になる）

---

## デザインの約束（#37）

- 配色と書体は `:root` の CSS 変数だけを使い、色を直書きしない（**変数の一覧は index.html の `:root` が正本**。ここに写さない）
- アクセントは朱（`--accent`）の1色だけ。**旧パレット（`#667eea` / `#764ba2` 等）・グラデーション・見出しの絵文字は使わない**（「AIで作った感」の主因だったため）
- 書体は IBM Plex Sans JP（本文）＋ IBM Plex Mono（番号・ラベル・数字）
- 小さい文字の色は背景（`--paper`）に対してコントラスト比 4.5 以上を保つ。色を変える時は測り直す
- 番号（`section-no` の 01〜05、`learning-no` の 01〜03）は手書きの連番。項目を増減したら振り直す

## CSSクラス一覧

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

---

## セクション構造

```html
<header class="hero">         <!-- 氏名・肩書き・連絡先・数字（pr-stats） -->
<section id="pr">             <!-- 自己PR -->
<section id="skills">         <!-- 技術スキル -->
<section id="projects">       <!-- プロジェクト実績 -->
<section id="learning">       <!-- 学習・今後 -->
<section id="certifications"><!-- 資格・認定 -->
```

---

## README 更新ルール

ファイル操作時は同階層の `README.md` も合わせて更新すること:

| 操作 | README への反映 |
|:---|:---|
| ファイル**追加** | 同ディレクトリの README.md の一覧・説明に追記 |
| ファイル**削除・リネーム** | README.md から該当エントリを削除・修正 |
| ディレクトリ**新規作成** | README.md を新規作成し、親ディレクトリの README.md にも追記 |

---

## 注意事項（プロジェクト固有）

- README.md は公開対象。シンプルに保つ（内部情報はこのCLAUDE.mdに）
- 反映確認時は Ctrl+Shift+R でキャッシュクリア

---

## 参照リンク

- [CHANGELOG.md](CHANGELOG.md)
- [TODO.md](TODO.md)
- Issues: https://github.com/dhc4mens/portfolio/issues

---

最終更新: 2026-10-07
