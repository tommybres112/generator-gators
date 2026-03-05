# Generator Gators — Project Documentation

## Project Overview

**Generator Gators** is a lead generation and installer-matching website for whole-home standby generator installation in Long Island and New York City. The site connects homeowners with vetted local generator installation professionals.

**Important:** Generator Gators is a referral/matching service, NOT a direct installer. All messaging must reflect this.

---

## Tech Stack

| Technology | Purpose |
|-----------|---------|
| [Astro](https://astro.build) | Static site framework |
| [Tailwind CSS v4](https://tailwindcss.com) | Utility-first CSS (via `@tailwindcss/vite`) |
| [@astrojs/sitemap](https://docs.astro.build/en/guides/integrations-guide/sitemap/) | Auto-generated sitemap.xml |
| [Formspree](https://formspree.io) | Form handling (static-compatible) |

---

## Build Commands

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

**Output directory:** `dist/`
**Build command:** `npm run build`
**Deployment target:** Cloudflare Pages

---

## Project Structure

```
generator-gators/
├── public/
│   ├── favicon.svg          # Generator Gators favicon
│   ├── favicon.ico          # Legacy favicon
│   └── og-image.jpg         # Open Graph image (TODO: replace with real image)
├── src/
│   ├── layouts/
│   │   └── Layout.astro     # Base layout: SEO, OG tags, GA4 placeholder, schema
│   ├── components/
│   │   ├── Header.astro     # Sticky nav with mobile menu
│   │   ├── Footer.astro     # Footer with nav, service areas, disclaimer
│   │   ├── QuoteForm.astro  # Formspree lead capture form
│   │   ├── MascotSVG.astro  # Power Gator mascot SVG illustration
│   │   └── FAQSection.astro # Accordion FAQ component
│   ├── pages/
│   │   ├── index.astro                          # Homepage
│   │   ├── whole-home-generator-installation.astro
│   │   ├── generator-installation-cost.astro
│   │   ├── about.astro
│   │   ├── contact.astro
│   │   ├── thank-you.astro                      # Post-form submission
│   │   ├── privacy-policy.astro
│   │   ├── robots.txt.ts                        # robots.txt API route
│   │   └── locations/
│   │       ├── index.astro                      # Locations hub
│   │       ├── brooklyn-ny.astro
│   │       ├── queens-ny.astro
│   │       ├── nassau-county-ny.astro
│   │       └── suffolk-county-ny.astro
│   └── styles/
│       └── global.css       # Tailwind v4 imports + custom theme tokens
├── astro.config.mjs          # Astro config: site URL, sitemap, Tailwind vite plugin
├── package.json
└── CLAUDE.md                 # This file
```

---

## URLs & Pages

| Page | URL |
|------|-----|
| Homepage | `/` |
| Generator Installation | `/whole-home-generator-installation` |
| Cost Guide | `/generator-installation-cost` |
| Locations Hub | `/locations` |
| Brooklyn, NY | `/locations/brooklyn-ny` |
| Queens, NY | `/locations/queens-ny` |
| Nassau County | `/locations/nassau-county-ny` |
| Suffolk County | `/locations/suffolk-county-ny` |
| About | `/about` |
| Contact | `/contact` |
| Thank You | `/thank-you` |
| Privacy Policy | `/privacy-policy` |

---

## Key Configuration

### Site URL
Set in `astro.config.mjs`:
```js
site: 'https://www.generatorgators.com'
```
Update this when deploying to the real domain.

### Form Handling (Formspree)
In `src/components/QuoteForm.astro`:
```js
const FORMSPREE_ID = 'YOUR_FORMSPREE_FORM_ID';
```
1. Create a free account at [formspree.io](https://formspree.io)
2. Create a new form
3. Copy the form ID (e.g., `xpwzrevk`)
4. Replace `YOUR_FORMSPREE_FORM_ID` with your actual ID

The form redirects to `/thank-you` after successful submission via the `_next` hidden field.

### Phone Number
Placeholder throughout the site: **`555-555-5555`**
Search and replace with the real phone number before launch.

### Google Analytics (GA4)
Placeholder in `src/layouts/Layout.astro` (commented out):
```html
<!-- Google Analytics GA4 Placeholder -->
<!-- Replace GA_MEASUREMENT_ID with your actual Google Analytics 4 measurement ID -->
```
Uncomment and replace `GA_MEASUREMENT_ID` with your real GA4 measurement ID (e.g., `G-XXXXXXXXXX`).

### Email Address
Placeholder: `info@generatorgators.com`
Update in `src/pages/contact.astro` and `src/pages/privacy-policy.astro`.

---

## SEO Features

- **Unique title + meta description** on every page
- **Canonical URLs** via `canonicalUrl` prop in Layout
- **Open Graph tags** (og:title, og:description, og:image, og:url) on every page
- **JSON-LD schema markup** on homepage (LocalBusiness + Service), service pages, and location pages
- **Sitemap** auto-generated by `@astrojs/sitemap` at `/sitemap-index.xml`
- **robots.txt** served via API route at `/robots.txt`
- **Internal linking** between service pages and location pages

---

## Design System

### Color Palette
| Color | Tailwind Class | Hex | Use |
|-------|---------------|-----|-----|
| Deep Green | `green-800` | `#166534` | Primary brand, headers, CTAs |
| Medium Green | `green-700` | `#15803d` | Hover states |
| Light Green | `green-50` | `#f0fdf4` | Section backgrounds |
| Electric Yellow | `yellow-400` | `#facc15` | Accent, primary CTAs |
| Charcoal | `gray-900` | `#111827` | Text, footer |

### Typography
- **Font:** Inter (Google Fonts)
- **Headings:** `font-extrabold` or `font-bold`
- **Body:** `text-gray-600`, `leading-relaxed`

---

## Deployment (Cloudflare Pages)

1. Push to GitHub (`generator-gators` repository)
2. Connect repository to Cloudflare Pages
3. Set build settings:
   - **Build command:** `npm run build`
   - **Output directory:** `dist`
   - **Node.js version:** 18 or 20+
4. Deploy

---

## Pre-Launch Checklist

- [ ] Replace `555-555-5555` with real phone number
- [ ] Replace `YOUR_FORMSPREE_FORM_ID` with real Formspree ID
- [ ] Replace `info@generatorgators.com` with real email
- [ ] Add real `og-image.jpg` to `/public/` (1200×630px recommended)
- [ ] Set up Google Analytics and uncomment GA4 code in `Layout.astro`
- [ ] Update `site` in `astro.config.mjs` if using a different domain
- [ ] Verify sitemap at `/sitemap-index.xml` after deployment
- [ ] Submit sitemap to Google Search Console
- [ ] Test all form submissions
- [ ] Test mobile responsiveness
- [ ] Test all internal links

---

## Important Brand Guidelines

- **Never claim Generator Gators installs generators.** Always use language like:
  - "connects homeowners with vetted local installation partners"
  - "our matched installers"
  - "vetted local professionals in our network"
- **Tone:** Trustworthy, approachable, professional — like a premium home services brand
- **Mascot:** "Power Gator" — a friendly cartoon alligator in a hard hat holding a generator
