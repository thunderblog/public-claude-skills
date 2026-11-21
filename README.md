# public-claude-skills

![version](https://img.shields.io/badge/version-3.0.0-blue) ![license](https://img.shields.io/badge/license-MIT-green)

Claude Code で使えるカスタムスキルのコレクションです。

## スキル一覧

### [`/token-saver`](skills/token-saver/SKILL.md) — トークン消費最適化

Claude Code のコスト増加の根本原因は「コンテキストの肥大化」。5つのモードで構造的に対処します。

| モード | コマンド | 内容 |
|--------|---------|------|
| チェックリスト | `/token-saver` | `/context`・`/clear`・`/compact` など組み込みコマンドを含む5つのコスト削減策を表示し、選択・実行まで案内 |
| セッション引き継ぎ | `/token-saver handoff` | 現在の会話を要約し、`tasks/handoff-YYYY-MM-DD.md` に保存 |
| 引き継ぎ読み込み | `/token-saver load` | 保存済みの引き継ぎファイルを自動検出して読み込み、前回のコンテキストを復元（読込後は `tasks/archive/` へ移動可） |
| CLAUDE.md 監査 | `/token-saver audit` | CLAUDE.md・CLAUDE.local.md・`@import` 先・MEMORY.md などを診断して削減提案（不在時は `/init` 等で新規作成支援） |
| モデル選択 | `/token-saver model` | タスク別の最適モデル（Haiku / Sonnet / Opus / Fable）を表示し、今のタスクに合ったモデルを提案 |

**構成：** `SKILL.md` はモード判定のみ。各モードの手順は `references/*.md` に分割し、使うモードの分だけ読み込むためスキル自体の消費トークンを抑えています。

```
skills/token-saver/
├── SKILL.md
└── references/
    ├── handoff.md
    ├── load.md
    ├── audit.md
    ├── check.md
    └── model.md
```

**トリガーワード：** 「コストを節約したい」「トークン消費が気になる」「セッションをリセットしたい」「引き継ぎ」「前回の続き」「CLAUDE.md を見直したい」「モデルを選びたい」

---

## インストール方法

### Mac / Linux

```bash
git clone https://github.com/thunderblog/public-claude-skills.git
mkdir -p ~/.claude/skills
cp -r public-claude-skills/skills/* ~/.claude/skills/
```

### Windows（PowerShell）

```powershell
git clone https://github.com/thunderblog/public-claude-skills.git
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills"
Copy-Item -Recurse public-claude-skills\skills\* "$env:USERPROFILE\.claude\skills\"
```

### Windows（WSL）

```bash
git clone https://github.com/thunderblog/public-claude-skills.git
mkdir -p ~/.claude/skills
cp -r public-claude-skills/skills/* ~/.claude/skills/
```

### claude.ai（Web）

1. [claude.ai/code](https://claude.ai/code) を開く
2. 左サイドバーの **Settings** → **Skills** を開く
3. 各スキルの `SKILL.md` の内容をコピーして貼り付けて保存

---

## スキルディレクトリの場所

| 環境 | パス |
|------|------|
| Mac / Linux | `~/.claude/skills/` |
| Windows（ネイティブ） | `%USERPROFILE%\.claude\skills\` |
| Windows（WSL） | `~/.claude/skills/` |

---

## CHANGELOG

### v3.0.0 — 2026-11-21

- `SKILL.md` をモード判定のみに縮小し、各モードを `references/*.md` に分割（約400行 → 約30行＋必要分のみ読込）
- 確認ステップを最大2回（選択 → 最終OK）に削減
- `check` に `/context`・`/cost`・`/clear`・`/compact` を追加、`handoff` 保存後に `/clear` → `load` の流れを案内
- `audit` の対象に `.claude/CLAUDE.md`・`CLAUDE.local.md`・`@import` 先・サブディレクトリ CLAUDE.md・MEMORY.md を追加、トークン見積もりルールを明記
- CLAUDE.md 新規作成は WebSearch を廃止し `/init` を第一推奨に
- `load` 後の `rm` 削除を廃止し、`tasks/archive/` への移動に変更
- `model` に Fable（最上位・長時間エージェント作業向け）を追加

### v2.1.1 — 2026-11-21

- リポジトリの `SKILL.md` に v2.1.0 の変更（`load` モード・`handoff` のファイル保存）を反映（未反映だった）
- `model` モードからバージョン番号・モデルIDのハードコードを削除し、`/model` と公式ドキュメント参照に変更
- `audit` 新規作成テンプレートのコードブロック入れ子による表示崩れを修正
- モード数の記述（3→5）とモード記号（A〜E）を整理

### v2.1.0 — 2026-04-18

- `load` モード追加：保存済み引き継ぎファイルを自動検出して読み込む
- `handoff` にファイル保存フロー追加（確認・上書き防止・カスタムパス対応）

### v2.0.0 — 2026-04-05

- スキルの選択肢を見直し、よく使う項目に絞り機能をブラッシュアップ

### v1.0.0 — 2026-04-04

- 初版公開

---

## ライセンス

[MIT License](LICENSE)
