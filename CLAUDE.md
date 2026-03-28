# CLAUDE.md — CENIA.system

## Project Overview

**CENIA** (Control de Evidencia Nacional con Inteligencia Artificial) is a static multi-page website built in Spanish. It is an early-stage project (v1.0.0) focused on presenting the CENIA concept with navigation between informational pages.

- **Author:** Anthony Propuestas
- **Language:** Spanish (`lang="es"` on all HTML pages)
- **Type:** Static website — no backend, no database, no JavaScript framework

---

## Tech Stack

| Tool | Version | Purpose |
|------|---------|---------|
| [Vite](https://vitejs.dev/) | ^5.4.11 | Dev server, production build, preview |
| HTML | Vanilla | Page structure |
| CSS | Inline `<style>` | Styling (no external stylesheets) |

No JavaScript logic, no frontend framework (React, Vue, etc.), no backend.

---

## Directory Structure

```
CENIA.system/
├── index.html                                    # Main landing page (CENIA home)
├── contacto.html                                 # Contact page
├── presupuesto.html                              # Budget/quote page
├── package.json                                  # npm manifest with Vite scripts
├── package-lock.json                             # Dependency lock file
├── README.md                                     # Minimal project description
├── Gemini_Generated_Image_iw9kljiw9kljiw9k.png  # Local hero image (1176×1250 RGBA PNG)
└── Diseño sin título.mp4                         # Local demo video (~950 KB MP4)
```

---

## Development Workflow

```bash
# Install dependencies (first time or after cloning)
npm install

# Start local dev server (hot reload)
npm run dev

# Build for production output
npm run build

# Preview the production build locally
npm run preview
```

Vite uses default configuration (no `vite.config.js` exists). The dev server serves all HTML files at their filename paths (e.g., `http://localhost:5173/contacto.html`).

---

## HTML Conventions

- All pages declare `<!DOCTYPE html>` and use `lang="es"`.
- Character encoding is always `<meta charset="UTF-8">`.
- No `<meta name="viewport">` is currently set — add it when adding responsive layouts.
- Inter-page navigation uses **relative paths**: `href="contacto.html"`, `href="presupuesto.html"`.
- External links (e.g., GitHub repository) use absolute URLs.
- Pages follow a flat structure — all HTML files live at the root, not in subdirectories.

---

## CSS Conventions

All CSS is written as **inline `<style>` blocks inside each HTML file** — there are no external `.css` files.

### Button pattern (`.btn-todos`)

Used for all navigation/call-to-action links styled as buttons:

```css
.btn-todos {
    text-decoration: none;
    background-color: #00ff00;  /* bright green */
    color: #000000;
    padding: 15px 30px;
    border-radius: 15px;
    transition: background-color 0.3s ease;
}
.btn-todos:hover {
    background-color: #000000;  /* hover: black */
}
```

### Color scheme

| Token | Value | Usage |
|-------|-------|-------|
| Primary | `#00ff00` | Button backgrounds, accents |
| Text / Hover | `#000000` | Button text, hover state |

- Always use `transition: background-color 0.3s ease` on interactive elements.
- Border radius of `15px` for rounded buttons.

---

## Assets

Local asset files are tracked in the repository:

| File | Type | Dimensions/Size |
|------|------|-----------------|
| `Gemini_Generated_Image_iw9kljiw9kljiw9k.png` | PNG (RGBA) | 1176 × 1250 px |
| `Diseño sin título.mp4` | MP4 video | ~950 KB |

In HTML, these assets are currently referenced via **raw GitHub URLs** (not local paths):

```html
<!-- Image via GitHub raw URL -->
<img src="https://github.com/anthony-propuestas/CENIA.system/blob/main/Gemini_Generated_Image_iw9kljiw9kljiw9k.png?raw=true">

<!-- Video via GitHub raw URL -->
<video src="https://github.com/anthony-propuestas/CENIA.system/raw/refs/heads/main/Dise%C3%B1o%20sin%20t%C3%ADtulo.mp4" controls></video>
```

When adding new assets: add the file to the repo root and reference it using the same GitHub raw URL pattern, or use a relative path for local development (`src="./filename.ext"`).

---

## Commit Message Style

Based on the existing git history, commit messages are short and descriptive in either Spanish or English, using sentence case or lowercase:

```
# Examples from history:
npm run dev
un boton varios destinos
CORRECCION
pagina presupuesto
estilo de boton
cambio de imagen y video
inicial
```

- Keep messages brief and descriptive.
- No enforced format (no Conventional Commits prefix required).
- Spanish descriptions are preferred but English is acceptable.

---

## No Tests / No CI

- There are **no automated tests** and no test framework.
- There are **no CI/CD pipelines** (no `.github/workflows/`, no Dockerfile).
- Verification is done manually by running `npm run dev` and checking pages in the browser.

---

## Future Considerations

These are not current requirements but good practices to adopt as the project grows:

- **Extract shared CSS** to a `styles.css` file referenced by all pages, to avoid duplicating `.btn-todos` and other repeated styles.
- **Add `vite.config.js`** if multi-page builds, asset handling, or plugins are needed.
- **Add `<meta name="viewport">`** to all pages for mobile responsiveness.
- **Use local asset paths** (e.g., `src="./image.png"`) instead of GitHub raw URLs for reliability during local development and production builds.
- **Add `.gitignore`** to exclude `node_modules/` and Vite's `dist/` output directory.
