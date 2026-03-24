# English Refiner CLI

A fast TUI tool for refining English text using LLM via OpenRouter. Fixes grammar while preserving your original voice and meaning.

Designed for quick grammar fixes on emails, Slack messages, and GitHub issues.

## Dependencies

- [gum](https://github.com/charmbracelet/gum) - TUI components
- [jq](https://jqlang.github.io/jq/) - JSON parsing
- curl
- [OpenRouter](https://openrouter.ai/) API key

## Installation

```bash
# Install dependencies (macOS)
brew install gum jq

# Create config directory and add your OpenRouter API key
mkdir -p ~/.config/englishrefiner
echo -n 'your-openrouter-api-key-here' > ~/.config/englishrefiner/key
chmod 600 ~/.config/englishrefiner/key

# Install the script
sudo cp englishrefiner /usr/local/bin/englishrefiner
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

## Model

Currently using `liquid/lfm-2-24b-a2b` via OpenRouter. Change the `MODEL` variable in the script to swap models.

## Model benchmarks

Test input: "Hello, I suddenly cant drag anything to the calendar. I have tried restarting the app but that didnt help. Its been like this all day. What is going on? Best regards,"

| Model | Speed | Quality | Notes |
|-------|-------|---------|-------|
| liquid/lfm-2-24b-a2b | 0.8s | Perfect | Minimal changes, added comma after "app" |
| inception/mercury-2 | 1.2s | Perfect | Same quality, added comma after "app" |
| google/gemini-3.1-flash-lite-preview | 2.2s | Perfect | Same quality |
| qwen/qwen3.5-122b-a10b | 3.5s | Perfect | Missing comma after "app" |
| qwen/qwen3.5-35b-a3b | 4.0s | Perfect | Missing comma after "app" |
| qwen/qwen3.5-flash-02-23 | 5.3s | Perfect | Missing comma after "app" |
| z-ai/glm-5-turbo | 8.3s | Perfect | Missing comma after "app" |
| bytedance-seed/seed-2.0-mini | 13.0s | OK | Removed blank line after "Hello," |
| qwen/qwen3.5-9b | 15.2s | Perfect | Way too slow |
| bytedance-seed/seed-2.0-lite | 15.7s | Perfect | Way too slow |
| openai/gpt-oss-120b | 36.3s | Perfect | Best quality but way too slow |
| openai/gpt-4.1-nano | 1.1s | Good | Changed "have tried" to "tried", added "onto" |
| google/gemini-2.5-flash-lite | 0.7s | Good | Changed "It's been" to "This has been happening" |
