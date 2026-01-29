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

## Usage

```bash
# Basic lookup
gpedia stoicism

# Multi-word topics
gpedia "Albert Einstein"
gpedia quantum mechanics

# Pipe through pager
gpedia "roman empire" | less

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
| `--json` | Output raw JSON instead of formatted text |
| `--refs` | Include references section |
| `--short` | Truncate to ~500 words |
| `--truncate N` | Truncate to N characters |

## Output

Colors are enabled when outputting to a terminal, disabled when piping. Set `NO_COLOR=1` to force plain text.

## API

Uses the unofficial [Grokipedia API](https://grokipedia-api.vercel.app) (not affiliated with xAI).

## License

MIT
