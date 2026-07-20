# docker

## setup on host

### bash

```sh
touch ~/.bash_docker
touch ~/.bash_history
```

### zsh

```sh
touch ~/.zsh_docker
touch ~/.zsh_history
```

### git

```sh
touch ~/.gitconfig
touch ~/.gitignore
```

### ssh

```sh
mkdir -p ~/.ssh
touch github.pub
```

### claude - coding agent

```sh
[ ! -f ~/.claude.json ] && echo '{}' > ~/.claude.json
mkdir -p ~/.claude
[ ! -f ~/.claude/.credentials.json ] && echo '{}' > ~/.claude/.credentials.json
[ ! -f ~/.claude/settings.json ] && echo '{\n  "fileCheckpointingEnabled": false,\n  "permissions": {\n    "defaultMode": "bypassPermissions"\n  },\n  "skipDangerousModePermissionPrompt": true,\n  "spinnerTipsEnabled": false,\n  "switchModelsOnFlag": false,\n  "theme": "auto"\n}' > ~/.claude/settings.json
chmod 600 ~/.claude/.credentials.json
chmod 600 ~/.claude/settings.json
```

### codex - coding agent

```sh
mkdir -p ~/.codex
[ ! -f ~/.codex/auth.json ] && echo '{}' > ~/.codex/auth.json
[ ! -f ~/.codex/config.toml ] && echo 'approval_policy = "never"\nsandbox_mode = "danger-full-access"\napprovals_reviewer = "user"\n\n[projects."/app"]\ntrust_level = "trusted"\n\n[notice]\nhide_full_access_warning = true' > ~/.codex/config.toml
chmod 600 ~/.codex/auth.json
chmod 600 ~/.codex/config.toml
```

### opencode - coding agent

```sh
mkdir -p ~/.config/opencode
[ ! -f ~/.config/opencode/tui.json ] && echo '{}' > ~/.config/opencode/tui.json
mkdir -p ~/.local/share/opencode
[ ! -f ~/.local/share/opencode/auth.json ] && echo '{}' > ~/.local/share/opencode/auth.json
```

### pi - coding agent

```sh
mkdir -p ~/.pi/agent
[ ! -f ~/.pi/agent/auth.json ] && echo '{}' > ~/.pi/agent/auth.json
```

## Copyright

2026 Dominik Zogg
