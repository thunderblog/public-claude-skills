# public-claude-skills

Claude Code で使えるカスタムスキルのコレクションです。

## スキル一覧

### [`/token-saver`](skills/token-saver/SKILL.md) — トークン消費最適化

Claude Code のコスト増加の根本原因は「コンテキストの肥大化」。4つのモードで構造的に対処します。

| モード | コマンド | 内容 |
|--------|---------|------|
| チェックリスト | `/token-saver` | すぐ実行できる3つのコスト削減策を表示し、選択・実行まで案内 |
| セッション引き継ぎ | `/token-saver handoff` | 現在の会話を要約し、次セッションにそのまま貼れる引き継ぎドキュメントを生成 |
| CLAUDE.md 監査 | `/token-saver audit` | グローバル・プロジェクトの CLAUDE.md を読み込み、肥大化箇所を診断して削減提案 |
| モデル選択 | `/token-saver model` | タスク別の最適モデル（Haiku / Sonnet / Opus）を表示し、今のタスクに合ったモデルを提案 |

**トリガーワード：** 「コストを節約したい」「トークン消費が気になる」「セッションをリセットしたい」「CLAUDE.md を見直したい」「モデルを選びたい」

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

## ライセンス

[MIT License](LICENSE)
