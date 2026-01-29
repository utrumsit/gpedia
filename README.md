# gpedia

CLI for looking up topics on [Grokipedia](https://grokipedia.com) (xAI's AI-generated encyclopedia).

## Installation

```bash
# Clone and link
git clone https://github.com/utrumsit/gpedia.git
cd gpedia
ln -s $(pwd)/gpedia ~/.local/bin/gpedia

# Or just copy it
cp gpedia /usr/local/bin/
```

No dependencies beyond Python 3.6+.

### Optional: Install glow for beautiful markdown rendering

```bash
brew install glow
```

[glow](https://github.com/charmbracelet/glow) renders markdown beautifully in the terminal with proper formatting, italics, headers, and a built-in pager.

## Usage

```bash
# Basic lookup
gpedia stoicism

# Beautiful markdown rendering with glow (recommended)
gpedia stoicism --glow
gpedia "Marcus Aurelius" --glow

# Raw markdown output (pipe to any markdown renderer)
gpedia stoicism --markdown
gpedia stoicism -m | glow -p

# Multi-word topics
gpedia "Albert Einstein"
gpedia quantum mechanics

# Short output (~500 words)
gpedia philosophy --short

# Include references
gpedia "Marcus Aurelius" --refs

# Raw JSON output (for scripting)
gpedia stoicism --json
gpedia "ancient rome" --json | jq .word_count

# Truncate to specific character count
gpedia "world war 2" --truncate 5000
```

## Options

| Flag | Description |
|------|-------------|
| `--glow`, `-g` | Render with glow pager (requires `brew install glow`) |
| `--markdown`, `-m` | Output raw markdown |
| `--json` | Output raw JSON |
| `--refs` | Include references section |
| `--short` | Truncate to ~500 words |
| `--truncate N` | Truncate to N characters |
| `--api` | API to use: `original` or `fork` (default: fork) |

## Output Modes

- **Default**: Formatted terminal output with ANSI colors
- **`--glow`**: Beautiful markdown rendering with built-in pager (page up/down, q to quit)
- **`--markdown`**: Raw markdown for piping to other tools
- **`--json`**: Full API response for scripting

## API

Uses a [fork of the Grokipedia API](https://github.com/utrumsit/grokipedia-api) with markdown support. The fork adds proper inline formatting (*italics* for terms like *eudaimonia*) and markdown headers.

Original API by [jasonniebauer](https://github.com/jasonniebauer/grokipedia-api).

## License

MIT
