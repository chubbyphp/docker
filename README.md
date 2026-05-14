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

### opencode - coding agent

```sh
mkdir -p ~/.config/opencode
[ ! -f ~/.local/share/opencode/auth.json ] && echo '{}' > ~/.config/opencode/tui.json
mkdir -p ~/.local/share/opencode
[ ! -f ~/.local/share/opencode/auth.json ] && echo '{}' > ~/.local/share/opencode/auth.json
```

## Copyright

2026 Dominik Zogg
