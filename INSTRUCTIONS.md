# dd26.parth.gg — what this is, and how to go live on stage

## What this page is

A single-page personal recap microsite for the talk "The Future of Development on OutSystems: Agentic Systems Engineering" (Developer Days Bengaluru). QR-coded on the closing slide. Self-contained static HTML — no build step, no external network calls, loads instantly on conference wifi.

**Sections:** hero (talk title/subtitle/byline + OutSystems/Developer Days badges) → "How it worked" pipeline strip (deliberately generic: "AI design tool" / "AI harness", no specific product named — the point of the talk is that any harness + any design tool can replicate this) → "See it live" CTA (app link) → "How it was built" (starter-repo link, Forge link, and a permanently-unlinked "full write-up · 🕒 coming later" card) → footer (LinkedIn only).

**Hosting:** this repo (`dd26-site`) is private on GitHub. Your hosting server has a webhook watching it — any push to `main` triggers an automatic redeploy. There is no manual deploy step; pushing IS shipping.

**Current shipped state on `main`:** CTA locked ("Unlocking during the talk..."), starter-repo and Forge links are `href="#"` placeholders, write-up card is permanently unlinked with a clock icon (no ETA, update whenever the write-up actually exists — not part of any stage-day flow).

## The stage-day "second push" — going live

This pairs with flipping the **separate** `DD26-DigitalChaos` starter-kit repo from private to public — do both around the same moment (see its own `PUBLISH.md`, Stage 2).

**What's already pre-staged on the `go-live` branch of this repo** (`dd26-site`):

1. CTA unlocked → `https://parthsharmademos.outsystems.app/DigitalChaos/`, `cta-active`
2. Starter-repo card → `https://github.com/Xoltox/dd26-digitalchaos`
3. Forge card → still `href="#"` placeholder — fill in once the Forge component is actually published (may not be ready by stage day; leave as-is if not, it just won't be clickable yet)
4. Write-up card → untouched on purpose, stays unlinked indefinitely

On stage, going live is one clean command block:

```bash
cd "/Users/parth.sharma/Projects/DD26 Lab/dd26-site"
git checkout main
git merge go-live
git push
```

No live-typing URLs in front of an audience. If the Forge link becomes available before stage day, fill it into `go-live`'s `href="#"` (the `.build-card` for "Get it on Forge") and re-commit before merging — same branch, same flow.

**Instant client-side preview alternative** (not a real deploy, doesn't persist, only visible in your own browser session): the commented-out `unlockApp(url)` helper in `index.html`'s `<script>` block does the same CTA class+href swap live via devtools console. Useful to sanity-check the look before the real push, not a substitute for it.

## Repo

Private GitHub repo (hosting-only, not the public starter kit — that's the separate `dd26-digitalchaos` repo, also kept private until the post-demo reveal). Push to `main` = live.
