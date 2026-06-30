# Wykam Tints — Website Package

Plain static HTML/CSS/JS. No build step, no dependencies. Drag the whole
folder into Cloudflare Pages and it deploys.

## Files
```
index.html            Main site
privacy.html          Privacy policy
accessibility.html    Accessibility statement
robots.txt            Crawler rules + sitemap pointer
sitemap.xml           Page list for search engines
img/                  Placeholder images (swap with real photos)
```

## Before you go live — replace these placeholders
1. **Phone** `(305) 000-0000` → real number (appears in nav-free footer, schema, privacy, accessibility)
2. **Email** `hello@wykamtints.com` → real inbox
3. **Domain** `https://wykamtints.com/` → if different, update canonical, OG tags, sitemap.xml, robots.txt, and the JSON-LD `@id`/url fields
4. **Street address** in the JSON-LD block (`REPLACE WITH STREET ADDRESS`) — Google needs this for the map pack. If they're mobile-only with no storefront, change `@type` handling (see Local SEO note below)
5. **Hours** in the JSON-LD `openingHoursSpecification` — set the real ones
6. **Prices** in the Pricing section — confirm Carbon/Ceramic/Ceramic IR numbers
7. **Images** in `img/` — swap each `.webp` for a real photo at the same filename + size

## Wiring the booking form (it currently only shows a success message)
Pick one, all work with static hosting:
- **Formspree / Web3Forms / Basin** — paste an endpoint, change the form to POST
- **Cloudflare Pages Function** — `/functions/submit.js`, send to email or a sheet
- The form has client-side validation already; you only add the submit target

## Consent management (built in)
- Banner appears on first visit: Accept all / Reject all / Customize
- Customize modal: Essential (locked) / Analytics / Marketing toggles
- Choice saved in localStorage; "Cookie settings" link in footer re-opens it
- **Tags only fire after consent.** Open `index.html`, find `applyConsent()`
  in the script, and drop your tags in the marked spots:
  - `if(c.analytics){ ... }` → GA4 or Plausible loader
  - `if(c.marketing){ ... }` → Meta Pixel / Google Ads loader
- Google Consent Mode v2 signal is already wired (safe no-op until gtag exists)

## Accessibility (built in — no third-party overlay)
We deliberately did NOT use an overlay plugin (accessiBe / UserWay style).
Those bolt-on widgets are widely criticized, have been named in ADA lawsuits
themselves, and don't fix the underlying code. Instead the site has:
- Semantic HTML, ARIA labels, skip-to-content link
- Visible keyboard focus everywhere; the tint slider is keyboard-operable
- Respects OS "reduce motion"
- A native toolbar (gold icon, bottom-right): bigger text, high contrast,
  underline links, pause motion — all persistent
This is real WCAG 2.1 AA-oriented compliance, which is what actually protects
against ADA claims.

## Local Miami SEO (built in)
- Title/H1/meta targeted to "window tinting Miami / ceramic tint Miami"
- LocalBusiness (AutoWindowTintingService) structured data with geo, hours,
  service area, services, rating
- FAQPage structured data (eligible for rich snippets)
- Service-area section naming Miami neighborhoods + nearby cities
- sitemap.xml + robots.txt
- OG/Twitter cards for clean link previews

### The off-site work that matters most (do this — it outranks on-page)
1. **Google Business Profile** — claim it, category "Window Tinting Service",
   add photos, post weekly, collect reviews. This is ~50% of local ranking.
2. **Reviews** — Google reviews with the word "tint" + "Miami" in them.
   The `aggregateRating` in schema should reflect real GBP numbers.
3. **NAP consistency** — same Name/Address/Phone on the site, GBP, Yelp,
   Apple Maps, Facebook. Inconsistency hurts.
4. **Citations** — get listed in Yelp, Bing Places, Apple Business Connect.

## Generating real images with AI (to replace placeholders)
Use these prompts in Midjourney / DALL·E / Firefly / Flux. Export at the
listed size, save over the matching file in `img/`. Keep filenames identical.

- `img/og-share.png` (1200×630) — "Cinematic wide shot of a glossy black luxury
  sedan with freshly tinted windows in a dark detailing studio, dramatic gold
  rim lighting, reflective floor, premium automotive advertising, moody, 16:9"

- `img/service-auto.webp` (800×600) — "Black BMW sedan, side windows being
  tinted with dark ceramic film, professional installer's gloved hands,
  clean modern garage, warm lighting"

- `img/service-commercial.webp` (800×600) — "Modern Miami storefront glass
  facade with subtle tinted windows, daytime, palm trees reflected, clean
  commercial photography"

- `img/service-residential.webp` (800×600) — "Bright modern living room with
  floor-to-ceiling windows, sun-control window film, sunlight softened,
  interior design photography"

- `img/service-marine.webp` (800×600) — "Luxury yacht cabin windows with tinted
  glass, ocean view, Miami marina, bright clean marine photography"

- `img/gallery-1..6.webp` (700×700, square) — real install shots: ceramic film
  on glass, squeegee in hand, finished car at golden hour, storefront, tint
  removal, Tesla profile. Square crop.

**Best of all:** use real photos from Wykam's actual jobs. They already post
install content on Instagram — those are more trustworthy than any AI render
and better for SEO (original images, geotagged).

## Nice-to-haves worth adding next
- Click-to-call sticky button on mobile
- WhatsApp / SMS booking link (huge in Miami market)
- Before/after slider using their real photos (same mechanic as the hero demo)
- Google Reviews embed once GBP is live
- Spanish version (`/es/`) — large bilingual market in Miami
- Blog/answers page targeting "Florida tint laws", "best tint percentage" for
  long-tail search traffic
