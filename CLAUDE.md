# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with this repository.

## Project overview

English Refiner is a bash TUI tool that refines English text using LLM via OpenRouter API. It uses gum for the terminal UI and curl for API calls.

## Architecture

Single bash script (`englishrefiner`) with three modes:
- TUI mode (default) - interactive text editor via gum
- Clipboard mode (`-c`) - reads from pbpaste, writes to pbcopy
- Pipe mode - reads from stdin

API key stored at `~/.config/englishrefiner/key`.

## Common commands

```bash
# Install
sudo cp englishrefiner /usr/local/bin/englishrefiner
sudo chmod +x /usr/local/bin/englishrefiner

# Run
englishrefiner
```

## Key guidelines

- Model is configured via the MODEL variable at the top of the script
- System prompt is tuned for CTO-to-customer communication style
- Output must use straight quotes, regular dashes, and three dots (not unicode variants)
- Never commit API keys or sensitive data

## Commits and code style

- One logical change per commit
- Keep commit messages concise (one line), use sentence case
- Use present tense in commits and CHANGELOG.md
- Use sentence case for headings
- Use * as bullets in CHANGELOG.md
- No emojis in commits or code
- Keep CHANGELOG.md date up to date when adding entries
