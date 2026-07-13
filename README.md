# Nimbus Template — Client Demo Site

A ready-to-deploy, ready-to-reskin website template. No build step, no framework — just push and it's live.

## Push to live (phone-only, browser-based)

1. Create a new **empty** GitHub repo (e.g. `nimbus-template`).
2. Upload these files into it (GitHub's mobile web upload works, or open `github.dev` and drag them in).
3. Go to **Cloudflare Pages** → Create a project → Connect to Git → pick this repo.
4. Build settings: leave the build command **empty**, output directory: `/` (root). This is a static site — nothing to build.
5. Deploy. Cloudflare gives you a live `*.pages.dev` URL immediately, and rebuilds automatically on every future push.
6. (Optional, later) Connect a custom domain in the same Cloudflare Pages project settings.

## Reskin for a new client (2 minutes)

Everything lives in one place: the `:root { ... }` block at the top of `css/styles.css`.

Change:
- `--color-void`, `--color-accent`, `--color-metal-*` → the client's palette
- `--font-display` / `--font-body` → swap the Google Fonts `<link>` in both HTML files and these variable names to match
- `.brand-mark` in `styles.css` → replace with the client's actual logo (`<img src="logo.svg">` in place of the `<span class="brand-mark">` in both HTML files)
- Section copy in `index.html` → replace placeholder text, pricing, and the testimonial quote
- `config/brand.example.json` → optional reference copy of the same tokens, useful once you're scripting reskins instead of doing them by hand

## What's already handled

- **No blank-flash page transitions** — native View Transitions API, two lines of CSS, fails safe on unsupported browsers.
- **Security headers** — `_headers` file is read automatically by Cloudflare Pages on deploy.
- **Crash-safe animation** — no heavy 3D/WebGL, no stacked blur; the signature "chrome sweep" effect is pure CSS.
- **Mobile-first, reduced-motion respected** throughout.

## What's not in here yet (add when you have a paying client)

- **Payment** — not included. When a client needs checkout, the cleanest zero-maintenance option is a Stripe Payment Link (no code) or Stripe Checkout via a Cloudflare Pages Function if you need custom logic. Ask me when you're ready and I'll wire it in.
- **Contact form backend** — the footer email link works out of the box; swap in a Cloudflare Pages Function or Formspree if you want an in-page form instead of `mailto:`.
- **Real content** — every price, quote, and case study here is a placeholder. Replace before showing to a real client.
