# public-claude-skills

Claude Code で使えるカスタムスキルのコレクションです。

## スキル一覧

### [`/token-saver`](skills/token-saver/SKILL.md)

ClaudeCode のトークン消費量を抑えるスキル。

| モード | コマンド | 内容 |
|--------|---------|------|
| チェックリスト | `/token-saver` | コスト削減6つの対策を表示 |
| セッション引き継ぎ | `/token-saver handoff` | 次セッション用の引き継ぎサマリーを生成 |
| CLAUDE.md監査 | `/token-saver audit` | CLAUDE.md の肥大化を診断・削減提案 |

**トリガーワード：** 「コストを節約したい」「トークンが多い」「セッションをリセットしたい」「CLAUDE.mdを見直したい」

---

## インストール方法

### Mac

#### Claude Code（ターミナル / デスクトップアプリ）

```bash
# リポジトリをクローン
git clone https://github.com/thunderblog/public-claude-skills.git

# スキルディレクトリを作成してコピー
mkdir -p ~/.claude/skills
cp -r public-claude-skills/skills/* ~/.claude/skills/
```

#### claude.ai（Web）

1. [claude.ai/code](https://claude.ai/code) を開く
2. 左サイドバーの **Settings（設定）** → **Skills** を開く
3. 各スキルの `SKILL.md` の内容をコピーして貼り付けて保存

---

### Windows

#### Claude Code（ターミナル / デスクトップアプリ）

**PowerShell で実行：**

```powershell
# リポジトリをクローン
git clone https://github.com/thunderblog/public-claude-skills.git

# スキルディレクトリを作成してコピー
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills"
Copy-Item -Recurse public-claude-skills\skills\* "$env:USERPROFILE\.claude\skills\"
```

**WSL（Windows Subsystem for Linux）を使っている場合：**

```bash
# リポジトリをクローン
git clone https://github.com/thunderblog/public-claude-skills.git

# スキルディレクトリを作成してコピー
mkdir -p ~/.claude/skills
cp -r public-claude-skills/skills/* ~/.claude/skills/
```

#### claude.ai（Web）

1. [claude.ai/code](https://claude.ai/code) を開く
2. 左サイドバーの **Settings（設定）** → **Skills** を開く
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
