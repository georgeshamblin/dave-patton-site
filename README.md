# Dave Patton — Site Backend Package

Built for SEO, AI visibility (ChatGPT, Perplexity, Google AI Overviews), and
schema.org structured data. Placeholder-first so Dave can drop in his real
info and go live.

---

## Files

pages/index.html         — Full HTML scaffold, all schema injected inline
schema/person.jsonld     — Standalone Person + RealEstateAgent JSON-LD
schema/faq.jsonld        — Standalone FAQPage JSON-LD
schema/breadcrumbs.jsonld — Standalone BreadcrumbList JSON-LD
meta/meta-bank.html      — Ready-to-paste <head> blocks for every page
sitemap.xml              — Sitemap template
robots.txt               — robots.txt (AI crawlers allowed)
llms.txt                 — AI systems visibility file (place at site root)

---

## What Needs to Be Filled In

Search for these placeholders in every file and replace:

  [PHONE]           — Dave's phone number
  [EMAIL]           — Dave's email address
  [ZIP]             — Hoover, AL ZIP (35244 or confirm)
  [LAT] [LNG]       — GPS coords for 1021 Brocks Gap Pkwy (approx 33.37, -86.81)
  [DATE]            — sitemap lastmod dates (YYYY-MM-DD)
  [LINKEDIN_URL]    — Dave's LinkedIn profile URL
  [FACEBOOK_URL]    — Dave's Facebook business page URL
  [ZILLOW_PROFILE_URL]    — Dave's Zillow agent page
  [REALTOR_COM_PROFILE_URL] — Dave's Realtor.com agent page

---

## Deploy Checklist

1.  Fill all [PLACEHOLDER] values above.
2.  Upload photos:
      /images/dave-patton-headshot.jpg  (min 800x800)
      /images/logo.png
      /images/og-home.jpg               (1200x630 for social sharing)
      /images/og-about.jpg
      /images/og-services.jpg
      /images/og-senior.jpg
      /images/og-communities.jpg
      /images/apple-touch-icon.png      (180x180)
      /favicon.ico

3.  Place llms.txt at https://davepattonrealty.com/llms.txt
    (this is the AI-visibility file — equivalent of robots.txt for AI crawlers)

4.  Place sitemap.xml at https://davepattonrealty.com/sitemap.xml

5.  Place robots.txt at https://davepattonrealty.com/robots.txt

6.  Submit sitemap in Google Search Console after domain is live.

7.  Validate structured data at:
      https://validator.schema.org
      https://search.google.com/test/rich-results

8.  Add remaining pages (/about/, /services/, /senior-transitions/,
    /communities/, /home-report/, /contact/) — meta blocks are in
    meta/meta-bank.html ready to copy.

---

## Schema Types Used

  Person              — Dave's identity, credentials, contact
  RealEstateAgent     — Business entity, address, hours, areaServed
  FAQPage / Question  — Targets AI Overview and People Also Ask
  BreadcrumbList      — Site navigation structure signal
  Service             — Each individual service offering
  Place               — Each community/area served
  EducationalOccupationalCredential — CSHP and Realtor® designations

---

## AI Visibility Notes

The llms.txt file (place at root) signals to AI crawlers (ChatGPT, Perplexity,
Gemini, Claude) that this site is authoritative for:
  - Dave Patton's identity
  - Senior real estate transitions in Alabama
  - CSHP expertise in Hoover/Birmingham

The FAQPage schema targets Google AI Overviews and voice search directly.
The Person schema with sameAs links is what anchors Dave as a real entity
across AI knowledge graphs — the social/profile URLs in sameAs matter a lot.

---

## Maintenance

- Update sitemap.xml lastmod whenever pages change.
- Monthly Home Report page: add a new /home-report/YYYY-MM/ page each month
  with an Article schema block for SEO compounding over time.
- Testimonials/reviews: add Review schema to the homepage or services page
  once Dave collects them.
