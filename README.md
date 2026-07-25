# kelicore.com

The Kelicore landing page. A single static page served by GitHub Pages on
the custom domain [kelicore.com](https://kelicore.com).

No build step, no framework. GitHub Pages serves `index.html` from the repo root
as-is.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The page (hero, venues, health check, proof, services, about, contact, footer). |
| `styles.css` | All styling. Brand palette and responsive layout. |
| `favicon.svg` / `favicon.ico` / `favicon-32.png` / `apple-touch-icon-180.png` | Favicons from the Kelicore icon. |
| `CNAME` | Tells GitHub Pages to serve on the custom domain. |
| `assets/` | The logos and social-preview image actually used by the page. |

> The full brand logo set lives outside this repo, in
> `~/Downloads/kelicore-logo-bundle/` (SVG masters, PNG exports, favicons and
> usage notes), so only the assets the site serves are published.

## Brand

From the logo bundle README:

- Orange `#FF4D00` (accent)
- Slate `#3C4655` (wordmark on light backgrounds, dark surfaces)
- Light `#E8ECF1` (wordmark on dark backgrounds)
- Typeface: Manrope (Google Fonts)
- Tagline: "Infrastructure that just works, wherever it runs."

## Launch checklist

- [ ] Create the GitHub repo (e.g. `Kelicore/kelicore.com`) and push `main`.
- [ ] Enable GitHub Pages (see below) and enforce HTTPS once the cert issues.
- [ ] Point DNS at GitHub Pages (records below).
- [ ] **Web3Forms**: the contact-form access key in `index.html` is domain-locked
      to cloudifinity.com. Create a new access key for kelicore.com (or add the
      domain to the existing key) in the Web3Forms dashboard and replace it.
- [ ] Set up the `hello@kelicore.com` mailbox.
- [ ] Replace the `[TODO]` company number in the footer once Kelicore Ltd is
      registered.

## Local preview

From the repo root:

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000/>.

## Deploying with GitHub Pages

1. Push to the `main` branch.
2. In the repo: **Settings -> Pages**.
3. Under **Build and deployment**, set **Source** to *Deploy from a branch*,
   branch `main`, folder `/ (root)`. Save.
4. The `CNAME` file sets the custom domain to `kelicore.com` automatically.
5. Once the certificate has provisioned, tick **Enforce HTTPS**.

## DNS records

Set these at your domain registrar / DNS provider for the apex domain.

**A records** (`kelicore.com` -> GitHub Pages):

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**AAAA records** (IPv6, same host):

```
2606:50c0:8000::153
2606:50c0:8001::153
2606:50c0:8002::153
2606:50c0:8003::153
```

**CNAME record** for the `www` subdomain (adjust to the GitHub account/org that
hosts the repo):

```
www  ->  kelicore.github.io
```

DNS changes can take a little time to propagate. After they do, GitHub will
issue a TLS certificate for the domain, at which point you can enforce HTTPS.

## Editing content

The copy lives directly in `index.html`. Service cards are in the
`#services` section, contact details point at `hello@kelicore.com`. Update
the text in place and push.
