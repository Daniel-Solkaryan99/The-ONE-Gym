# The ONE Gym — Website

A single-file, production-ready website for The ONE Gym (Yerevan). Everything —
markup, styles and behavior — lives in `index.html` so it previews instantly and
deploys anywhere with zero build step. `robots.txt` and `sitemap.xml` ship alongside it.

## What's inside

- **Dark/light theme**, dark by default, remembered across visits (`localStorage`,
  with an in-memory fallback so it never breaks in a sandboxed preview).
- **Armenian / Russian / English** instant switcher — no reload, no backend.
  All copy lives in one `translations` object near the top of the `<script>` block.
- Every section from the brief: hero with animated stats, about, "why choose us",
  three training zones (General Gym / Women Only Gym / Fitness Bar), membership
  plans, coach profiles with expandable bios, weekly coach schedule, masonry
  gallery with a lightbox, testimonials slider, FAQ accordion, newsletter form,
  contact section with an embedded map, and a full footer.
- Loading screen, scroll progress bar, sticky navbar, floating call/WhatsApp/
  back-to-top buttons, sticky mobile CTA, and a cookie-consent banner.
- Semantic HTML, `alt` text on every image, visible focus states, a skip link,
  `prefers-reduced-motion` support, and JSON-LD `ExerciseGym` structured data
  plus Open Graph / Twitter meta tags for SEO.
- No frameworks or build tools — vanilla HTML/CSS/JS only, so there's nothing to
  install and nothing to break.

## Before you launch — replace these placeholders

1. **Photography.** The hero, zone cards and gallery currently use royalty-free
   Unsplash photos (free to use, no attribution required) as stand-ins. Swap the
   `<img src="...">` URLs for real photos of your space once you have them —
   keep the same aspect ratios noted in each `width`/`height` pair for the
   layout to hold.
2. **Coach names, bios and Instagram links.** Search `coach-card` in the file —
   each `coach-ig` link currently points to `#`.
3. **Prices.** The four membership cards use placeholder AMD pricing — update
   the numbers in the `.plan-price` blocks (and the matching `plans.per*`
   translation strings for all three languages).
4. **Map.** The contact section embeds a keyless Google Maps iframe built from
   the address text. For a pinned, branded result, replace the `iframe src`
   with an embed URL from Google Maps' own "Share → Embed a map" tool once you
   have a verified Google Business Profile.
5. **Social links.** Instagram/Facebook/Yandex Maps/Google Maps icons in the
   footer point to `#` — add the real URLs.
6. **Forms.** The newsletter form and cookie banner are fully functional on the
   front end but don't send data anywhere yet — wire the `newsletter-form`
   submit handler to your email provider (Mailchimp, etc.) or a backend
   endpoint.
7. **Domain.** `theonegym.am` is used as a placeholder in the canonical URL,
   Open Graph tags, JSON-LD and `sitemap.xml` — replace it with your real
   domain before launch.

## Editing translations

All copy for all three languages sits in one place: search for
`var translations = {` in `index.html`. It's a plain nested object with three
top-level keys (`en`, `ru`, `hy`); each leaf string maps to a `data-i18n="..."`
attribute in the HTML. To add a fourth language, duplicate one language block,
translate every value, and add a matching button to the two `.lang-switch`
blocks and the footer language list.

## A note on multilingual SEO

Because translation happens client-side for instant switching (per the brief),
search engines will primarily index the default Armenian content. If discoverability
in Russian and English search results matters, the strongest long-term option is
serving `/ru/` and `/en/` as separate pre-rendered routes with `hreflang` tags —
happy to help set that up if you'd like to go that route later.

## Performance notes

Images are served from Unsplash's CDN with `w=`/`q=` params already tuned, and
everything below the fold uses `loading="lazy"`. Fonts are loaded from Google
Fonts with `preconnect`. For the best Lighthouse score in production, self-host
the fonts and replace the Unsplash placeholders with your own optimized
(WebP/AVIF) photography.
