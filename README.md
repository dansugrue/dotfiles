les
Personal config files for bash, zsh, vim, tmux, and Alacritty — kept in sync across machines via symlinks.

## What's included

| File | Links to | Machine |
|---|---|---|
| `home/zshrc_cato` | `~/.zshrc` | cato |
| `home/zshrc_maclab` | `~/.zshrc` | maclab |
| `home/bashrc_homelab` | `~/.bashrc` | homelab |
| `home/bashrc_default` | `~/.bashrc` | any other/foreign machine |
| `home/vimrc` | `~/.vimrc` | all |
| `home/tmux.conf` | `~/.tmux.conf` | all |
| `config/alacritty/alacritty.toml` | `~/.config/alacritty/alacritty.toml` | cato only |

## Install

Clone into your home directory, then run the setup script:

```bash
git clone https://github.com/dansugrue/dotfiles.git ~/dotfiles
cd ~/dotfiles
./setup
```

This will:
- On macOS, install Homebrew (if missing) and GNU coreutils
- Symlink the shell config for the current hostname — `zshrc_cato`, `zshrc_maclab`, `bashrc_homelab`, or `bashrc_default` for anything else
- Symlink `vimrc` and `tmux.conf`

**Alacritty is handled separately.** It's only relevant on the machine you actually look at a screen on (cato) — SSH'd-into boxes never render a local terminal font, so it doesn't belong in the multi-device flow. Run it once, by hand, only on cato:

```bash
./setup-alacritty
```

This installs the JetBrainsMono Nerd Font (needed for the git-branch glyph in the prompt) and symlinks `alacritty.toml`.

## Requirements
- **macOS**: [Homebrew](https://brew.sh) — installed automatically by `./setup` if missing
- **Linux**: none — uses native GNU coreutils already present

## Notes
- Hostname-based branching lives in `./setup` — see the `case` statement for which file maps to which machine.
- Branch color in the prompt is the same across every shell config; only the user/host/path colors vary per machine.
- Foreign machines always get `bashrc_default`, regardless of shell. Foreign zsh isn't supported — a zsh login shell won't source `.bashrc` automatically, so if you ever land on a foreign box running zsh, the prompt customization won't apply. This was an intentional tradeoff, not an oversight.
- Safe to re-run `./setup` or `./setup-alacritty` any time — symlinks are overwritten (`ln -sf`), not duplicated.

## Git identity
Git user/email isn't included here (kept out of version control intentionally). Set per-machine:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```
