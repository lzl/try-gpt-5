# Repository Guidelines

## Project Structure & Module Organization
The repository contains standalone HTML apps at the root: `balls-rotating-polygon.html`, `crypto-portfolio-rebalance.html`, `crypto-weekly-ratio.html`, and `portfolio-total-mdd.html`. Each file embeds its own CSS and JavaScript, so feature updates should stay in-file unless you introduce a reusable asset. Place any shared helpers under a new `lib/` directory and reference them with relative paths to avoid CDN drift.

## Build, Test, and Development Commands
- `open <file>.html` (macOS) or double-click the file to preview locally in Chrome/Edge; no build step is required.
- `python3 -m http.server 8000` from the repo root serves all pages with correct CORS headers for fetch requests to exchanges; visit `http://localhost:8000/<file>.html`.
- `npx prettier --check "*.html"` validates formatting before you commit.

## Coding Style & Naming Conventions
Use two-space indentation and keep inline scripts organized into top-level configuration, DOM bindings, and render/update functions. Prefer `const` and `let` over `var`, camelCase for variables/functions, and PascalCase for component-like helpers. Inline CSS follows BEM-style class names when new panels or controls are added. Run `npx prettier --write "*.html"` if structure changes become hard to read.

## Testing Guidelines
There is no automated test suite; rely on manual verification. After changes, refresh each affected page, use the provided UI controls, and watch the browser console for warnings. For finance tools, confirm live data loads by toggling the Binance price fetch and X-to-USDT bridge suggestions. Capture before/after screenshots when behavior changes.

## Commit & Pull Request Guidelines
Existing history uses short, imperative messages (e.g., `Update crypto-weekly-ratio.html`). Follow that style but call out the feature or fix. Every pull request should describe the scenario, link relevant issues if any, and attach screenshots or screen recordings for UI changes, plus reproduction steps for bug fixes. Note any external APIs touched so reviewers can retest.

## Security & Data Source Notes
Never commit API keys or secrets; the current tools rely only on public REST endpoints. Document new endpoints or rate limits, and guard fetches with clear error messaging so contributors can diagnose live-data failures quickly.
