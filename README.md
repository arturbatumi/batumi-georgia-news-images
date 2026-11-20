# Batumi Georgia News — public editorial media

Only publication-ready images intended for public viewing. Never store source code, secrets, or tokens here.

## Telegram: large photo preview without a duplicated news headline (editor decision 20.11.2026)

For **new** `previews/*.html` pages used as `telegram_longform_preview_url`, keep the approved photo and all `og:image` / size metadata, but **do not put the article's headline in HTML `<title>` or `og:title`**. Telegram renders those fields above the photo, then repeats the article headline from the message text.

Use neutral, short preview-only metadata:

```html
<title>Фото</title>
<meta property="og:type" content="article">
<meta property="og:title" content="Фото">
<meta property="og:site_name" content="Batumi Georgia News">
```

Do not add `og:description`, story text, overlay headlines, or extra text to images. Keep the **full approved article text and headline in the Telegram message itself**, using the existing `InputMediaWebPage(force_large_media=True)` longform path in the scheduler. The preview remains a clickable link to the public HTML photo page; this method does not make it a native Telegram photo. Do not promise that the click/open action disappears.

**Important:** existing URLs use a Git commit SHA, so modifying an HTML file on `main` does **not** alter a previously published or already pinned preview. For every future post, generate a fresh page from this metadata, commit it, and use its new immutable URL in the approval before publishing. Do not rewrite already approved/scheduled posts or republish historic posts without explicit separate approval and duplicate preflight.
