# SocialPay permanent entry address

This GitHub Pages project provides one stable entry address for SocialPay. `go.html` reads the current HTTPS backend from `config.json`, then redirects to the requested route on that backend.

## Update the Railway address

Edit only `config.json` when the Railway hostname changes:

```json
{
  "server_url": "https://YOUR-CURRENT-RAILWAY-HOST.up.railway.app",
  "version": 2
}
```

Keep `server_url` as the origin only (no route or trailing path), and keep it HTTPS. Do not put secrets or API keys in this public repository.

## Permanent entry URL examples

Base/home page:

`https://ahmadiliyasu7031-coder8.github.io/socialpay-config/go.html`

Referral:

`https://ahmadiliyasu7031-coder8.github.io/socialpay-config/go.html?ref=REFERRAL_CODE`

Any app route (the path is URL-encoded):

`https://ahmadiliyasu7031-coder8.github.io/socialpay-config/go.html?path=%2Ftasks`

Other examples:

- Buy Data: `?path=%2Fbuy-data`
- Buy Gmail: `?path=%2Fbuy-gmail`
- Wallet: `?path=%2Fwallet`
- Login: `?path=%2Flogin`

Replace the example paths with the exact routes that actually exist in the deployed SocialPay app. The redirect preserves additional query parameters and referral codes. When `path` is omitted, a valid `ref` opens `/r/REFERRAL_CODE`; with neither, it opens the app home page.

## Important integration note

This project handles the browser entry/redirect only. SocialPay's own TinyURL creation code must also be updated to generate links through this permanent `go.html` address, using `path=` for non-referral destinations and `ref=` for referrals. The app's API/backend base URL is a separate setting; this redirect does not act as an API reverse proxy.

## GitHub Pages

Enable GitHub Pages for the `main` branch and repository root. After each edit, allow GitHub Pages to finish publishing before testing. Test the base URL, a referral URL, and at least one real app route.
