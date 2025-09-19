
# Oh My Posh — Quick install & setup (WSL / Linux)

This file shows simple, easy-to-follow steps to install and configure Oh My Posh in a WSL or Linux shell (bash / zsh). Adapt paths and shell names to your environment.

If you want to find more info about Oh My Posh, please visit the official website: https://ohmyposh.dev

## 1) Install

Run the official install script (make sure that you have already installed curl)(recommended):

	curl -s https://ohmyposh.dev/install.sh | bash -s

The installer places the `oh-my-posh` binary (usually) under `$HOME/.local/bin`.

## 2) Add to PATH

If `$HOME/.local/bin` is not already in your `PATH`, add it to your shell profile so the `oh-my-posh` command is available in new shells.

For bash (`~/.bashrc`) or zsh (`~/.zshrc`) add:
```bash
export PATH="$PATH:$HOME/.local/bin"
```
Reload the profile or start a new shell after editing:
```bash
source ~/.bashrc   # or: source ~/.zshrc
```
## 3) Enable Oh My Posh in your shell

Add the initialization line to the end of your shell profile (same file you edited above):

```bash
	eval "$(oh-my-posh init bash)"
```
If you use `zsh` replace `bash` with `zsh`:
```bash
	eval "$(oh-my-posh init zsh)"
```
## 4) Choose a theme

Oh My Posh includes many themes. The installer typically caches themes under `~/.cache/oh-my-posh/themes/`.

To use a specific theme (example):
```bash

	eval "$(oh-my-posh init bash --config ~/.cache/oh-my-posh/themes/jandedobbeleer.omp.json)"
```
Replace the filename with whichever theme you prefer.

### Rotate themes randomly (optional)

If you'd like to pick a random theme on each shell start, add something like this to your profile:

```bash
# List themes (base names only)
themes=("di4am0nd" "slim" "slimfat")

# Pick one at random and export
POSH_THEME="${themes[$((RANDOM % ${#themes[@]}))]}"
export POSH_THEME

# Initialize Oh My Posh with the selected theme
eval "$(oh-my-posh init bash --config ~/.cache/oh-my-posh/themes/$POSH_THEME.omp.json)"
```

```bash
# List themes (base names only)
themes=("di4am0nd" "slim" "slimfat")

# Pick one at random and export
POSH_THEME="${themes[$((RANDOM % ${#themes[@]}))]}"
export POSH_THEME

# Initialize Oh My Posh with the selected theme
eval "$(oh-my-posh init bash --config ~/.cache/oh-my-posh/themes/$POSH_THEME.omp.json)"
```

Adjust the `themes` array to include theme filenames available on your system.

## Troubleshooting

- If `oh-my-posh` is not found, confirm the binary exists and your `PATH` includes the install location (`$HOME/.local/bin`).
- If a theme file isn't found, list `~/.cache/oh-my-posh/themes/` and confirm the exact filename or path.
- On Windows (PowerShell) use the PowerShell-specific init: `oh-my-posh init pwsh --config <path>` and add the output to your PowerShell profile, here the official documentation for PowerShell https://ohmyposh.dev/docs/installation/windows.

## Notes

- This README shows minimal, per-user setup. For system-wide or alternative installs, see the official docs: https://ohmyposh.dev
- Keep your theme files cached locally for offline usage.

---