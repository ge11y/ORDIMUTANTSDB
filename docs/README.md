# Documentation Directory

Technical documentation and development guides for the OrdiMutants site.

## Planned Documentation

### DATABASE_SCHEMA.md
Supabase table definitions, relationships, and indexes.

**Tables to define:**
- users (auth)
- mutant_tracking (user favorites, watching, owned, wishlist)
- featured_mutants (weekly featured schedule/history)
- collector_signals (aggregated interest metrics)

### API_ROUTES.md
Next.js API route planning and endpoint specifications.

**Endpoints to plan:**
- `/api/mutants` — search and filter
- `/api/mutants/[id]` — individual mutant data
- `/api/tracking` — add/remove tracking statuses
- `/api/featured` — get current/past featured mutants

### DESIGN_SYSTEM.md
Component library, color palette, typography, and nordic/runic aesthetic guidelines.

**Sections:**
- Color palette (dark wood, stone, muted gold)
- Typography (based on banner asset)
- Component primitives (buttons, cards, filters)
- Runic accent elements (dividers, headers)
- Badge rendering guidelines
- Rarity status chips

### DEPLOYMENT.md
Vercel deployment configuration and environment variables.

---

**Status:** Documentation will be created during Phase 2 (Architecture) and Phase 3 (Scaffold).
