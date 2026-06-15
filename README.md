# QRify Website

Static site for **QRify - Scan & Generate**, hosted on GitHub Pages.

- Landing page: https://qrify-scan-generate.github.io/
- Privacy Policy: https://qrify-scan-generate.github.io/privacy/

---

## Structure

```
/
├── index.html        # Landing page (EN/VI)
├── privacy/
│   └── index.html    # Privacy Policy (EN/VI), applies to all app versions
└── assets/
    └── style.css      # Shared styles
```

> **Note:** When updating App Store / Google Play privacy URL, use
> `https://qrify-scan-generate.github.io/privacy/` — this URL stays the same
> across app versions. Track policy changes in the "Version History" section
> on the privacy page instead of creating new URLs per version.

---

## Deploy to GitHub Pages

1. Go to the repo on GitHub → **Settings**
2. Left sidebar → **Pages**
3. Source: **Deploy from a branch**
4. Branch: **main** / **(root)**
5. Click **Save**
6. Wait ~1 minute → the URL will appear

---

## Custom Domain (optional, later)

1. Fill in your domain in the `CNAME` file (e.g. `yangwave.com`)
2. Add a CNAME DNS record pointing to `qrify-scan-generate.github.io`
3. In GitHub Pages settings → enter the custom domain → enable **Enforce HTTPS**
