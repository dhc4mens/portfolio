# portfolio — このリポで毎ターン要る事実

## 事実

- 🔴 リポは **PUBLIC**。README・この CLAUDE.md・CHANGELOG・docs・コミットメッセージ・PR 本文まで、リポのすべてが公開される。内部向けの情報（採用や営業の事情など）はどこにも書かない
- GitHub Pages（main から）で公開する。main にマージすると1〜2分で https://dhc4mens.github.io/portfolio/ に出る
- サイトは `index.html` 1ファイル（CSS・JS もインライン）。編集はほぼここだけ

## 作法

### 資格を取った時

1. 資格は階層別（`cert-tier top` / `cert-tier` / `cert-tier foundational`）に置く
   - 最上位（AWS Professional・LPIC-3 等）: `cert-tier top` 内に `cert-top-item` を1つ追加（資格名＋`cert-status acquired`＋補足）
   - AWS Associate / Foundational: 該当 `cert-tier-list` に `<li>` を追加し、ラベルの `×N` を +1
   - 失効した資格は消さず `cert-status expired`（グレーの「失効」バッジ）にする
2. AWS認定資格数: `pr-stat-number` と見出し「AWS認定資格（N）」の数字を +1
3. 学習セクション: 次の目標に更新

### プロジェクトを足す時

- 並び順: **featured（進行中）を先頭、その後は終了日の新しい順**（開始日順ではない）
- 構成: `<article class="project-card">` の中に `div.project-body`（`h3` ＋ `dl.project-description`（概要・成果・役割）＋ `tech-tags`）→ `div.project-meta`（`project-period` ＋ 体制・領域の `<span>`）の順で書く
  - 本文を先に書くのは読み上げ順のため。期間はグリッド指定で左列に出る
  - `project-body` で包み忘れると、h3・dl・タグがグリッドに直接並んで崩れる
- 最新・注目は `project-card featured`（期間が朱色になる）。状態は `featured-badge`、稼働中は `featured-badge live`（点滅ドット付き）

### スキルを足す時

- `id="skills"` セクション内。新規は `experience-level new`（経験年数の表示が朱色になる）

### デザインの約束（#37）

- 配色と書体は `:root` の CSS 変数だけを使う（**変数の一覧は index.html の `:root` が正本**。ここに写さない）
- アクセントは朱（`--accent`）の1色だけ
- 書体は IBM Plex Sans JP（本文）＋ IBM Plex Mono（番号・ラベル・数字）
- 小さい文字の色は背景（`--paper`）に対してコントラスト比 4.5 以上を保つ。色を変える時は測り直す
- 番号（`section-no` の 01〜05、`learning-no` の 01〜03）は手書きの連番。項目を増減したら振り直す
- `ai-highlight` は資格欄では先頭カードの2行ぶち抜き（`grid-row: span 2`）も兼ねる。他の資格カードに付け外ししない

### その他

- ファイルを足す・消す・リネームした時は、`docs/README.md` の「リポの構成」を直す（ルートの README.md は公開用なので一覧を足さない）。ディレクトリを作ったら、そこにも README を置く
- CSS クラスを足したり意味を変えたりした時は、`docs/README.md` の一覧も直す

## やらないこと

- 色を直書きしない。旧パレット（`#667eea` / `#764ba2` 等）・グラデーション・見出しの絵文字を使わない（「AIで作った感」の主因だったため）
