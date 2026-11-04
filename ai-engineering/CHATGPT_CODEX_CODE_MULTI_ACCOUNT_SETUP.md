# ChatGPT Codex Multi Account Setup

Run two ChatGPT Codex accounts simultaneously on macOS without re-authenticating by using separate configuration directories.

## 1. Create Separate Config Directories

```bash
mkdir ~/.codex-a1
mkdir ~/.codex-a2
```

## 2. Add Aliases to Your Shell Config

Open `~/.zshrc` (or `~/.bashrc` for Bash):

```bash
nano ~/.zshrc
```

Add the following aliases:

```bash
alias codex-a1="CODEX_HOME=~/.codex-a1 codex"
alias codex-a2="CODEX_HOME=~/.codex-a2 codex"
```

Save the file, then reload your shell:

```bash
source ~/.zshrc
```

## 3. Authenticate Each Account

**Account 1** - run the alias and log in when prompted:

```bash
codex-a1
```

Credentials are saved to `~/.codex-a1`.

**Account 2** - repeat for the second account:

```bash
codex-a2
```

Credentials are saved to `~/.codex-a2`.

## 4. Switch or Run Simultaneously

Open separate terminal tabs with **Cmd + T** and run each alias independently. Each instance uses its own configuration directory and usage limits.
