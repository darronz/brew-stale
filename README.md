# brew-stale

Find Homebrew packages you never use.

Cross-references `brew leaves` with your zsh history to show when each package was last used, how many times, and which ones are gathering dust.

## Install

```bash
brew tap darronz/tap
brew install brew-stale
```

Or run directly:

```bash
curl -O https://raw.githubusercontent.com/darronz/brew-stale/main/brew-stale
chmod +x brew-stale
./brew-stale
```

## Usage

```bash
brew-stale                # show all packages, sorted by last used
brew-stale --stale 30     # only packages not used in the last 30 days
brew-stale --csv          # CSV output for further processing
brew-stale --history ~/alt_history  # use a different history file
```

## Output

Packages are colour-coded by staleness:

- **Green** — used in the last 30 days
- **Yellow** — used 30–90 days ago
- **Red** — not used in 90+ days, or never

The tool also resolves binary aliases (e.g. `ripgrep` → `rg`) so usage is detected even when the package name doesn't match the command you type.

## Requirements

- macOS with [Homebrew](https://brew.sh)
- zsh (uses zsh history format)
- Python 3 (for parsing `brew info` JSON)

## License

MIT
