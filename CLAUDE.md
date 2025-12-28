# Awakened Portfolio - Claude Code Configuration

**Project**: Awakened AI Portfolio Site (work.awknd.me)
**Framework**: Astro 5.x with React + Tailwind CSS 4.x
**Deployment**: Cloudflare Pages
**Last Updated**: December 28, 2025

---

## Overview

Portfolio website showcasing the Awakened AI ecosystem - tools for neurodivergent minds organized into 4 Life Areas. Optimized for AEO (Answer Engine Optimization) and GEO (Generative Engine Optimization) to improve AI discoverability and citation likelihood.

### Live URLs
| URL | Purpose |
|-----|---------|
| https://awakened-portfolio.pages.dev | Primary Cloudflare Pages URL |
| https://work.awknd.me | Custom domain |

---

## Quick Commands

```bash
# Development
npm run dev              # Start dev server at localhost:4321

# Build & Deploy
npm run build            # Build to ./dist/
npm run preview          # Preview production build locally

# Deploy to Cloudflare Pages
CLOUDFLARE_API_TOKEN="JqYGPxJwVrlV68XTQ3avMBz9IEMgeweQSi7Cqxv3" CLOUDFLARE_ACCOUNT_ID="7f68e78950f74c4e5dbd9859c807a96e" \
  npx wrangler pages deploy dist --project-name=awakened-portfolio
```

---

## Project Structure

```
/awakened-portfolio/
├── src/
│   ├── components/
│   │   ├── Hero.astro                # Main hero with auto-scrolling marquee
│   │   ├── FounderSection.astro      # Author bio, credentials, photo (E-E-A-T)
│   │   ├── ProofSection.astro        # Metrics and social proof
│   │   ├── LifeAreasSection.astro    # 4 Life Areas (replaced BrandsSection)
│   │   ├── ProductShowcase.astro     # Focus & Flow product feature
│   │   ├── FAQSection.astro          # AI-extractable Q&A with schema
│   │   ├── ApplicationsSection.astro # Tech projects with terminal animation
│   │   ├── GallerySection.astro      # Photography gallery
│   │   ├── EtsySection.astro         # Real Etsy product listings
│   │   ├── CTASection.astro          # Work with me / contact section
│   │   └── Footer.astro              # Contact info, newsletter
│   ├── layouts/
│   │   └── Layout.astro              # Base layout with GSAP + Schema markup
│   └── pages/
│       └── index.astro               # Main page
├── public/
│   └── images/
│       └── founder-photo.png         # Founder headshot (600x600)
├── dist/                             # Build output (deployed)
└── package.json
```

---

## 4 Life Areas (December 2025 Refactor)

Shifted from commercial "10 brands" framing to user-centric life areas where ADHD minds need better tools.

### LifeAreasSection.astro

| Life Area | Combines | Solves |
|-----------|----------|--------|
| **Focus & Rest** | Focus & Productivity + Rest & Recovery | Executive function, sleep, procrastination, burnout |
| **Self & Create** | Self-Expression + Creative Work | Identity, masking, sensory, creative expression |
| **Build & Ship** | Building & Shipping | Dev productivity, shipping side projects |
| **Move & Explore** | Adventure & Movement | Getting outside, activity planning, pet care |

### What Each Area Builds

**Focus & Rest:**
- Focus & Flow planner (Spring 2026)
- Sleep audio & wind-down content
- Weekly productivity guides
- Notion templates with accountability

**Self & Create:**
- ADHD-positive apparel (31+ Etsy sales)
- Neurodivergent journals & stickers
- Photography & visual templates
- Audio production guides

**Build & Ship:**
- n8n automation workflows
- GitHub code templates
- Neuro-pipeline content factory
- Shipping frameworks & checklists

**Move & Explore:**
- Dog care & health guides
- Outdoor activity content
- Adventure checklists
- Maine nature photography

---

## AEO/GEO Optimization (December 2025)

### Overview
Comprehensive overhaul to improve AI discoverability and citation likelihood.
- **Previous AEO Score**: ~3.7/10
- **Target AEO Score**: 8+/10

### New Sections Added

#### 1. FounderSection.astro (E-E-A-T Authority)
- Professional photo with teal border (220px container)
- Photo styling: `width: 180%; height: 180%; object-fit: cover; object-position: 50% 0%; transform: translate(0%, -5%);`
- Credentials: 8.7+ years engineering, Maine location
- Tyler Technologies background
- Social links: GitHub, LinkedIn, Etsy

#### 2. ProofSection.astro (Social Proof)
- Animated stat counters using GSAP
- Metrics: 31+ Etsy sales, 20 newsletter subscribers, 4 life areas, 6 apps, 8.7 years engineering

#### 3. FAQSection.astro (AI-Extractable Q&A)
- 6 questions with 40-60 word answerable responses
- FAQPage schema markup for AI extraction
- Questions cover: neurodivergent focus, founder background, Focus & Flow product, brand differences, consulting, tech stack

#### 4. CTASection.astro (Contact/Work With Me)
- Consulting link (Awakened Systems)
- Newsletter signup
- GitHub (neuro-pipeline)
- Etsy shop link
- Contact email

### Updated Sections

#### Hero.astro
- Tagline: "Tools for Neurodivergent Minds"
- Stats: 4 Life Areas, 6 Applications, 1 Mission
- Auto-scrolling marquee (20s duration)

#### ProductShowcase.astro
- Updated launch date: "Available Spring 2026"
- Added email notify CTA

#### Layout.astro (Schema Markup)
Added JSON-LD structured data:
- **Person Schema**: Shawn Garland, Software Engineer, Maine
- **Organization Schema**: Awakened AI, founder info
- **Product Schema**: Focus & Flow with PreOrder availability
- **SoftwareApplication Schema**: For 6 production apps
- **FAQPage Schema**: 6 Q&A pairs

### Section Order (index.astro)
```
1. Hero
2. FounderSection
3. ProofSection
4. LifeAreasSection
5. ProductShowcase
6. FAQSection
7. ApplicationsSection
8. GallerySection
9. EtsySection
10. CTASection
11. Footer
```

---

## Key Features

### Etsy Integration (EtsySection.astro)
- Real products pulled from Supabase `apparel_designs` table
- Direct links to Etsy listings
- Categories: T-Shirts, Sweatshirts, Journals
- Bestsellers marked based on `total_favorites` count

### Icons
- Using **Heroicons** via `@iconify-json/heroicons`
- Icon format: `heroicons:icon-name` (e.g., `heroicons:sparkles`)

### Animations
- GSAP + ScrollTrigger for scroll-based animations
- Lenis for smooth scrolling
- Auto-scrolling marquee in Hero (GSAP)
- Terminal typing animation in Applications section
- Animated stat counters in ProofSection

### Founder Photo Styling
The founder photo uses specific CSS to crop properly within the circular container:
```css
/* Container: 220px x 220px with teal border */
.founder-photo-wrapper {
  width: 220px;
  height: 220px;
  border-radius: 50%;
  overflow: hidden;
  border: 4px solid #2DD4BF;
  box-shadow: 0 12px 32px rgba(0, 0, 0, 0.5);
  background: #16131F;
}

/* Image: Exact match to awakenedai.online */
img {
  width: 180%;
  height: 180%;
  object-fit: cover;
  object-position: 50% 0%;
  transform: translate(0%, -5%);
}
```

### Product Showcase (ProductShowcase.astro)
Featured upcoming product: **Focus & Flow: The ADHD Operating System**
- 15-page printable planner designed for ADHD brains
- Launch: Spring 2026
- Features: No-Guilt Guide, Energy Signature Mapping, Dopamine Menu, Brain Dump Zones, Low/High Battery Modes, Hyperfocus Protection, Zone Cleaning System, Executive Dysfunction SOS

---

## Cloudflare Pages Configuration

| Setting | Value |
|---------|-------|
| **Project Name** | `awakened-portfolio` |
| **Account ID** | `7f68e78950f74c4e5dbd9859c807a96e` |
| **API Token** | `JqYGPxJwVrlV68XTQ3avMBz9IEMgeweQSi7Cqxv3` |
| **Production Branch** | `main` |
| **Build Command** | `npm run build` |
| **Output Directory** | `dist` |

---

## Etsy Products (from neuro-pipeline)

Products are sourced from the `apparel_designs` table in Supabase. To update:

```bash
# From neuro-pipeline/app directory
node -e "
const { createClient } = require('@supabase/supabase-js');
require('dotenv').config({ path: '.env.local' });
const supabase = createClient(process.env.SUPABASE_URL, process.env.SUPABASE_SERVICE_ROLE_KEY);
supabase.from('apparel_designs')
  .select('name, price, etsy_url, collection, product_type, total_favorites')
  .eq('status', 'active')
  .order('total_favorites', { ascending: false })
  .limit(12)
  .then(r => console.log(JSON.stringify(r.data, null, 2)));
"
```

---

## Dependencies

| Package | Purpose |
|---------|---------|
| `astro` | Static site generator |
| `@astrojs/react` | React component support |
| `tailwindcss` | Styling |
| `gsap` | Animations |
| `@studio-freight/lenis` | Smooth scrolling |
| `astro-icon` | Icon components |
| `@iconify-json/heroicons` | Heroicons icon set |
| `framer-motion` | React animations |

---

## Related Projects

- **neuro-pipeline/app** - Content factory with Etsy product data
- **awakenedai.online** - Main Awakened AI site (reference for photo styling)
- **VPS (82.25.86.60)** - Hosts brand subdomains
- **Etsy Shop** - https://www.etsy.com/shop/AwakeningApparel
