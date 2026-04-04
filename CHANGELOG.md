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
