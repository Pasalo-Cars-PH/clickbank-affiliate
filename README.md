# Stagebound — Concert Ticket Affiliate Site

A static site listing concert/event tours, built for use with affiliate networks
like Partnerize, Impact, or CJ. No build step, no framework — just HTML/CSS/JS,
so it runs free on GitHub Pages.

## Structure

```
index.html                 → homepage (hero, ticket-stub grid, dispatch/blog, about)
affiliate-disclosure.html   → required disclosure page (link this from your footer)
style.css                  → all styling
script.js                  → loads data/events.json and data/posts.json and renders them
data/events.json           → your concerts/shows — EDIT THIS to add real events + affiliate links
data/posts.json            → short blog posts for the "Dispatch" section
```

## 1. Edit your content

Open `data/events.json`. Each entry looks like:

```json
{
  "artist": "Artist Name",
  "tour": "Tour Name",
  "venue": "Venue",
  "city": "City, Country",
  "date": "2026-09-02",
  "priceFrom": 65,
  "genre": "Pop",
  "affiliateUrl": "https://your-real-affiliate-link.com",
  "image": ""
}
```

Once you're accepted into a ticket brand's program on Partnerize, replace
`affiliateUrl` with the tracking link they give you. Add or remove events freely —
the page re-sorts by date automatically.

Do the same for `data/posts.json` for the blog section — a few real posts help
brands see this as an active content site, not a bare link page.

## 2. Push it to GitHub

If you don't have a GitHub account yet, make one free at github.com, then:

```bash
# 1. Create a new empty repo on github.com (no README/license — you have your own)
#    Name it something like: stagebound-site

# 2. In this folder, run:
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/stagebound-site.git
git push -u origin main
```

## 3. Turn on GitHub Pages (free hosting)

1. On your repo's GitHub page, go to **Settings → Pages**.
2. Under "Build and deployment", set **Source** to `Deploy from a branch`.
3. Choose branch `main`, folder `/ (root)`, then **Save**.
4. Wait ~1 minute. Your live URL will appear at the top of that page —
   usually `https://YOUR-USERNAME.github.io/stagebound-site/`.

That live URL is what you submit to Partnerize as your website.

## 4. Apply on Partnerize

1. Go to partnerize.com and sign up as a **publisher/partner**.
2. Use the GitHub Pages URL as your website.
3. Once approved as a publisher, browse the brand directory (ticket sellers like
   StubHub are on Partnerize) and apply per-brand.
4. Once a brand approves you, they'll give you a tracking link — drop it into
   the matching event's `affiliateUrl` in `data/events.json`, commit, and push.
   GitHub Pages updates automatically within a minute or two.

## Notes

- The `affiliate-disclosure.html` page and the footer link to it are there on
  purpose — most affiliate networks and the FTC require a visible disclosure
  when links earn you a commission. Keep it.
- `rel="sponsored"` is already set on ticket links in `script.js` — this is
  Google's recommended tag for paid/affiliate links.
- To add real event photos, put images in an `/images` folder and reference
  them in `events.json`'s `image` field (not wired into the layout by default —
  ask if you want photo cards instead of text-only stubs).
