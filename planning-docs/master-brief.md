# OrdiMutants Site Master Brief

## Product Overview

Build a new OrdiMutants community site as an explorer, archive, and collector platform for the OrdiMutants ordinal collection on Bitcoin.

The site should not feel like a generic NFT website. It should feel like an ancient archive or registry with rustic, historic, nordic, and runic-inspired design language.

The OrdiMutants banner and logo assets in the repository should be used as the visual reference for typography, branding, and overall design mood.

## Core Product Goals

The site should allow users to:

- browse the entire OrdiMutants collection
- search by mutant number, inscription id, and relevant metadata
- filter by traits and satributes
- view the slug associated with each mutant
- view rare sat badges
- create accounts without wallet login
- track mutants using collector statuses
- explore featured and notable mutants
- later use advanced collector tools and social signals

## V1 Features

### Public Experience
- Homepage
- Gallery of all OrdiMutants
- Search
- Trait filters
- Satribute filters
- Mutant detail page
- Rare sat badges
- Slug viewer integration
- Weekly Featured Mutant section
- Hall of Featured archive page

### User Accounts
Users can sign up and log in without wallet authentication.

### Tracking System
Users can mark mutants as:
- Favorite
- Watching
- Owned
- Wishlist

### User Dashboard
Users should have a personal dashboard with tracked mutants grouped by status.

### Collector Signals
Mutant detail pages should show visible collector interest/activity metrics such as:
- number watching
- number favorited
- number marked owned
- number wishlisted

## Planned Later Features

### Collector Intelligence
- Trait + Satribute Hunter
- Saved searches
- Trending Mutants
- Optional public collector profiles
- Archive Ledger activity/history page

### Market Data
- listing links
- floor data
- marketplace integrations
- recent sale info

### Media / Community Tools
- pose gallery
- mutant share cards
- GM post generator
- image generation or pose tools

## Design Direction

The site should feel:
- ancient
- rustic
- weathered
- carved
- archival
- nordic / viking inspired
- runic in accent, but still readable

Avoid:
- neon
- cyberpunk
- glossy startup aesthetics
- generic NFT marketplace design

Suggested materials and palette:
- dark wood
- stone
- iron
- parchment
- muted gold
- weathered textures

Use runic motifs and nordic inspiration sparingly as accents, dividers, and headings, while keeping the UI readable and modern.

## Technical Direction

Recommended stack:
- Next.js
- Supabase
- Vercel

## Data Strategy

### File-based collection data
Use repository files for:
- mutant metadata
- CSV collection data
- satributes data
- slug viewer source files
- assets and textures
- banner and logo assets

### Database-backed app data
Use Supabase for:
- users
- auth
- tracking statuses
- collector signals
- featured mutant schedule/history
- future saved searches
- future public profiles

## Site Structure

### Public Pages
- Home
- Gallery
- Mutant Detail Page
- Trait Explorer
- Hall of Featured
- Login / Sign Up

### User Pages
- Dashboard
- Favorites
- Watching
- Owned
- Wishlist
- Profile

### Future Pages
- Trending Mutants
- Collector Profile
- Archive Ledger
- Market Explorer
- Pose Gallery

## Build Priorities

### Phase 1
Plan architecture and inspect datasets/assets.

### Phase 2
Create database schema, route plan, and component map.

### Phase 3
Scaffold the Next.js app and Supabase integration.

### Phase 4
Implement V1:
- gallery
- mutant pages
- slug viewer
- auth
- tracking system
- dashboard
- featured mutant system
- hall of featured

### Phase 5
Implement later collector and market features.