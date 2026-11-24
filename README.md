# Milestone 2: Accessibility and Visual Design

Dark-mode-only site with three pages: Home (`index.html`), About/Contact (`about.html`), and JavaScript Exercises (`exercises.html`). Files: those three pages, `style.css`, `exercises.js`, and an `images/` folder.

## 1. Accessibility fixes (WAVE)
> Run WAVE (wave.webaim.org) on every page and confirm each line below, then add any extra item WAVE reports.

- Added a "Skip to main content" link so keyboard users can bypass the header and nav.
- Removed the stray space before `<!DOCTYPE html>` and set `lang="en"` on every page.
- Put all page content, including the gallery, inside one `<main>` landmark.
- Fixed heading order (one h1, then h2 for each section) so no heading level is skipped.
- Turned the hobby lines into a real `<ul>` so screen readers announce a list.
- Wrote hobbies in normal sentence case instead of typing them in capitals.
- Fixed grammar ("listening to music") so screen readers read it correctly.
- Gave all 13 gallery photos descriptive `alt` text, plus `width`/`height` to prevent layout shift.
- Marked the current page with `aria-current="page"` plus a non-color cue (filled background and underline).
- Gave every form input a visible `<label>` linked with `for`/`id`.
- Grouped related form fields in `<fieldset>`/`<legend>`.
- Added `autocomplete` to the name and email inputs.
- Made the gallery photo buttons real `<button>` elements with labels like "View larger: Chariot mural".
- Built the photo pop-up on native `<dialog>` so focus stays inside it, Esc closes it, and focus returns to the photo.
- Announced the gallery position ("Photo 3 of 11") through an `aria-live="polite"` status line.
- Marked the decorative background images `aria-hidden="true"`.
- Added a Pause/Play background button because moving content lasting over 5 seconds must be stoppable (WCAG 2.2.2).
- Started the background loop paused when the visitor has `prefers-reduced-motion` turned on.
- Added a live character counter to the message box that announces to screen readers only near the 500-character limit, so it does not read out every keystroke.
- Linked all three pages in the same nav with the current page marked, so navigation is consistent.
- Put the exercise output in a labeled, keyboard-focusable region so screen reader and keyboard users can read it.
- Added a `<footer>` (contentinfo landmark) to every page so each page has a consistent end region.
- Added a `<noscript>` message on the Exercises page so visitors without JavaScript know why the output is empty.
- Added an inline emoji favicon so browsers do not request a missing icon file.
- Added a visible 4px yellow focus outline on every interactive element.
- Gave each page a unique `<title>` and meta description.

## 2. Color contrast (WebAIM Contrast Checker)
The site is dark mode only (`color-scheme: dark`). Every combination passes WCAG AA.

| Text / background | Ratio | Result |
|---|---|---|
| Text #F2F2F7 on page #0E0E14 | 17.24:1 | AAA |
| Text #F2F2F7 on cards #1A1A24 | 15.46:1 | AAA |
| Muted #B8B8C8 on page #0E0E14 | 9.83:1 | AAA |
| Muted #B8B8C8 on cards #1A1A24 | 8.81:1 | AAA |
| Link #7DB4FF on page #0E0E14 | 9.02:1 | AAA |
| Link #7DB4FF on cards #1A1A24 | 8.09:1 | AAA |
| Yellow #FFD60A on header #000000 | 14.88:1 | AAA |
| Dark #14141F on yellow #FFD60A (buttons, current nav) | 12.94:1 | AAA |
| Error #FF7B8F on page #0E0E14 | 7.77:1 | AAA |
| Error #FF7B8F on cards #1A1A24 | 6.97:1 | AA+ |
| Borders #9A9AB0 on page #0E0E14 (non-text, needs 3:1) | 6.98:1 | Pass |
| Worst case: lowest-contrast text over the brightest possible background image (light overlay plus dark content panel) | 6.92:1 minimum | AA+ |

## 3. Gestalt principles
- **Proximity:** I put the three hobbies tight together in one list, with a large gap before the gallery, so they read as one group.
- **Common region:** Each photo row, the About cards, and the form sit inside the same bordered dark cards, so each reads as one unit.
- **Similarity:** All nav links, buttons, and cards share the same borders, corners, and colors, so users recognize what is clickable and what is content.
- **Figure/ground:** The black header with yellow type and the dark content panel over the background photos, make the text stand out from the page behind it.

## 4. Consistent palette
Every page uses the same CSS variables in `style.css`: near-black background, dark gray cards, off-white text, spray yellow, light blue links, pink accent, and soft red errors. Fonts are Eater (page titles) and Karla (everything else).

## 5. Accessible contact form (About page)
- Every input has a `<label>`; related inputs are in `<fieldset>`/`<legend>` (your details, topic radio group, message).
- Validation runs on submit (`novalidate`) so my messages show instead of the browser's.
- Errors appear next to each field, in a summary at the top that receives focus, and as `aria-invalid="true"` on the field.
- Each error is text starting with "Error:" plus an icon and a thick red border, so it never depends on color alone.
- The summary links jump straight to the field with the problem.

## 6. JavaScript features
- **Photo slideshow:** Previous/Next buttons change the photo, wrap around at the ends, and update a status line.
- **Photo pop-up:** Clicking a photo opens it large with Previous, Next, and Close, and the arrow keys work.
- **Looping background:** the five images are CSS classes (`.bg-1` to `.bg-5`) in `style.css`, and a small script at the bottom of each HTML page cross-fades five images every 7 seconds. The photos show clearly around the page, and the text sits on a dark content panel.
- **Message counter:** `about.html` counts characters as you type and enforces a 500-character limit.
- **Exercises:** `exercises.js` runs on `exercises.html`, prints each result on the page and in the console, and covers `let`/`const` with string, number, boolean, and array; functions that return values; `if`/`else` and a ternary; and `for` and `forEach` loops.

## Folder
Keep `index.html`, `about.html`, `exercises.html`, `style.css` and `exercises.js` in the same folder. The gallery photos are saved inside `index.html`, and the originals are in `images/`.