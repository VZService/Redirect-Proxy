# VZ-Redirect-Proxy

*English* | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md)

A minimalist, beautiful, and feature-rich **redirect intermediary page**. It supports dynamic URL routing via parameters, automatic target site icon fetching, millisecond-level countdown animations, smart dark/light mode adaptation, and anti-abuse protection when no parameters are provided.

**Live Demo:** `https://url-r.pages.dev`

## ✨ Core Features

- **Dynamic Redirect**: Dynamically set the target URL via the `?to=example.com` URL parameter. If no parameter is provided, it denies the redirect and displays a prompt: "Please enter via a friend's shared link".
- **Millisecond Countdown**: A 10-second countdown (with 4 decimal places). In the last 3 seconds, the background smoothly transitions to green, the progress bar gradients, and it smoothly blackouts and redirects when it hits zero.
- **Smart Icon Fetching**: Automatically requests the target site's `favicon.ico`. In dark mode, it automatically adds a white background to prevent black icons from blending in. If the target has no icon or times out, it gracefully falls back to an inline "circle i" SVG.
- **Quick Jump**: Provides a "Go now" button (with a bright blue gradient hover effect). Clicking it immediately freezes the countdown, turns the page grayscale, cancels the auto-redirect, and navigates to the target site after 0.3 seconds.
- **Extremely Lightweight**: The entire code is contained in a single HTML file with zero external CSS/JS framework dependencies. Native support for dark/light mode (`prefers-color-scheme`).

## 🚀 How to Use

### 1. Redirect with Parameters
Share the link directly, and it will automatically redirect to the specified site:

`https://url-r.pages.dev/?to=github.com`

*(Supports missing protocol prefixes, the system will automatically prepend `https://`)*

### 2. Access without Parameters
If a user visits `https://url-r.pages.dev/` directly (without the `to` parameter), the page will:
- Hide the countdown and redirect button.
- Change the tab `<title>` to `Tip`.
- Display the prompt: "Please enter via a friend's shared link".

### 3. Customize Styles
Modify the CSS variables in `:root` and `@media (prefers-color-scheme: dark)` within the `<style>` tag to quickly customize the theme color, button color (default `#33ACE9`), etc.

## 🛠️ Technical Details

- **Vanilla Implementation**: ES6 syntax, using `requestAnimationFrame` for smooth countdowns.
- **Anti-Black-Box Favicon**: The tab icon is hardcoded to a specific SVG, avoiding the dark mode black box bug by replacing the `fill` color.
- **Security Protection**: Uses `new URL()` to strictly validate redirect parameter protocols (only `http/https` allowed). Includes a 3-second timeout fallback for icon fetching to prevent malicious parameters from freezing the page.

## 📄 License
MIT License. See the `LICENSE` file for details.
