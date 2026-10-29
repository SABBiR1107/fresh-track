# FreshTrack website

The public website for **FreshTrack — Food Expiry & Waste Saver** (Android).
It exists mainly to host the two URLs the Google Play Console and AdMob ask
for, plus a page that explains what the app does.

## Pages

| Path | What it is |
|---|---|
| `/` | Landing page: what the app does, how the loop works, the privacy summary |
| `/privacy-policy/` | Privacy policy — this is the URL for Play Console and AdMob |
| `/terms/` | Terms of service |

## How it is built

Plain HTML and one stylesheet. No build step, no dependencies, no framework —
so it cannot break on a dependency update, and any static host serves it as
is. `styles.css` carries the app's own Bento palette (grey ground, lighter
tiles, ink accent) with light and dark themes, so the site and the app look
like one product.

## Running it locally

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Deploying

Any static host works, because there is nothing to compile. On Vercel, import
the repository and accept the defaults — framework preset "Other", no build
command, output directory `.`. Folder-per-page means the URLs stay clean
(`/privacy-policy/`) with no rewrite rules.

## Keeping the policy in step with the app

`privacy-policy/index.html` must keep saying what the app actually does. The
app repository holds the same text in `PRIVACY_POLICY.md` and shows a short
version on its in-app "Privacy and food safety" screen. If one changes, change
all three, and bump the effective date here.
