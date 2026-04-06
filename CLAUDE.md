# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Eventually** is a static HTML5 "coming soon" landing page template by HTML5 UP (html5up.net), licensed under CCA 3.0. It features an email signup form and an auto-rotating slideshow background.

There is no build system, package manager, or backend. The template is production-ready as static files.

## Architecture

**Entry point:** `index.html` loads `assets/css/main.css` and `assets/js/main.js`.

**SASS source** lives in `assets/sass/` with this structure:
- `main.scss` — root entry that imports all partials
- `base/` — reset, page, background, typography
- `components/` — button, form, icon, list, section
- `layout/` — header, footer, signup-form
- `libs/` — variables, mixins, functions, breakpoints, vendor prefixes

The compiled output is `assets/css/main.css`. Edit the SASS source; the CSS is a build artifact.

**JavaScript** (`assets/js/main.js`) has two self-contained modules:
- **Slideshow Background** (~lines 32–102): Cycles through images every 6 seconds with CSS transitions. Configure image list and `delay` value in this block.
- **Signup Form** (~lines 104–169): Client-side validation with hooks for AJAX integration (e.g. MailChimp). For non-AJAX form submission, remove this block and set the `action` attribute on the `<form>` tag instead.

## Customization Reference

**Adding/changing slideshow images** — Edit the `images` object in the "Slideshow Background" block of `main.js`:
```js
'images/your-image.jpg': 'center'  // values: 'top', 'center', 'bottom'
```

**Signup form integration:**
- AJAX approach: fill in the AJAX handler inside the "Signup Form" block in `main.js`
- Non-AJAX approach: set `action` on `<form>`, delete the "Signup Form" JS block entirely

**SASS compilation:** If you modify SASS files, recompile to `assets/css/main.css`. No config file is included — use any SASS compiler (e.g. `sass assets/sass/main.scss assets/css/main.css`).
