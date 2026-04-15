# Claude Code Multi Account Setup

Run two Claude Code accounts simultaneously on macOS without re-authenticating by using separate configuration directories.

## 1. Create Separate Config Directories

```bash
mkdir ~/.claude-a1
mkdir ~/.claude-a2
```

## 2. Add Aliases to Your Shell Config

Open `~/.zshrc` (or `~/.bashrc` for Bash):

```bash
nano ~/.zshrc
```

Add the following aliases:

```bash
alias claude-a1="CLAUDE_CONFIG_DIR=~/.claude-a1 claude"
alias claude-a2="CLAUDE_CONFIG_DIR=~/.claude-a2 claude"
```

Save the file, then reload your shell:

```bash
source ~/.zshrc
```

## 3. Authenticate Each Account

**Account 1** — run the alias and log in when prompted:

```bash
claude-a1
```

Credentials are saved to `~/.claude-a1`.

**Account 2** — repeat for the second account:

```bash
claude-a2
```

Credentials are saved to `~/.claude-a2`.

## 4. Switch or Run Simultaneously

Open separate terminal tabs with **Cmd + T** and run each alias independently. Each instance uses its own configuration directory and usage limits.
