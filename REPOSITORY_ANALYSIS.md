# OrdiMutants Repository Analysis & Refactor Plan

**Analyzed:** March 7, 2026  
**Repository:** /Users/goobbotv3/Documents/ORDIMUTANTSDB

---

## 🔍 Current Repository Structure

### Root Level (Workspace)
```
/Users/goobbotv3/Documents/ORDIMUTANTSDB/
├── AGENTS.md                    # OpenClaw agent operating manual
├── SOUL.md                      # Agent personality config
├── IDENTITY.md                  # Agent identity
├── USER.md                      # User profile
├── HEARTBEAT.md                 # Periodic tasks config
├── TOOLS.md                     # Local tool notes
├── .openclaw/                   # OpenClaw session data
└── [Project files below]
```

### Duplicate Structure Issue ⚠️
There's **duplication** between root and `ORDIMUTANTSDB/`:

**Root level:**
- `OrdiMutants_Search_Viewer_Autocomplete.html` (557KB)
- `ordimutants_merged_dataset_with_rank_status.json` (2MB)
- `planning-docs/`
- `BADGES/`
- `ORDIMUTANTS_BANNER.jpeg`
- `ORDIMUTANTS_O.jpg`

**ORDIMUTANTSDB/ subfolder:**
- Same files duplicated
- Has its own `.git/`

---

## 📊 Data Assets Analysis

### Primary Dataset
**File:** `ordimutants_merged_dataset_with_rank_status.json`  
**Size:** 2MB  
**Records:** 2,226 mutants  

**Schema:**
```json
{
  "inscription_id": "...",
  "inscription_number": 76393049,
  "sat_number": 45536076390,
  "name": "ORDIMUTANT OG#0",
  "attributes": [
    { "trait_type": "Background", "value": "Orange" },
    { "trait_type": "Skin", "value": "Diamond" },
    // ... more traits
  ],
  "satributes": ["Block 9", "Common", "First Transaction", ...],
  "rank": 75,
  "status": "legendary"
}
```

**Quality:** ✅ Clean, complete, ready to use  
**Action:** **KEEP** as primary data source

---

### Search Viewer HTML
**File:** `OrdiMutants_Search_Viewer_Autocomplete.html`  
**Size:** 545KB  
**Purpose:** Single-page search/viewer demo

**Features:**
- Search by name, inscription ID, number
- Autocomplete suggestions
- Trait display
- Satribute badges
- Rarity status chips
- Embedded JSON data

**Status:** Working prototype with good UX patterns  
**Action:** **REFERENCE** for feature extraction, then archive

---

### Badge Assets
**Location:** `BADGES/`  
**Count:** 17 badge images (JPG format)  

**Badges:**
- Special numbers: 9, 78, 286, 666
- Rarity: UNCOMMON, BLACKUNCOMMON
- Historic: NAKAMOTO, PIZZA, SILKROAD, VINTAGE, FIRSTTX, ALPHA, OMEGA
- Technical: JPEG, PALINBLOCK, PALIBLOCKPALINDROME
- Special: HITMAN

**Action:** **KEEP** — these are core visual assets

---

### Branding Assets
- `ORDIMUTANTS_BANNER.jpeg` (55KB) — Main banner with typography
- `ORDIMUTANTS_O.jpg` (14KB) — Logo

**Action:** **KEEP** — primary brand assets

---

## 📋 Planning Documents Analysis

### master-brief.md ⭐
**Quality:** Excellent, comprehensive  
**Contains:**
- Product overview & goals
- V1 feature spec
- Design direction (nordic/runic aesthetic)
- Technical stack recommendations (Next.js, Supabase, Vercel)
- Data strategy (file-based + DB-backed)
- Site structure
- Build phase plan

**Action:** **KEEP** — primary reference doc

### vision.md
**Quality:** Good high-level summary  
**Overlap:** ~80% redundant with master-brief.md  
**Action:** **MERGE** into master-brief or archive

### features.md
**Quality:** Good feature list  
**Overlap:** Already detailed in master-brief  
**Action:** **MERGE** or archive

### design-direction.md
**Quality:** Good mood/aesthetic guidance  
**Overlap:** Already in master-brief  
**Action:** **MERGE** or archive

### sitemap.md
**Quality:** Basic page list  
**Overlap:** Better version in master-brief  
**Action:** **MERGE** or archive

---

## 🎯 Recommended File Structure for Clean Site

```
ordimutants-site/
├── README.md                           # Project overview
├── PROJECT_BRIEF.md                    # Consolidated from planning docs
├── .git/                               # Version control
│
├── data/                               # Static collection data
│   ├── mutants.json                    # Main dataset (2226 records)
│   └── schema.md                       # Data structure docs
│
├── assets/                             # Visual assets
│   ├── branding/
│   │   ├── banner.jpeg                 # OrdiMutants banner
│   │   └── logo.jpg                    # O logo
│   └── badges/                         # Satribute badge images
│       ├── nakamoto.jpg
│       ├── pizza.jpg
│       └── ... (17 badges)
│
├── archive/                            # Reference prototypes
│   └── search-viewer-prototype.html    # Original demo
│
├── docs/                               # Development docs
│   ├── DESIGN_SYSTEM.md                # Nordic/runic aesthetic guide
│   ├── DATABASE_SCHEMA.md              # Supabase tables
│   └── API_ROUTES.md                   # Next.js API planning
│
└── app/                                # Next.js 13+ app directory
    ├── (public)/
    │   ├── page.tsx                    # Homepage
    │   ├── gallery/
    │   │   └── page.tsx                # Browse all mutants
    │   ├── mutant/
    │   │   └── [id]/
    │   │       └── page.tsx            # Mutant detail page
    │   ├── featured/
    │   │   └── page.tsx                # Hall of Featured archive
    │   └── explorer/
    │       └── page.tsx                # Trait/Satribute explorer
    │
    ├── (auth)/
    │   ├── login/
    │   │   └── page.tsx
    │   └── signup/
    │       └── page.tsx
    │
    ├── (user)/
    │   ├── dashboard/
    │   │   └── page.tsx                # User dashboard
    │   ├── favorites/
    │   │   └── page.tsx
    │   ├── watching/
    │   │   └── page.tsx
    │   ├── owned/
    │   │   └── page.tsx
    │   └── wishlist/
    │       └── page.tsx
    │
    ├── api/                            # API routes
    │   ├── mutants/
    │   ├── search/
    │   └── tracking/
    │
    ├── components/                     # React components
    │   ├── ui/                         # Base UI primitives
    │   ├── mutant/                     # Mutant-specific components
    │   └── layout/                     # Layout components
    │
    └── lib/                            # Utilities
        ├── supabase.ts                 # DB client
        ├── mutants.ts                  # Data utilities
        └── types.ts                    # TypeScript types
```

---

## 🧹 Refactor Actions

### 1. Consolidate Documentation
**Create:** `PROJECT_BRIEF.md`  
**Merge from:**
- master-brief.md (primary)
- vision.md (high-level context)
- features.md (feature list)
- design-direction.md (aesthetic notes)
- sitemap.md (page structure)

**Result:** Single source of truth

---

### 2. Organize Data Files
**Create:** `data/` directory  
**Move:**
- `ordimutants_merged_dataset_with_rank_status.json` → `data/mutants.json`

**Add:**
- `data/schema.md` — document the data structure

---

### 3. Organize Assets
**Create:** `assets/` directory structure  
**Move:**
- `ORDIMUTANTS_BANNER.jpeg` → `assets/branding/banner.jpeg`
- `ORDIMUTANTS_O.jpg` → `assets/branding/logo.jpg`
- `BADGES/*` → `assets/badges/` (rename to lowercase .jpg)

---

### 4. Archive Prototype
**Create:** `archive/` directory  
**Move:**
- `OrdiMutants_Search_Viewer_Autocomplete.html` → `archive/search-viewer-prototype.html`

**Purpose:** Reference for:
- Search UX patterns
- Autocomplete behavior
- Badge rendering
- Status chip styling

---

### 5. Remove Duplicates
**Problem:** Root and `ORDIMUTANTSDB/` contain duplicate files  
**Action:**
- Keep ONE version (probably root level since that's the active workspace)
- Delete `ORDIMUTANTSDB/` subfolder
- If `ORDIMUTANTSDB/.git` has different history, merge commits first

---

### 6. Separate Agent Files
**Problem:** Agent config files mixed with project files  
**Action:** Keep them separate (already at root level is fine)

**Agent files (stay at root):**
- AGENTS.md
- SOUL.md
- IDENTITY.md
- USER.md
- HEARTBEAT.md
- TOOLS.md
- .openclaw/

**Project files:** Move to organized structure above

---

## ✅ What to Keep

### Essential Files
- ✅ `ordimutants_merged_dataset_with_rank_status.json` — primary data
- ✅ `master-brief.md` — comprehensive spec
- ✅ All badge images (BADGES/)
- ✅ Banner and logo images
- ✅ `OrdiMutants_Search_Viewer_Autocomplete.html` — as reference

### Optional/Redundant
- ⚠️ `vision.md` — merge into master-brief
- ⚠️ `features.md` — merge into master-brief
- ⚠️ `design-direction.md` — merge into master-brief
- ⚠️ `sitemap.md` — merge into master-brief

---

## 🚀 Next Steps

### Immediate
1. **Consolidate planning docs** → `PROJECT_BRIEF.md`
2. **Create organized folder structure**
3. **Move files to new structure**
4. **Delete duplicates**
5. **Commit clean structure**

### Phase 1: Setup
1. Initialize Next.js 13+ project
2. Configure Supabase
3. Set up Vercel deployment
4. Import mutants.json
5. Create TypeScript types from data schema

### Phase 2: Core Pages
1. Homepage with featured mutant
2. Gallery with search and filters
3. Mutant detail page
4. Slug viewer integration

### Phase 3: Auth & Tracking
1. Supabase auth (email/password)
2. User tracking system (favorite, watching, owned, wishlist)
3. User dashboard
4. Collector signals on mutant pages

### Phase 4: Features
1. Hall of Featured archive
2. Trait explorer
3. Advanced search
4. Weekly featured mutant rotation

---

## 🎨 Design Implementation Notes

### Nordic/Runic Aesthetic
**From master-brief:**
- Dark wood textures
- Stone and iron accents
- Parchment colored panels
- Muted gold highlights (#facc15 used in prototype)
- Runic divider elements

**Avoid:**
- Neon colors
- Cyberpunk aesthetics
- Glossy startup design
- Generic NFT marketplace look

**Prototype insights:**
The existing HTML viewer uses a good dark gradient background with gold accents. This can be evolved into the full nordic theme.

---

## 📐 Data Schema Reference

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

**Traits:**
- Background
- Skin
- Clothes
- Mouth
- Eyes
- Hat
- Earring
- DNA

**Satributes:** (badge-worthy sat properties)
- Block 9, Block 78, etc.
- Common, Uncommon
- First Transaction
- Nakamoto
- Pizza
- Silk Road
- Vintage
- Alpha, Omega
- JPEG
- Palindrome variants
- Hitman

---

## 🎯 Summary

**Current state:** Mixed workspace with duplicates and scattered planning docs  
**Target state:** Clean, organized project ready for Next.js development  
**Key assets:** 2,226 mutant dataset, 17 badge images, comprehensive master-brief  
**Next action:** Consolidate, organize, then scaffold Next.js app

The repository has **excellent raw materials** — it just needs structural organization before development begins.
