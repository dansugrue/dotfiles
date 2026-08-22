# dotfiles

Personal config files for bash, zsh, vim, tmux, and Alacritty — kept in sync across machines via symlinks.

## What's included

| File | Links to | Purpose |
|---|---|---|
| `home/bashrc` | `~/.bashrc` | Bash config (Linux/servers) |
| `home/zshrc` | `~/.zshrc` | Zsh config (macOS) |
| `home/vimrc` | `~/.vimrc` | Vim settings |
| `home/tmux.conf` | `~/.tmux.conf` | tmux config (window indexing, keybindings) |
| `config/alacritty/alacritty.toml` | `~/.config/alacritty/alacritty.toml` | Alacritty terminal config |

## Install

Clone into your home directory, then run the setup script:

```bash
git clone https://github.com/dansugrue/dotfiles.git ~/dotfiles
cd ~/dotfiles
./setup
```

This will:
- Install GNU coreutils via Homebrew (macOS only, for consistent `ls` colors across Linux/macOS)
- Symlink all config files into place

## Requirements

- **macOS**: [Homebrew](https://brew.sh) (script installs `coreutils` automatically)
- **Linux**: none — uses native GNU coreutils already present

## Notes

- Prompt colors and hostname are set per-machine via `HostName`/`ComputerName` (macOS) — see `zshrc` for prompt color scheme. Though branch uses the same colour scheme across all devices.
- `ls` colors are matched across macOS and Linux using GNU coreutils (`gls` aliased to `ls` on macOS).
- Safe to re-run `./setup` any time — symlinks are overwritten (`ln -sf`), not duplicated.

## Git identity

Git user/email isn't included here (kept out of version control intentionally). Set per-machine:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```
