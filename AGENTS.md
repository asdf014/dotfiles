# Repository Guidelines

## Project Structure & Module Organization
This repo tracks the author’s shell and editor dotfiles expected to live in `~/git/dotfiles`. Key assets include `.zshrc` (Oh My Zsh setup and plugin list), `.vimrc` (Vim behavior and UI tweaks), `env.sh` (shared environment variables and helper aliases), `alias.sh` (standalone shortcuts), and `README.md` (bootstrap notes). Keep machine-specific secrets out of version control and prefer sourcing a private override file from `.zshrc` if needed.

## Build, Test, and Development Commands
No formal build exists; focus on fast bootstrap and reload loops. After cloning, refresh links with:
```bash
ln -s ~/git/dotfiles/.zshrc ~/.zshrc
ln -s ~/git/dotfiles/.vimrc ~/.vimrc
```
Reload changes without restarting the terminal via `zsh -i -c "source ~/.zshrc"`. Ensure plugin dependencies are present with `brew install fnm fzf rust`, and load added aliases quickly with `source ~/git/dotfiles/alias.sh`.

## Coding Style & Naming Conventions
Shell scripts are written for `zsh`; keep the `#!/bin/zsh` shebang and use two-space indentation for any blocks. Name aliases in lowercase without separators (`updatelog`, `gl`), reserve uppercase snake-case for exported variables, and favor explicit `$HOME/git/dotfiles` paths for clarity. In Vim configs, follow the existing comment style (`"` prefix) and group related options under the documented sections before adding new clusters.

## Testing Guidelines
Automated tests are not configured, so rely on quick manual checks. Run `shellcheck alias.sh env.sh` before committing to catch syntax issues (install with Homebrew if missing). Validate aliases in a clean shell using `zsh -i -c "alias buc"` and confirm Vim loads without warnings via `vim -Nu ~/git/dotfiles/.vimrc +'quit'`. Update `README.md` when new dependencies or plugins are introduced.

## Commit & Pull Request Guidelines
Aim for focused commits covering a single configuration theme. Use short, imperative subjects (e.g., `Add docker aliases`), optionally followed by a brief body describing context or manual verification. Group related file updates together and mention if users must re-run the symlink or install commands. For pull requests, include: goal of the change, validation steps executed, dependency or plugin notes, and screenshots or terminal snippets when altering prompts or themes.
