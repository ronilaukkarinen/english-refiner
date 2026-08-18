### 1.3.0: 2026-08-18

* Detect provider from the key prefix so either key works
* Default OpenRouter to google/gemini-2.5-flash-lite for sub-second refining
* Add voice-preservation rules so the fast model proofreads instead of rewriting
* Allow overriding the model with ENGLISHREFINER_MODEL

### 1.2.0: 2026-04-13

* Switch model to openai/gpt-5-chat for smarter refinement with consistent capitalization
* Restore original open-webui prompt that actively refines wording
* Add sentence-case capitalization rules from open-webui system prompt
* Add rule to preserve curse words and crude language as written
* Add rule to replace spoken-word slang with proper written English
* Update englishrefiner-linux to match macOS script

### 1.1.0: 2026-04-05

* Add Linux support with separate englishrefiner-linux script
* Support wl-clipboard (Wayland) and xclip (X11) for clipboard operations

### 1.0.1: 2026-03-26

* Switch model from liquid/lfm-2-24b-a2b to google/gemini-2.0-flash-lite-001 for better meaning preservation and sub-second speed
* Update benchmark table with 23 models tested for speed, quality, and consistency

### 1.0.0: 2026-03-24

* Initial release
* TUI mode with gum for interactive text editing
* Clipboard mode (-c) for quick refine and paste back
* Pipe mode for stdin input
* OpenRouter API integration with configurable model
* Error display for API failures
* Auto-copy result to clipboard
* System prompt tuned for CTO-to-customer communication
