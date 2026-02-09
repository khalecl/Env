# CLAUDE.md

## Project Overview

This is an **educational and training platform for Environmental Impact Assessment (EIA)**, ESG diagnostics, and climate policy simulation. It consists of standalone, self-contained HTML files with embedded CSS and JavaScript — there is no build system, package manager, or backend server.

The target audience is environmental professionals in the UAE/Gulf region. Content is in both **English** and **Arabic (RTL)**.

## Repository Structure

```
Env/
├── act1.html              # Activity 1: ESG Function Diagnostic (English, Firebase)
├── act2.html              # Activity 2: ESG Quest Leadership Challenge (English)
├── oilcarb.html           # Carbon Footprint Calculator - Scope 1 & 2 (English, Chart.js)
├── policy.html            # Aramco Climate Policy Strategy Simulator (English, Chart.js)
├── eiareview.html          # Interactive EIA Review Scenario (Arabic)
├── day2a.html             # Exercise 1: Basic Data Assessment (Arabic, RTL)
├── day2b.html             # Exercise 2: Leopold Matrix Analysis (Arabic, RTL)
├── day2c.html             # Exercise 3: Mitigation Measures Analysis (Arabic, RTL)
├── تأثير التواصل الجيد.html      # Communication Impact Training (Arabic, RTL)
├── تحليل أصحاب المصلحة.html     # Stakeholder Analysis Training (Arabic, RTL)
├── صياغة التعليقات الفنية.html    # Technical Comments Formulation (Arabic, RTL)
├── عملية صنع القرار المتدرجة.html  # Tiered Decision-Making Process (Arabic, RTL)
├── eiar.txt               # Full EIA Report text (Arabic, ~95K)
├── resources/
│   ├── Federal Law No. (12) of 2018 on Integrated Waste Management.pdf
│   └── Federal Law No. (24) of 1999 Concerning Environmental Protection.pdf
└── CLAUDE.md              # This file
```

## Architecture & Technology

- **No build system** — no `package.json`, no bundler, no compiler
- **No tests** — no test framework or test files
- **No CI/CD** — no pipeline configuration
- **No server-side code** — all logic is client-side JavaScript

Each HTML file is **fully self-contained**: it includes its own `<style>` and `<script>` blocks and can be opened directly in a browser.

### External Dependencies (loaded via CDN)

| Dependency | Files | Purpose |
|---|---|---|
| Firebase SDK 10.0.0 | `act1.html` | Real-time database for persisting user responses |
| Chart.js 3.9.1 | `oilcarb.html`, `policy.html` | Data visualization (emissions charts, policy graphs) |
| Google Fonts (Inter, Space Mono) | `act2.html` | Typography |

## Code Conventions

### HTML Structure
- All files start with `<!DOCTYPE html>` and proper `<meta charset="UTF-8">` / viewport tags
- Arabic files use `<html lang="ar" dir="rtl">` with `direction: rtl` in CSS
- English files use `<html lang="en">`

### CSS Patterns
- **CSS custom properties** (`:root` variables) for theming in newer modules (`oilcarb.html`, `act2.html`)
- **Gradient backgrounds**: `linear-gradient(135deg, ...)` is the standard pattern
- **Layout**: Flexbox and CSS Grid; `.container` with `max-width` for centering
- **Component styling**: `.main-panel`, `.panel-header`, `.panel-content` pattern
- **Font stack**: `'Segoe UI', Tahoma, Geneva, Verdana, sans-serif` (default)
- **Box model reset**: `* { margin: 0; padding: 0; box-sizing: border-box; }` in every file
- **Visual effects**: `box-shadow`, `border-radius: 12px–20px`, `backdrop-filter: blur()`, keyframe animations

### JavaScript Patterns
- **Inline event handlers**: `onclick="functionName()"`, `onchange="handler()"`
- **Global functions and variables** — no module system
- **Step-based navigation**: `goToStep('step-N')` pattern with `.step-container` divs toggled via `display: none/block`
- **Star rating widgets**: clickable `<span>` elements with Unicode stars (`★`)
- **Data stored in global objects** (e.g., `summaryData = {}`)
- **Firebase writes** use `firebase.database().ref(...).set(...)` or `.push(...)`

### Color Palette (common across modules)
- Primary blues: `#004972`, `#005a94`, `#1e3c72`, `#2a5298`
- Accent gold: `#FFC000`
- Accent cyan: `#00d4ff`, `#2dd4bf`
- Success green: `#00ff88`
- Warning orange: `#ffaa00`
- Danger red: `#ff3333`

## Development Workflow

1. **Edit** any `.html` file directly — no compilation or build step required
2. **Preview** by opening the file in a web browser
3. **Test interactively** — fill out forms, click through steps, verify Firebase writes (for `act1.html`)
4. **Commit and push** to the repository

### When Adding a New Module
- Create a new `.html` file at the repository root
- Include the standard box-model reset and font stack
- For Arabic content: set `lang="ar" dir="rtl"` on `<html>` and `direction: rtl` on `body`
- Use the existing gradient background and panel styling patterns for visual consistency
- Keep all CSS and JS inline within the single file

### When Modifying Existing Modules
- Each file is independent — changes to one file do not affect others
- Preserve the existing styling conventions (gradients, border-radius, shadows)
- If using Firebase, the config is in `act1.html` — do not duplicate credentials unnecessarily
- Chart.js is loaded from CDN; no local copies exist

## Key Domain Context

- **EIA** = Environmental Impact Assessment — a regulatory process for evaluating environmental effects of proposed projects
- **ESG** = Environmental, Social, and Governance — a framework for evaluating organizational sustainability
- **Scope 1 emissions** = direct emissions from owned/controlled sources
- **Scope 2 emissions** = indirect emissions from purchased electricity, heat, or steam
- **Leopold Matrix** = a method for identifying and assessing environmental impacts
- The EIA report (`eiar.txt`) references a chemical plant project in Ras Al Khaimah, UAE
- Regulatory references are to UAE Federal Laws on environmental protection and waste management

## File Naming

- English modules: descriptive lowercase names (`act1.html`, `oilcarb.html`, `policy.html`)
- Arabic modules: either `day2X.html` format or Arabic-language filenames
- Resource documents: full descriptive names with spaces (stored in `resources/`)
