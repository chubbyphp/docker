# docker

## setup on host

### bash

```sh
touch ~/.bash_docker
touch ~/.bash_history
```

### git

```sh
touch ~/.gitconfig
touch ~/.gitignore
```

### opencode

```sh
mkdir -p ~/.config/opencode
[ ! -f ~/.local/share/opencode/auth.json ] && echo '{}' > ~/.config/opencode/tui.json
mkdir -p ~/.local/share/opencode
[ ! -f ~/.local/share/opencode/auth.json ] && echo '{}' > ~/.local/share/opencode/auth.json
```

### ssh

```sh
mkdir -p ~/.ssh
touch ~/.ssh/github.pub
```

### zsh

```sh
touch ~/.zsh_docker
touch ~/.zsh_history
```

## Copyright

2026 Dominik Zogg
