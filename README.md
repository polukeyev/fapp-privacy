# Sperar — legal / site

Static site for **Sperar** (operator of *SMS Forwarding: AutoRelay*), served via
**Cloudflare Pages** at `https://sperar.com/`.

Pure static HTML — no build step, no Jekyll. Cloudflare Pages serves
`*.html` files at clean URLs (e.g. `privacy.html` → `/privacy`).

## Structure & public URLs

| File | URL |
|------|-----|
| `index.html` | https://sperar.com/ |
| `privacy.html` | https://sperar.com/privacy |
| `terms.html` | https://sperar.com/terms |
| `refund.html` | https://sperar.com/refund |

Cross-links between pages use root-relative paths (`/privacy`, `/terms`,
`/refund`) so they are domain-agnostic.

## Cloudflare Pages setup

1. Cloudflare dashboard → Workers & Pages → Create → Pages → Connect to Git →
   select this repo (`polukeyev/fapp-privacy`, branch `master`).
2. Build settings: **Framework preset = None**, Build command = *(empty)*,
   Build output directory = `/` (root).
3. Custom domain: add `sperar.com` (apex) to the Pages project.
4. Verify `sperar.com/privacy`, `/terms`, `/refund` resolve and render.

## Filled-in details

- Operator: **Sperar**, a trade name of Oleg Polukeev (update to KZ ИП after registration)
- App name: **AutoRelay** (full Play name: *SMS Forwarding: AutoRelay*)
- Support email: **urbandevapp@gmail.com** (migrate to support@sperar.com later)
- Refund window: **14 days**
- Governing law: **Republic of Kazakhstan**
- Merchant of Record: referenced generically ("third-party payment provider
  acting as the Merchant of Record") until a payment provider approves the store.
  Name the specific provider in `terms.html` / `refund.html` once live.

> Not legal advice — solid working templates. A quick review before relying on
> them is recommended.
