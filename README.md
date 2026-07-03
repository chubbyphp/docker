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
mkdir -p ~/.claude
[ ! -f ~/.claude.json ] && echo '{}' > ~/.claude.json
[ ! -f ~/.claude/.credentials.json ] && echo '{}' > ~/.claude/.credentials.json
[ ! -f ~/.claude/settings.json ] && echo '{}' > ~/.claude/settings.json
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
