# Awakened Portfolio - Claude Code Configuration

**Project**: Awakened AI Portfolio Site (work.awknd.me)
**Framework**: Astro 5.x with React + Tailwind CSS 4.x
**Deployment**: Cloudflare Pages
**Last Updated**: December 28, 2025

---

## Overview

Portfolio website showcasing the Awakened AI ecosystem - 10 brands focused on neurodivergent productivity, fashion, and content.

### Live URLs
| URL | Purpose |
|-----|---------|
| https://awakened-portfolio.pages.dev | Primary Cloudflare Pages URL |
| https://work.awknd.me | Custom domain (to be configured) |

---

## Quick Commands

```bash
# Development
npm run dev              # Start dev server at localhost:4321

# Build & Deploy
npm run build            # Build to ./dist/
npm run preview          # Preview production build locally

# Deploy to Cloudflare Pages
CLOUDFLARE_API_TOKEN="<token>" CLOUDFLARE_ACCOUNT_ID="7f68e78950f74c4e5dbd9859c807a96e" \
  npx wrangler pages deploy dist --project-name=awakened-portfolio
```

---

## Project Structure

```
/awakened-portfolio/
├── src/
│   ├── components/
│   │   ├── BrandsSection.astro    # 10-brand ecosystem showcase
│   │   ├── BrandCard.astro        # Individual brand card
│   │   ├── EtsySection.astro      # Real Etsy product listings
│   │   ├── HeroSection.astro      # Main hero with animations
│   │   └── ...
│   ├── layouts/
│   │   └── Layout.astro           # Base layout with GSAP
│   └── pages/
│       └── index.astro            # Main page
├── public/
│   └── images/                    # Static images
├── dist/                          # Build output (deployed)
└── package.json
```

---

## Key Features

### Brand Ecosystem (BrandsSection.astro)
- **Tier 1**: Awakened Insights, Awakened Systems, Awakening Apparel
- **Tier 2**: Awakened Visuals, Awakened Frameworks, Awakened Outdoors, Awakened Pack, Awakened Audio
- **Tier 3**: Awakened Publishing, Awakened Sleep

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
- Terminal typing animation in Applications section (typewriter effect with blinking cursor)

---

## Cloudflare Pages Configuration

| Setting | Value |
|---------|-------|
| **Project Name** | `awakened-portfolio` |
| **Account ID** | `7f68e78950f74c4e5dbd9859c807a96e` |
| **Production Branch** | `main` |
| **Build Command** | `npm run build` |
| **Output Directory** | `dist` |

### API Token Permissions
Create a custom token with:
- **Account** → **Cloudflare Pages** → **Edit**

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
- **VPS (82.25.86.60)** - Hosts brand subdomains
- **Etsy Shop** - https://www.etsy.com/shop/AwakeningApparel
