# How to Turn the Dave Patton Backend Into a Live Website
## Step-by-Step Launch Guide

---

## OVERVIEW

Two-track guide. Pick the one that fits:

  TRACK A — Simple/Fast (static site, no CMS)
    Best if: someone technical is managing the site, content rarely changes,
    or you just want it live fast with zero ongoing cost.
    Time to live: ~2 hours.

  TRACK B — WordPress (CMS, Dave can edit himself)
    Best if: Dave wants to log in and update his own copy, add blog posts,
    manage the Home Report, etc.
    Time to live: 3-4 hours + a bit of learning.

Both tracks use the same backend files. The schema, structured data,
and SEO layer are identical. The difference is just how content gets
edited later.

RECOMMENDATION: Start with Track A to get live fast and validate everything.
Migrate to WordPress later if Dave wants self-editing.

---

## BEFORE YOU START — GATHER THESE

Have these ready before you touch anything:

  1. Dave's phone number
  2. Dave's email address
  3. Hoover, AL ZIP code (likely 35244 — confirm for 1021 Brocks Gap Pkwy)
  4. Dave's photo (headshot, min 800x800px, JPG)
  5. Dave's social/profile URLs:
       LinkedIn profile URL
       Facebook business page URL
       Zillow agent profile URL
       Realtor.com agent profile URL
  6. A credit card for domain + hosting (costs below)

Estimated recurring costs:
  Domain: ~$15/year (GoDaddy, Namecheap, Google Domains)
  Hosting Track A: $0 (Netlify free tier) or ~$10/mo (Netlify Pro)
  Hosting Track B: ~$10-20/mo (SiteGround, Bluehost, or WP Engine)

---

## STEP 1 — FILL IN ALL PLACEHOLDERS (30 min)

Open the files in ~/Desktop/dave-patton and find/replace every placeholder.
Do this BEFORE uploading anything.

Files to edit:
  pages/index.html
  schema/person.jsonld
  schema/faq.jsonld
  meta/meta-bank.html
  sitemap.xml
  llms.txt

Placeholders to replace (use Find & Replace in any text editor or VS Code):

  [PHONE]           → Dave's phone, e.g. (205) 555-1234
  [EMAIL]           → Dave's email
  [ZIP]             → Hoover ZIP code (confirm with Dave)
  [LAT]             → 33.3720 (approx for 1021 Brocks Gap Pkwy — verify in Google Maps)
  [LNG]             → -86.8103 (approx — verify in Google Maps)
  [DATE]            → Today's date in YYYY-MM-DD format, e.g. 2026-07-10
  [LINKEDIN_URL]    → https://linkedin.com/in/davepatton (his actual URL)
  [FACEBOOK_URL]    → his Facebook business page URL
  [ZILLOW_PROFILE_URL]   → his Zillow agent page URL
  [REALTOR_COM_PROFILE_URL] → his Realtor.com agent page URL

To get exact GPS coordinates for the office:
  1. Go to maps.google.com
  2. Search: 1021 Brocks Gap Pkwy, Hoover, AL
  3. Right-click the pin → "What's here?"
  4. Copy the lat/lng shown

---

## STEP 2 — PREPARE YOUR IMAGES (30 min)

Create a folder: dave-patton/images/
Add these files (names must match exactly):

  dave-patton-headshot.jpg     — Dave's headshot, min 800x800, JPG/WebP
  logo.png                     — Logo or wordmark, transparent background
  og-home.jpg                  — Social share image, exactly 1200x630px
  og-about.jpg                 — Same size, about page variant
  og-services.jpg              — Same size, services page variant
  og-senior.jpg                — Same size, senior transitions page
  og-communities.jpg           — Same size, communities page
  apple-touch-icon.png         — 180x180px, Dave's logo/icon
  favicon.ico                  — 32x32px icon

For og- images: a clean photo of Dave with his name and tagline
overlaid works great. Use Canva if needed (free, easy).

For favicon: go to https://favicon.io, upload a photo or use initials "DP",
download the package, use the favicon.ico file.

---

## STEP 3 — REGISTER YOUR DOMAIN (15 min)

Recommended registrars (price + ease):
  Namecheap: namecheap.com — cheapest, clean UI
  GoDaddy: godaddy.com — most familiar, slightly pricier
  Google Domains (now Squarespace): domains.squarespace.com

Domain name options to check (in order of preference):
  davepattonrealty.com
  davepattonre.com
  davepattonhomes.com
  pattonrealtyhoover.com
  pattonrealty.com

Steps:
  1. Go to namecheap.com (or your preferred registrar)
  2. Search your top domain choice
  3. Add to cart — select 1 year (or 2-3 years for slight discount)
  4. Enable WhoisGuard (privacy protection) — usually free
  5. Checkout
  6. You will get an email confirming registration
  7. Log in to your registrar dashboard — you'll need it in Step 5

Do NOT buy website builder add-ons. Just the domain.

---

## STEP 4A — DEPLOY VIA NETLIFY (TRACK A — STATIC SITE) (30 min)

Netlify hosts static HTML files for free and handles SSL automatically.

  Step 4A.1 — Create account
    Go to netlify.com → Sign Up (use email or GitHub)

  Step 4A.2 — Deploy your files
    Option 1: Drag & Drop (easiest)
      a. Log into Netlify dashboard
      b. Click "Add new site" → "Deploy manually"
      c. Drag your entire dave-patton/ folder onto the upload area
      d. Netlify gives you a random URL like https://quirky-name-123.netlify.app
      e. Site is live instantly

    Option 2: GitHub (best for long-term)
      a. Create a free GitHub account at github.com
      b. Create a new repository called "dave-patton-site"
      c. Upload your dave-patton/ folder to the repo
      d. In Netlify: "Add new site" → "Import from Git"
      e. Connect GitHub, select your repo
      f. Build command: leave blank
      g. Publish directory: / (or pages/ if your index.html is there)
      h. Deploy

  Step 4A.3 — Make llms.txt, robots.txt, sitemap.xml accessible at root
    Your folder structure should be:
      /index.html      (from pages/index.html — RENAME/MOVE this)
      /llms.txt
      /robots.txt
      /sitemap.xml
      /images/         (your images folder)
      /schema/         (optional — keep schema files for reference)

    IMPORTANT: Move pages/index.html → index.html (root of folder).
    Netlify serves whatever is at the root.

  Step 4A.4 — Verify it works
    Visit your .netlify.app URL
    Check: https://your-site.netlify.app/llms.txt — should show text
    Check: https://your-site.netlify.app/robots.txt — should show text
    Check: https://your-site.netlify.app/sitemap.xml — should show XML

---

## STEP 4B — DEPLOY VIA WORDPRESS (TRACK B — CMS) (2-3 hours)

Use this if Dave wants to update content himself.

  Step 4B.1 — Get hosting
    Recommended: SiteGround (siteground.com) or WP Engine (wpengine.com)
    Plan: Start with the cheapest shared hosting plan ($10-15/mo)
    During signup: select "Start a new website" → WordPress

  Step 4B.2 — Install WordPress
    SiteGround auto-installs WordPress during signup.
    You'll get an admin URL: https://yourdomain.com/wp-admin
    Log in with the credentials they email you.

  Step 4B.3 — Install a lightweight theme
    In WP Admin → Appearance → Themes → Add New
    Search: "GeneratePress" or "Kadence" (both free, fast, SEO-friendly)
    Install & Activate

  Step 4B.4 — Install these plugins (required for backend to work)
    WP Admin → Plugins → Add New → search and install each:

      SEOPress or Yoast SEO    — handles meta tags, sitemap, robots.txt
                                  (enter Dave's info in the setup wizard)
      WP Schema Pro            — for injecting the JSON-LD schema files
                                  (or paste script blocks from person.jsonld
                                  manually into theme header)
      Smush or Imagify         — image compression for speed
      Wordfence                — basic security
      UpdraftPlus              — backups

  Step 4B.5 — Inject the schema
    Option A (plugin): In WP Schema Pro → add Person schema, fill in fields
    Option B (manual): 
      Go to Appearance → Theme Editor → header.php
      OR install "Headers and Footers" plugin
      Paste the contents of schema/person.jsonld inside a
      <script type="application/ld+json"> block just before </head>
      Do the same for faq.jsonld and breadcrumbs.jsonld on relevant pages

  Step 4B.6 — Build pages
    WP Admin → Pages → Add New for each:
      Home, About, Services, Senior Transitions, Communities,
      Home Report, Contact
    Copy the placeholder text from index.html sections into each page
    Meta tags: handled by SEOPress/Yoast — fill in from meta/meta-bank.html

  Step 4B.7 — Add contact form
    Install: WPForms Lite (free)
    Create a simple form: Name, Phone, Email, Message
    Embed in Contact page with shortcode

  Step 4B.8 — Upload llms.txt and robots.txt
    llms.txt: upload via FTP (FileZilla, free) or SiteGround File Manager
    Place at public_html/llms.txt
    robots.txt: SEOPress/Yoast generates this automatically — edit via the plugin

---

## STEP 5 — CONNECT YOUR DOMAIN (20 min)

After deploying (either track), point your domain to your host.

  TRACK A — Netlify:
    1. In Netlify dashboard → Domain management → Add custom domain
    2. Type in your domain (e.g. davepattonrealty.com)
    3. Netlify gives you nameservers OR DNS records
       Choice A (easiest): Update nameservers at your registrar to Netlify's
       Choice B: Add DNS records at your registrar pointing to Netlify

    To update nameservers at Namecheap:
      a. Log in → Domain List → click Manage on your domain
      b. Nameservers → select "Custom DNS"
      c. Enter the nameservers Netlify provided (usually dns1.p08.nsone.net etc.)
      d. Save — DNS propagates in 5 min to 48 hours (usually under 1 hour)

    Netlify automatically provisions a free SSL certificate (https) once DNS
    propagates. You'll see "SSL/TLS certificate" turn green in the dashboard.

  TRACK B — SiteGround/WordPress:
    1. SiteGround gives you an IP address or nameservers in your account
    2. At your registrar → update nameservers to SiteGround's
    3. Same process as above — log into registrar, update nameservers
    4. SSL: in SiteGround cPanel → Security → SSL/TLS → enable for your domain

---

## STEP 6 — VERIFY EVERYTHING WORKS (30 min)

Once live, run through this checklist:

  Structure
  [ ] https://yourdomain.com loads (no errors)
  [ ] https://yourdomain.com/llms.txt shows the AI file
  [ ] https://yourdomain.com/robots.txt shows robots rules
  [ ] https://yourdomain.com/sitemap.xml shows the XML sitemap
  [ ] All nav links work (no 404s)
  [ ] Site loads over HTTPS (padlock icon in browser)

  Schema validation (do both)
  [ ] Go to https://validator.schema.org
      Paste your domain URL → Validate → check for errors (warnings are OK)
  [ ] Go to https://search.google.com/test/rich-results
      Paste your domain URL → Run test → confirm Person, FAQ detected

  Meta / Social
  [ ] Go to https://metatags.io → paste your URL → check OG preview looks right
  [ ] Share the URL in a text message → check social preview image appears

  Speed check
  [ ] Go to https://pagespeed.web.dev → paste your URL
      Target: 90+ on mobile. If under 80, images are too large (compress them)

---

## STEP 7 — SUBMIT TO GOOGLE (15 min)

  Step 7.1 — Create Google Search Console account
    Go to: search.google.com/search-console
    Sign in with a Google account (create one for Dave if needed)

  Step 7.2 — Add your property
    Click "Add property" → URL prefix → enter https://yourdomain.com
    Verify ownership:
      Easiest method: HTML tag → copy the meta tag → paste into index.html
      <head> section → redeploy → click Verify
      Alternative: upload the verification .html file to your root folder

  Step 7.3 — Submit sitemap
    In Search Console left sidebar → Sitemaps
    Enter: sitemap.xml → Submit
    Status should show "Success" within a few minutes

  Step 7.4 — Request indexing for key pages
    Left sidebar → URL Inspection
    Enter / → click "Request Indexing"
    Do this for each key page: /about/, /services/, /senior-transitions/

---

## STEP 8 — ONGOING MAINTENANCE (once it's live)

Monthly:
  - Publish new Home Report page at /home-report/YYYY-MM/
    (add Article schema to each — compounding SEO value over time)
  - Update sitemap.xml lastmod dates for any changed pages

Quarterly:
  - Check Google Search Console for crawl errors or manual actions
  - Run schema validator again after any structural changes
  - Check PageSpeed score — if it drops, usually a large image was added

As you build:
  - Collect 3-5 client testimonials → add Review schema to homepage
  - Add a community blog targeting searches like
    "downsizing Hoover AL" or "senior housing Birmingham"
  - Link from Zillow, Realtor.com, and LinkedIn profiles back to the site
    (sameAs backlinks are high-value for AI entity recognition)

---

## QUICK REFERENCE — KEY URLS

  Schema validator:        https://validator.schema.org
  Rich results test:       https://search.google.com/test/rich-results
  Meta preview:            https://metatags.io
  PageSpeed:               https://pagespeed.web.dev
  Search Console:          https://search.google.com/search-console
  Netlify:                 https://netlify.com
  SiteGround:              https://siteground.com
  Namecheap:               https://namecheap.com
  Canva (OG images):       https://canva.com
  favicon.io:              https://favicon.io

---

## TOTAL TIME ESTIMATE

  Fill placeholders + images:  30-60 min
  Domain registration:         15 min
  Netlify deploy (Track A):    30 min
  Connect domain + SSL:        20 min (+ up to 1 hour DNS propagation)
  Verify + Search Console:     30 min

  TOTAL: ~2.5-3 hours to fully live, indexed, and validated.
