# dd26.parth.gg — what this is, and how to go live on stage

## What this page is

A single-page personal recap microsite for the talk "The Future of Development on OutSystems: Agentic Systems Engineering" (Developer Days Bengaluru). QR-coded on the closing slide. Self-contained static HTML — no build step, no external network calls, loads instantly on conference wifi.

**Sections:** hero (talk title/subtitle/byline + OutSystems/Developer Days badges) → "How it worked" pipeline strip → "See it live" CTA (app link) → "How it was built" (GitHub repo link + write-up teaser) → footer (micro-copy + socials).

**Hosting:** this repo is private on GitHub. Your hosting server has a webhook watching it — any push to `main` triggers an automatic redeploy. There is no manual deploy step; pushing IS shipping.

**Current shipped state (as of repo init):** CTA is locked (dimmed, "Unlocking during the talk..."), GitHub repo link and social links are `href="#"` placeholders.

## The stage-day "second push" — going live

Do this mid-talk or right after the live build segment, once you're ready for the QR code to actually work. It's one `git push` — the webhook does the rest.

**What needs to change in `index.html`:**

1. **Unlock the CTA** (~line 497): change
   `<a href="#" id="cta" class="cta-wrap cta-locked">`
   to
   `<a href="https://parthsharmademos-dev.outsystems.app/DigitalChaos" id="cta" class="cta-wrap cta-active">`
   (swap `href="#"` for the real live app URL, and `cta-locked` → `cta-active`.)

2. **Fill the GitHub repo link** (~line 511, first `.build-card`): change its `href="#"` to
   `https://github.com/Xoltox/DD26-DigitalChaos`
   (this assumes the `DD26-DigitalChaos` starter-kit repo has already been published public that morning per its own `PUBLISH.md` — do that first if you haven't.)

3. **Optional** — fill in the footer social links (~line 529) if you want those live too; not load-bearing for the demo.

**Recommended: prep this as a ready commit in advance, don't live-edit on stage.**

Before the talk, make these three edits, commit them to a branch (e.g. `go-live`), and don't push yet. On stage, the "second push" is then just:

```bash
cd "/Users/parth.sharma/Projects/DD26 Lab/dd26-site"
git checkout main
git merge go-live
git push
```

One clean command sequence, no typing URLs live in front of an audience.

**If you'd rather flip it live instantly without waiting on a git push/webhook cycle** (e.g. mid-demo, before you're ready to commit anything): open the browser devtools console on the live page and run the commented-out `unlockApp(url)` helper already sitting in `index.html`'s `<script>` block — it does the same class+href swap client-side, immediately, but only for whoever's session that is (not a real deploy, won't persist or show for QR scanners until the real push happens). Useful as an on-the-spot preview, not a substitute for the actual push.

## Repo

Private GitHub repo (hosting-only, not the public starter kit — that's the separate `DD26-DigitalChaos` repo). Push to `main` = live.
