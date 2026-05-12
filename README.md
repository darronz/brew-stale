# brew-stale

Find Homebrew packages you never use.

Cross-references `brew leaves` and installed casks with your shell history (bash or zsh) to show when each package was last used, how many times, how much space it takes, and which ones are gathering dust.

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

Each row shows: package name, type (formula/cask), install date, last-used date, days since last use, usage count, and disk size.

Packages are colour-coded by staleness:

- **Green** — used in the last 30 days, or an active brew service
- **Yellow** — used 30–90 days ago
- **Red** — not used in 90+ days, or never

### Smart detection

- **Binary aliases** — resolves alternative command names (e.g. `ripgrep` → `rg`) so usage is detected even when the package name doesn't match the command you type
- **Cask apps** — uses macOS Spotlight metadata (`kMDItemLastUsedDate`) to detect when GUI apps were last opened, even if launched via Finder or Spotlight rather than the terminal
- **Brew services** — detects packages running as background services (e.g. `watchman`, `postgresql`, `dnsmasq`) and marks them with `● service` so they aren't mistaken for unused packages

## Requirements

- macOS with [Homebrew](https://brew.sh)
- bash 4+ or zsh (macOS ships bash 3.2 — run `brew install bash` for a modern version)
- Python 3 (for parsing `brew info` JSON)

## License

MIT
