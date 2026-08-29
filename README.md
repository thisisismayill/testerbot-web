# TesterBot — website

The public site for **TesterBot**, a free, open-source website audit tool that runs on your own
machine: it crawls a site in a real browser and reports accessibility, performance, security, SEO
and internationalisation problems in one self-contained HTML report.

**Live:** https://testerbot-web.vercel.app

## What is in this repository

| File | What it is |
|---|---|
| `index.html` | The landing page. Single file — all CSS and JS inlined, screenshots embedded as data URIs. |
| `sample-report.html` | A real report produced by the tool, published so people can read one before downloading anything. Self-contained. |
| `testerbot.zip` | The tool itself (825 KB). Served with `Content-Disposition: attachment` so it downloads instead of opening. |
| `og-image.png` | 1200×630 social share card referenced by the Open Graph and Twitter tags. |
| `favicon.svg` | Site icon. |
| `robots.txt` | Crawl rules; points search engines at the sitemap. |
| `sitemap.xml` | The two indexable URLs. Update `lastmod` when the pages change. |
| `vercel.json` | Clean URLs, no trailing slash, and the download header for the zip. |

There is no build step. Every page is a single static file: edit it, commit it, and Vercel
publishes it.

## Deploying

The repository is connected to Vercel. Any push to the default branch deploys automatically —
either by pushing with git, or by using **Add file → Upload files** on GitHub for a one-off change.

## SEO checklist

Kept here so nothing is forgotten when the pages change:

- [x] Unique `<title>` under 65 characters on every page
- [x] `<meta name="description">` around 150 characters
- [x] `<link rel="canonical">` on every page
- [x] Open Graph and Twitter card tags, including `og:image`
- [x] `SoftwareApplication` JSON-LD on the landing page
- [x] One `<h1>` per page, no skipped heading levels
- [x] `alt` text plus `width`/`height` on every image
- [x] `robots.txt` and `sitemap.xml`
- [ ] Verified in Google Search Console and the sitemap submitted
- [ ] A real domain instead of `*.vercel.app`
- [ ] More indexable content — the landing page is around 650 words

## Licence

The site content is © its authors. The tool in `testerbot.zip` is MIT licensed.
