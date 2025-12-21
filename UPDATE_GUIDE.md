# ポートフォリオ更新ガイド

## 📋 概要

| 項目 | 値 |
|------|-----|
| URL | https://dhc4mens.github.io/portfolio/ |
| リポジトリ | https://github.com/dhc4mens/portfolio |
| デプロイ | GitHub Pages（mainブランチpushで自動） |
| ファイル | `index.html`（単一ファイル構成） |

---

## 🔄 更新フロー（全体像）

```
┌─────────────────┐
│ 1. ファイル編集  │  ← index.html を修正
└────────┬────────┘
         ↓
┌─────────────────┐
│ 2. Git コミット  │  ← ローカルに保存
└────────┬────────┘
         ↓
┌─────────────────┐
│ 3. Git プッシュ  │  ← GitHub に送信
└────────┬────────┘
         ↓
┌─────────────────┐
│ 4. 自動デプロイ  │  ← GitHub Pages が自動で実行（1-2分）
└────────┬────────┘
         ↓
┌─────────────────┐
│ 5. 公開ページ更新 │  ← https://dhc4mens.github.io/portfolio/
└─────────────────┘
```

---

## 📝 手順詳細

### Step 1: リポジトリに移動 & 最新取得

```fish
cd ~/portfolio
git pull origin main
```

### Step 2: index.html を編集

**方法A: Claude経由（推奨）**
```
Claudeに「ポートフォリオを更新したい」と依頼
→ MCP経由で直接編集してもらう
```

**方法B: 手動編集**
```fish
code index.html   # VSCode
# または
vim index.html    # vim
```

### Step 3: 変更内容を確認

```fish
git status                  # 変更ファイル一覧
git diff index.html         # 差分表示
```

### Step 4: コミット & プッシュ

```fish
git add index.html UPDATE_GUIDE.md   # 変更ファイルをステージング
git commit -m "update: 変更内容を簡潔に"
git push origin main
```

**コミットメッセージ例:**
```
update: DEA資格を取得済みに変更
feat: 新規プロジェクト追加
fix: タイポ修正
docs: 更新ガイド追記
```

### Step 5: GitHub Pages 自動デプロイ（待つだけ）

```
┌────────────────────────────────────────────────────┐
│ GitHub Pages 自動デプロイの仕組み                    │
├────────────────────────────────────────────────────┤
│                                                    │
│  git push                                          │
│      ↓                                             │
│  GitHub が検知                                      │
│      ↓                                             │
│  pages build and deployment ワークフロー実行        │
│      ↓                                             │
│  github-pages 環境にデプロイ                        │
│      ↓                                             │
│  https://dhc4mens.github.io/portfolio/ 更新完了    │
│                                                    │
│  所要時間: 約1-2分                                  │
│                                                    │
└────────────────────────────────────────────────────┘
```

**設定場所:** GitHub → Settings → Pages
- Source: Deploy from a branch
- Branch: main / (root)

### Step 6: 反映確認

```fish
# ブラウザで確認
# https://dhc4mens.github.io/portfolio/

# キャッシュが残っている場合は強制リロード
# Windows: Ctrl + Shift + R
# Mac: Cmd + Shift + R
```

**デプロイ状況の確認:**
- https://github.com/dhc4mens/portfolio/actions
- 緑チェック ✅ = 成功
- 赤バツ ❌ = 失敗（ログ確認）

---

## 🚀 クイックリファレンス（コピペ用）

### 通常の更新

```fish
cd ~/portfolio
git pull origin main
# ファイル編集（Claude経由 or 手動）
git add .
git commit -m "update: 内容"
git push origin main
# 1-2分待って https://dhc4mens.github.io/portfolio/ 確認
```

### 資格取得時の更新

```fish
cd ~/portfolio
git pull origin main
# Claudeに依頼: 「〇〇資格を取得済みに更新して」
git add index.html
git commit -m "update: 〇〇資格取得"
git push origin main
```

---

## 📝 よくある更新パターン

### 1. 資格取得時

**更新箇所:**
- 資格セクション: `planned` → `acquired` に変更
- PRセクション: AWS認定資格数を更新
- 学習セクション: 次の目標に変更

**検索キーワード:** `cert-status planned`, `pr-stat-number`

**例: MLA取得時**
```html
<!-- Before -->
<div class="skill-name">ML Engineer - Associate (MLA)<span class="cert-status planned">2026年予定</span></div>

<!-- After -->
<div class="skill-name">ML Engineer - Associate (MLA)<span class="cert-status acquired">取得済</span></div>
```

```html
<!-- PRセクションの数字更新 -->
<div class="pr-stat-number">7</div>  <!-- 6→7 -->
<div class="pr-stat-label">AWS認定資格</div>
```

---

### 2. 新規プロジェクト追加

**更新箇所:** `id="projects"` セクション内

**テンプレート:**
```html
<div class="project-card">
    <h3>プロジェクト名</h3>
    <div class="project-meta">
        <span>📅 YYYY年MM月〜</span>
        <span>👥 役割（人数）</span>
        <span>🎯 カテゴリ</span>
    </div>
    <div class="project-description">
        <strong>概要：</strong>説明文<br>
        <strong>成果：</strong>具体的な成果<br>
        <strong>役割：</strong>担当内容
    </div>
    <div class="tech-tags">
        <span class="tech-tag">技術1</span>
        <span class="tech-tag">技術2</span>
    </div>
</div>
```

**注目プロジェクトの場合:**
```html
<div class="project-card featured">
    <h3>プロジェクト名<span class="featured-badge">🔥 最新</span></h3>
    ...
</div>
```

---

### 3. スキル追加

**更新箇所:** `id="skills"` セクション内

**テンプレート:**
```html
<div class="skill-item">
    <div class="skill-name">スキル名<span class="experience-level">実務N年</span></div>
    <div class="skill-detail">詳細説明</div>
</div>
```

**新しいスキル（ハイライト）:**
```html
<span class="experience-level new">実績あり</span>
```

---

### 4. 学習目標更新

**更新箇所:** `id="learning"` セクション内

```html
<div class="learning-item">
    <h3>🤖 カテゴリ名</h3>
    <p>説明文<br>補足情報</p>
</div>
```

---

## 🎨 スタイルクラス一覧

### 資格ステータス
| クラス | 表示 | 用途 |
|--------|------|------|
| `cert-status acquired` | 緑バッジ | 取得済み |
| `cert-status planned` | オレンジバッジ | 取得予定 |

### 経験レベル
| クラス | 表示 | 用途 |
|--------|------|------|
| `experience-level` | 紫バッジ | 通常 |
| `experience-level new` | 赤バッジ | 新規・注目 |

### プロジェクトカード
| クラス | 表示 | 用途 |
|--------|------|------|
| `project-card` | 緑ボーダー | 通常 |
| `project-card featured` | 赤ボーダー | 注目案件 |

### 技術タグ
| クラス | 表示 | 用途 |
|--------|------|------|
| `tech-tag` | 紫背景 | 通常 |
| `tech-tag ai` | 赤背景 | AI関連 |

---

## 🔍 セクション構造

```
index.html
├── <aside class="sidebar">        # サイドバーナビ
├── <main class="main-content">
│   ├── <header class="header">    # ヘッダー（名前・肩書き）
│   ├── <section id="pr">          # 自己PR
│   ├── <section id="skills">      # 技術スキル
│   ├── <section id="projects">    # プロジェクト実績
│   ├── <section id="learning">    # 学習・今後
│   └── <section id="certifications"> # 資格・認定
└── <script>                       # ナビゲーションJS
```

---

## 📌 Claudeに依頼する場合

### 依頼例

```
ポートフォリオを更新したい。
以下の変更を index.html に反映してほしい:

1. MLA資格を「取得済」に変更
2. AWS認定資格数を7に更新
3. 新しいプロジェクト「〇〇」を追加
```

### MCP経由での編集

Claudeはポートフォリオのファイルに直接アクセス可能:
- 読み取り: `portfolio:read_text_file`
- 書き込み: `portfolio:write_file`
- 部分編集: `portfolio:edit_file`

**注意:** Claudeはファイル編集のみ可能。Git操作（commit/push）は手動で実行が必要。

---

## ⚠️ 注意事項

1. **Git pull忘れ**: 編集前に必ず `git pull` で最新化
2. **キャッシュ**: 反映確認時は Ctrl+Shift+R で強制リロード
3. **デプロイ待ち**: push後1-2分は待つ（すぐ確認しても古い）
4. **モバイル確認**: スマホでも表示確認を推奨
5. **文字化け**: 日本語はUTF-8で保存

---

## 🔧 トラブルシューティング

### デプロイが反映されない

```fish
# 1. Actions の状態確認
# https://github.com/dhc4mens/portfolio/actions

# 2. 失敗している場合はログ確認

# 3. 成功しているのに反映されない場合
# → ブラウザキャッシュをクリア（Ctrl+Shift+R）
# → シークレットモードで確認
```

### push が reject された

```fish
# リモートに新しい変更がある場合
git pull --rebase origin main
git push origin main
```

### 編集を取り消したい

```fish
# コミット前
git checkout -- index.html

# コミット後（push前）
git reset --soft HEAD~1

# push後（履歴に残る）
git revert HEAD
git push origin main
```

---

## 📅 更新履歴

| 日付 | 内容 |
|------|------|
| 2025/12/21 | DEA取得反映、更新ガイド作成（Git/デプロイフロー追記） |
| 2025/12 | サイドバーナビ追加、モバイル対応 |
| 2025/12 | 初版作成、スキルシートベースで刷新 |

---

## 🔗 関連リンク

- [公開ページ](https://dhc4mens.github.io/portfolio/)
- [リポジトリ](https://github.com/dhc4mens/portfolio)
- [GitHub Pages設定](https://github.com/dhc4mens/portfolio/settings/pages)
- [Actions（デプロイ状況）](https://github.com/dhc4mens/portfolio/actions)
- [Credly バッジ](https://www.credly.com/users/daisuke-hatada.akiko/badges)
