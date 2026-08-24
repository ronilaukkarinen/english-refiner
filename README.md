# English Refiner CLI

**A fast TUI tool for refining English text via OpenRouter or the Anthropic API. Fixes grammar and wording while keeping the message intact.**

<img width="836" height="368" alt="image" src="https://github.com/user-attachments/assets/ddbff1ef-c3fc-418b-8b54-086ed666c5e6" />

## Dependencies

- [gum](https://github.com/charmbracelet/gum) - TUI components
- [jq](https://jqlang.github.io/jq/) - JSON parsing
- curl
- [Anthropic](https://console.anthropic.com/) API key

## Installation on macOS

```bash
brew install gum jq

mkdir -p ~/.config/englishrefiner
echo -n 'your-anthropic-api-key-here' > ~/.config/englishrefiner/key
chmod 600 ~/.config/englishrefiner/key

sudo cp englishrefiner /usr/local/bin/englishrefiner
sudo chmod +x /usr/local/bin/englishrefiner
```

## Installation on Linux

Install dependencies for your distro. For Wayland, install `wl-clipboard`. For X11, install `xclip` instead.

```bash
# Arch
sudo pacman -S gum jq wl-clipboard

# Debian/Ubuntu
sudo apt install gum jq wl-clipboard
```

```bash
mkdir -p ~/.config/englishrefiner
echo -n 'your-anthropic-api-key-here' > ~/.config/englishrefiner/key
chmod 600 ~/.config/englishrefiner/key

sudo cp englishrefiner-linux /usr/local/bin/englishrefiner
sudo chmod +x /usr/local/bin/englishrefiner
```

## Usage

```bash
# TUI mode - opens editor, type/paste text, Ctrl+D to submit
englishrefiner

# Clipboard mode - refines clipboard contents, copies result back
englishrefiner -c

# Pipe mode
echo 'your text' | englishrefiner
```

Result is always auto-copied to clipboard.

## Quick AI

A second tool, `quickai`, uses the same TUI but for quick one-off questions instead of refining text. It uses Claude Haiku 4.5 (`claude-haiku-4-5-20251001`) for fast, cheap answers and its own Anthropic API key.

An alias `quai` is also available for convenience.

```bash
mkdir -p ~/.config/quickai
echo -n 'your-anthropic-api-key-here' > ~/.config/quickai/key
chmod 600 ~/.config/quickai/key

sudo cp quickai /usr/local/bin/quickai
sudo chmod +x /usr/local/bin/quickai
```

```bash
# TUI mode - opens editor, type your question, Ctrl+D to submit
quickai

# Clipboard mode - asks about clipboard contents
quickai -c

# Pipe mode
echo 'your question' | quickai
```

## Model

The provider is detected from the key prefix. An `sk-or-` key uses OpenRouter with `google/gemini-3.7-flash`, anything else uses the Anthropic API with `claude-haiku-4-5-20251001`. Set `ENGLISHREFINER_MODEL` or change the `MODEL` variable in the script to swap models.

## Model benchmarks

Tested with a message containing typos, comma issues, and wrong article usage. Quality rated on whether meaning is preserved while improving readability. These benchmarks predate the switch to direct Anthropic API and are kept for reference on model choice.

| Model | Speed | Quality | Notes |
|-------|-------|---------|-------|
| google/gemini-2.0-flash-lite-001 | 0.8s | Perfect | Fast, consistent, preserved meaning |
| anthropic/claude-3-haiku:beta | 1.1s | Good | Occasionally adds preamble |
| openai/gpt-5.4-nano | 0.8s | Good | Inconsistent article/dash usage |
| inception/mercury-2 | 0.7s | Good | Inconsistent speed and wording |
| anthropic/claude-3.5-haiku:beta | 2.2s | Good | Same as claude-3-haiku, slower and pricier |
| openai/gpt-oss-120b | 3.5s | Good | Clean output, too slow |
| google/gemini-2.5-flash-lite | 0.7s | OK | Sometimes changes word choices |
| z-ai/glm-5-turbo | 9.5s | OK | Too slow |
| bytedance-seed/seed-1.6-flash | 3.6s | OK | Emdashes, inconsistent |
| stepfun/step-3.5-flash | 5.0s | OK | Too slow, emdashes |
| xiaomi/mimo-v2-flash | 1.1s | OK | Wildly inconsistent speed (1-12s) |
| openai/gpt-4.1-nano | 0.8s | Poor | Changed meaning |
| liquid/lfm-2-24b-a2b | 1.0s | Poor | Rewrote sentences, changed meaning entirely |
| mistralai/ministral-3b-2512 | 0.4s | Poor | Fastest but rewrites everything |
| google/gemini-3.1-flash-lite-preview | 6.1s | Poor | Expanded contractions, too formal |
| openai/gpt-5-nano | 14.8s | Poor | Way too slow |
| qwen/qwen3.5-122b-a10b | 52.7s | Poor | Too slow |
| qwen/qwen3.5-35b-a3b | 55.5s | Poor | Too slow |
| qwen/qwen3.5-flash-02-23 | 77.0s | Poor | Too slow |
| qwen/qwen3.5-9b | 103.6s | Poor | Too slow |
| bytedance-seed/seed-2.0-mini | 122.9s | Poor | Too slow |
| bytedance-seed/seed-2.0-lite | 55.4s | Poor | Too slow |
| z-ai/glm-4.7-flash | 28.1s | Poor | Too slow |
