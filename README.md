# dd26-site

Single-page recap microsite for Parth Sharma's "The Future of Development on OutSystems: Agentic Systems Engineering" talk at Developer Days Bengaluru 2026. Self-contained, no build step — open `index.html` directly or host it as a static file.

## Assets to drop in

The `assets/` folder is where the two logo placeholders referenced in `index.html` should go, if/when you want to swap the current CSS-drawn placeholders for real logo lockup images:

- `assets/outsystems-logo.svg` — the official OutSystems logo. Currently `index.html` uses a small red-dot + "outsystems" text wordmark drawn in CSS instead. To switch to the real logo image, replace that markup with an `<img src="assets/outsystems-logo.svg" alt="OutSystems logo — replace me" height="28">` (the comment right above it in the HTML shows exactly where).
- `assets/developer-days-logo.svg` — the official "Developer Days" event logo/badge. Currently `index.html` ships a real, working CSS pill badge with gradient outline reading "Developer Days" — that's fine to keep as-is. If you'd rather use the official logo image instead, drop the file here and swap in `<img src="assets/developer-days-logo.svg" alt="Developer Days logo — replace me" height="24">` per the comment in the HTML.

Neither file needs to exist for the page to work — the current state (CSS dot/wordmark + CSS pill badge) is fully shippable as-is.

## Three placeholders to fill in before/during the talk

1. **App link** — the `<a id="cta" ...>` element in the "See it live" section. Paste the real app URL into its `href` when ready, and flip its class from `cta-locked` to `cta-active` (see the commented `unlockApp(url)` helper in `index.html`'s `<script>` block — call it from the browser console to do both at once).
2. **GitHub repo link** — first `.build-card` in the "How it was built" section.
3. **Social/contact links** — bottom-right of the footer (`LinkedIn` / `X` / `Email` placeholders).
