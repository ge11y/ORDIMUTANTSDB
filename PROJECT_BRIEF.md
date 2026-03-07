# OrdiMutants Site — Project Brief

**Last Updated:** March 7, 2026  
**Status:** Pre-development / Planning Phase

---

## Vision

Build a community site and explorer for the OrdiMutants ordinal collection on Bitcoin — a place where collectors can browse the collection, track mutants, view rare satributes and traits, and discover featured highlights.

The site should feel like an **ancient archive or registry** rather than a modern NFT website.

The goal is to create a timeless, historic, and immersive experience that reflects the spirit of the OrdiMutants collection.

---

## Design Direction

### Aesthetic Philosophy

The site should feel:
- **Ancient** — like a historic registry or manuscript
- **Rustic** — weathered, carved, textured
- **Nordic/Viking inspired** — runic motifs, stone, iron
- **Archival** — focused, organized, timeless

**Avoid:**
- Neon colors
- Cyberpunk aesthetics
- Glossy startup design
- Generic NFT marketplace look

### Visual Elements

**Materials and palette:**
- Dark wood textures
- Stone and iron accents
- Parchment colored panels
- Muted gold highlights
- Weathered textures
- Runic divider elements

**Typography and branding:**
Use the OrdiMutants banner and logo assets in the repository as the visual reference for typography, branding, and overall design mood.

**Balance:**
Use runic motifs and nordic inspiration sparingly as accents, dividers, and headings, while keeping the UI readable and modern.

---

## Core Product Goals

The site should allow users to:

- Browse the entire OrdiMutants collection
- Search by mutant number, inscription id, and relevant metadata
- Filter by traits and satributes
- View the slug associated with each mutant
- View rare sat badges
- Create accounts without wallet login
- Track mutants using collector statuses (favorite, watching, owned, wishlist)
- Explore featured and notable mutants
- Later: use advanced collector tools and social signals

---

## V1 Features

### Public Experience
- **Homepage** with featured mutant highlight
- **Gallery** of all OrdiMutants with search and filters
- **Search** by name, inscription ID, or mutant number
- **Trait filters** (Background, Skin, Clothes, etc.)
- **Satribute filters** (Nakamoto, Pizza, Vintage, etc.)
- **Mutant detail page** showing traits, satributes, slug viewer, and tracking options
- **Rare sat badges** visually displayed on mutant pages
- **Slug viewer integration** for each mutant
- **Weekly Featured Mutant** section on homepage
- **Hall of Featured** archive page for past featured mutants

### User Accounts
- Sign up and log in **without wallet authentication** (email/password)
- Simple, accessible authentication flow

### Tracking System
Users can mark mutants with the following statuses:
- **Favorite** — mutants they love
- **Watching** — mutants they're interested in
- **Owned** — mutants they currently own
- **Wishlist** — mutants they want to acquire

### User Dashboard
- Personal dashboard with tracked mutants grouped by status
- Quick access to favorites, watching, owned, and wishlist

### Collector Signals
Mutant detail pages should show visible collector interest/activity metrics:
- Number of collectors watching
- Number of collectors who favorited
- Number marked as owned
- Number on wishlists

**Example:**
> "12 collectors watching this mutant"

---

## Planned Later Features

### Collector Intelligence
- **Trait + Satribute Hunter** — advanced search for specific combinations
- **Saved searches** — bookmark complex filters
- **Trending Mutants** — most watched/favorited recently
- **Optional public collector profiles** — showcase collections
- **Archive Ledger** — activity/history page for collection events

### Market Data
- Listing links (Magic Eden, etc.)
- Floor data
- Marketplace integrations
- Recent sale information

### Media / Community Tools
- **Pose gallery** — showcase mutant artwork
- **Mutant share cards** — generate social media graphics
- **GM post generator** — community engagement tools
- **Image generation or pose tools** — creative utilities

---

## Technical Direction

### Recommended Stack
- **Next.js 13+** (App Router)
- **Supabase** (database, auth)
- **Vercel** (hosting, deployment)

### Data Strategy

#### File-based collection data
Use repository files for static collection data:
- Mutant metadata (JSON dataset)
- CSV collection data
- Satributes data
- Slug viewer source files
- Visual assets (badges, textures, branding)
- Banner and logo assets

#### Database-backed app data
Use Supabase for dynamic user/app data:
- Users and authentication
- Tracking statuses (favorite, watching, owned, wishlist)
- Collector signals (aggregated counts)
- Featured mutant schedule/history
- Future: saved searches
- Future: public profiles

---

## Site Structure

### Public Pages
- **Home** — featured mutant, search, navigation
- **Gallery** — browse all OrdiMutants
- **Mutant Detail Page** — individual mutant view with traits, satributes, slug viewer, tracking
- **Trait Explorer** — find mutants by trait combinations
- **Hall of Featured** — archive of weekly featured mutants
- **Login / Sign Up** — authentication pages

### User Pages (authenticated)
- **Dashboard** — overview of tracked mutants
- **Favorites** — favorited mutants
- **Watching** — mutants being watched
- **Owned** — mutants marked as owned
- **Wishlist** — mutants on wishlist
- **Profile** — user settings and preferences

### Future Pages
- **Trending Mutants** — most popular recently
- **Collector Profile** — public user profiles
- **Archive Ledger** — collection history
- **Market Explorer** — marketplace data
- **Pose Gallery** — community artwork

---

## Build Priorities

### Phase 1: Planning & Inspection
- ✅ Analyze repository structure
- ✅ Review datasets and assets
- ✅ Consolidate planning documents
- ✅ Establish technical direction

### Phase 2: Architecture
- Create database schema (Supabase tables)
- Plan Next.js route structure
- Map out component hierarchy
- Design data flow (file-based + DB-backed)

### Phase 3: Scaffold
- Initialize Next.js 13+ project
- Configure Supabase client
- Set up Vercel deployment
- Import mutants.json dataset
- Create TypeScript types from data schema

### Phase 4: Implement V1 Core Features
- **Gallery:**
  - Display all mutants
  - Search functionality
  - Trait and satribute filters
- **Mutant pages:**
  - Detail view with all metadata
  - Badge rendering
  - Slug viewer integration
- **Auth:**
  - Sign up / login flow
  - Session management
- **Tracking system:**
  - Mark mutants (favorite, watching, owned, wishlist)
  - Update collector signals
- **Dashboard:**
  - User overview
  - Tracked mutants by status
- **Featured mutant system:**
  - Homepage featured section
  - Hall of Featured archive page
  - Weekly rotation logic

### Phase 5: Implement Later Features
- Collector intelligence tools
- Market data integrations
- Community/media tools

---

## Data Schema Reference

### Mutant Object Structure

```json
{
  "inscription_id": "02a19275c279b61423ba50933ea2778110d3959806f0f85259a6e96eea0a7b21i0",
  "inscription_number": 76393049,
  "sat_number": 45536076390,
  "name": "ORDIMUTANT OG#0",
  "attributes": [
    { "trait_type": "Background", "value": "Orange" },
    { "trait_type": "Skin", "value": "Diamond" },
    { "trait_type": "Clothes", "value": "Bitcoin Vest" },
    { "trait_type": "Mouth", "value": "Slavering" },
    { "trait_type": "Eyes", "value": "Blue Aviators" },
    { "trait_type": "Hat", "value": "Fitted Cap" },
    { "trait_type": "Earring", "value": "Silver Hoop" },
    { "trait_type": "DNA", "value": "OG" }
  ],
  "satributes": [
    "Block 9",
    "Common",
    "First Transaction",
    "Nakamoto",
    "Vintage"
  ],
  "rank": 75,
  "status": "legendary"
}
```

### TypeScript Interface

```typescript
interface Mutant {
  inscription_id: string;
  inscription_number: number;
  sat_number: number;
  name: string;
  attributes: Array<{
    trait_type: string;
    value: string;
  }>;
  satributes: string[];
  rank: number;
  status: 'common' | 'uncommon' | 'rare' | 'epic' | 'legendary' | 'mythic';
}
```

### Trait Types
- Background
- Skin
- Clothes
- Mouth
- Eyes
- Hat
- Earring
- DNA

### Satributes (Badge-Worthy)
- Block 9, Block 78, Block 286, Block 666
- Common, Uncommon, Black Uncommon
- First Transaction
- Nakamoto
- Pizza
- Silk Road
- Vintage
- Alpha, Omega
- JPEG
- Palindrome, Palin Block, Pali Block Palindrome
- Hitman

### Rarity Status Values
- `common` — most common
- `uncommon` — slightly rare
- `rare` — rare
- `epic` — very rare
- `legendary` — extremely rare
- `mythic` — rarest of all

---

## Assets Overview

### Collection Data
- **2,226 mutants** in JSON format
- Complete metadata with traits, satributes, rank, and rarity status

### Visual Assets
- **Banner:** ORDIMUTANTS_BANNER.jpeg (55KB)
- **Logo:** ORDIMUTANTS_O.jpg (14KB)
- **Badges:** 17 satribute badge images (JPG)
  - Special numbers: 9, 78, 286, 666
  - Historic: Nakamoto, Pizza, Silk Road, Vintage, First TX, Alpha, Omega
  - Rarity: Uncommon, Black Uncommon
  - Technical: JPEG, Palin Block, Pali Block Palindrome
  - Special: Hitman

### Reference Prototype
- **search-viewer-prototype.html** — working single-page demo with search, autocomplete, badge rendering, and status chips

---

## Notes

- **No wallet login required** — authentication via email/password for accessibility
- **Collector-focused** — emphasis on tracking, discovery, and community
- **Timeless aesthetic** — avoid trends, aim for lasting design
- **File + DB hybrid** — static collection data in files, dynamic user data in database

---

**End of Brief**
