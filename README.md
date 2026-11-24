# mixingpods.com

Static export of [mixingpods.com](https://mixingpods.com), ready to host on [Cloudflare Pages](https://pages.cloudflare.com/).

This is a read-only snapshot of the WordPress blog (51 posts, pages, images, and existing comments). It is not a WordPress site anymore: there is no admin, login, or database.

## Cloudflare Pages settings

When you connect this GitHub repository to a Pages project, use:

- **Framework preset:** None
- **Build command:** *(leave empty)*
- **Build output directory:** `public`

The site files are already built. Pages only needs to publish the `public` folder.

`public/_redirects` keeps old WordPress feed URLs (`/feed/`, `/feed/rss/`, `/comments/feed/`, and per-section `/…/feed/`) working by serving the static XML. `public/_headers` sets the correct content types for feeds and sitemaps.

You do not need a www-to-apex redirect in this repo. That can be handled later in DNS, if you want `www.mixingpods.com` to keep pointing at the apex.

## What changed from WordPress

- Permalinks are preserved (for example `/hey-dad-whats-up/`).
- The contact form is a placeholder with a `mailto:tony@mixingpods.com` link, until a spam-protected form is added (a Cloudflare Pages Function plus Turnstile, or a free form service such as Formspree or Basin).
- Comment forms were removed. The existing 28 comments remain as static text.
- WordPress admin, login, xmlrpc, and REST API links were stripped.
- The ~88 MB self-hosted MP4 (`MP2-Change-Requires-a-Foundation-of-Trust.mp4`) is **not** in this repo. Cloudflare Pages rejects files over 25 MiB. The Dad Pool post already embeds the same story on Vimeo (`https://player.vimeo.com/video/426758117`). The original file can be uploaded later to Cloudflare R2 (or YouTube) if you want a self-hosted copy.

## Local preview

Any static file server works. From this directory:

```bash
python3 -m http.server 8765 --directory public
```

Then open http://127.0.0.1:8765/
