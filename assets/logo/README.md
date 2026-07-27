# Logo Files — Sudheer Samudrala

Mark: two "S" initials in a viewfinder/crosshair frame, one inverted on a lime-on-black chip. Matches the site's brutalist console palette: ink `#0a0a0a`, paper `#ffffff`, lime accent `#d4ff3d`.

## Icon / mark only
- `logo-icon-transparent.svg` / `logo-icon-transparent-512.png` — transparent background, ink-only mark. Use for favicons, watermarks, anywhere you need it to sit on an existing background.
- `favicon-16.png`, `favicon-32.png`, `favicon-192.png` — pre-sized from the transparent mark for `<link rel="icon">` tags.
- `logo-icon-dark-bg.svg` / `app-icon-dark-512.png`, `android-chrome-192.png`, `apple-touch-icon-180.png` — filled black square (no transparency) — use for app icons, social profile avatars, and anywhere a platform requires an opaque square (Apple/Android/social icons flatten transparency unpredictably otherwise).
- `logo-icon-light-bg.svg` / `app-icon-light-512.png` — filled white square version, for use on dark or colored surfaces where a light chip reads better (e.g. printed materials on a dark stock).

## Full lockup (mark + wordmark)
- `logo-lockup-light.svg` / `logo-lockup-light-1200.png` — mark + "SUDHEER_SAMUDRALA" wordmark, transparent/white background. Use in site headers, letterhead, email signature.
- `logo-lockup-dark.svg` / `logo-lockup-dark-1200.png` — same lockup, black background, white wordmark — for dark headers/footers or the SAMSBPM section treatment.

## Notes
- All SVGs are plain vector markup (editable in Illustrator/Figma/Inkscape) using a monospace font stack (`Space Mono`, falling back to `JetBrains Mono`, then system monospace) to match the site's typography. If Space Mono isn't installed on the machine opening the SVG, text falls back to the system monospace font — reapply Space Mono there if you have it installed for exact fidelity. The pre-rendered PNGs were rasterized without the webfont loaded, so their wordmark text uses a fallback bold sans — regenerate from the SVGs with Space Mono installed for pixel-exact wordmark PNGs.
- No `.ico` file included — modern browsers accept PNG favicons via `<link rel="icon" type="image/png" sizes="32x32" href="favicon-32.png">` (repeat for 16x16192x192). Generate a `.ico` separately if you need legacy support.
