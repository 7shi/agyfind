# agyfind

Search and inspect files under the brain directory of the Antigravity CLI (`~/.gemini/antigravity-cli`).

The brain directory contains one UUID-named directory per conversation. Each `*.md` file directly under such a directory has a `<filename>.metadata.json` sidecar (summary, updatedAt, etc). This tool lists and displays those files.

## Requirements

- Python 3.10 or higher
- An existing `~/.gemini/antigravity-cli` directory (created by the Antigravity CLI)

## Installation

### As a tool (recommended)

```bash
# Install as a tool
uv tool install https://github.com/7shi/agyfind.git

# Add ~/.local/bin to PATH if not already added
export PATH="$HOME/.local/bin:$PATH"
```

### From source

```bash
# Source installation with uv
git clone https://github.com/7shi/agyfind.git
cd agyfind
uv sync
```

**Note**: When using source installation, prefix all commands with `uv run` (e.g., `uv run agyfind summary`).

## Usage

```bash
# List entries as "N. YYYY/MM/DD HH:mm:SS [workspace] summary"
agyfind summary

# Filter by working directory (also matches subdirectories)
agyfind summary ~/repos/opencode

# List md file paths under brain
agyfind ls [DIRECTORY]

# Show details of summary entry N (content limited to LINES lines, default 10)
agyfind show N [-n LINES]
```

If `DIRECTORY` is given, only conversations belonging to that working directory (the `~/...` part of a summary line) are shown. In that case the workspace is omitted from summary lines, since it would be identical on every line.

Entries are always sorted by `updatedAt` (converted to JST) in descending order. The index number shown by `agyfind summary` corresponds to this order, so it can be passed directly to `agyfind show N`.

## Sources of information

- `brain/<UUID>/<file>.md.metadata.json` — summary, updatedAt (falls back to file mtime if absent)
- `conversation_summaries.db` — mapping from conversation ID to working directory (official source)
- `history.jsonl` — same mapping from input history, used to fill gaps when the DB has not yet caught up with the latest conversation
