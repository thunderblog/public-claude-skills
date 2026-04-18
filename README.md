# public-claude-skills

![version](https://img.shields.io/badge/version-2.1.0-blue) ![license](https://img.shields.io/badge/license-MIT-green)

Claude Code で使えるカスタムスキルのコレクションです。

## スキル一覧

### [`/token-saver`](skills/token-saver/SKILL.md) — トークン消費最適化

Claude Code のコスト増加の根本原因は「コンテキストの肥大化」。5つのモードで構造的に対処します。

| モード | コマンド | 内容 |
|--------|---------|------|
| チェックリスト | `/token-saver` | すぐ実行できる3つのコスト削減策を表示し、選択・実行まで案内 |
| セッション引き継ぎ | `/token-saver handoff` | 現在の会話を要約し、`tasks/handoff-YYYY-MM-DD.md` に保存 |
| 引き継ぎ読み込み | `/token-saver load` | 保存済みの引き継ぎファイルを自動検出して読み込み、前回のコンテキストを復元 |
| CLAUDE.md 監査 | `/token-saver audit` | グローバル・プロジェクトの CLAUDE.md を読み込み、肥大化箇所を診断して削減提案 |
| モデル選択 | `/token-saver model` | タスク別の最適モデル（Haiku / Sonnet / Opus）を表示し、今のタスクに合ったモデルを提案 |

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
