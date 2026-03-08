# Gallery Implementation Documentation

**Date:** March 7, 2026  
**File:** `gallery.html`

---

## Data Sources

### Mutant Images

**Source:** `https://ordinals.com/content/{inscription_id}`

Each mutant card loads its image using the `inscription_id` field from the mutant dataset. This is the canonical on-chain image stored on Bitcoin via Ordinals.

**Example:**
```javascript
inscription_id: "02a19275c279b61423ba50933ea2778110d3959806f0f85259a6e96eea0a7b21i0"
→ Image URL: https://ordinals.com/content/02a19275c279b61423ba50933ea2778110d3959806f0f85259a6e96eea0a7b21i0
```

**Fallback:** If the image fails to load, a placeholder message is displayed with the first 8 characters of the inscription ID.

---

## Badge Mapping

Each satribute in the `mutant.satributes` array is mapped to a specific badge image file in `assets/badges/`.

### Complete Badge Mapping Table

| Satribute Name | Badge Filename | Path |
|----------------|----------------|------|
| Block 9 | `9.JPG` | `assets/badges/9.JPG` |
| Block 78 | `78.JPG` | `assets/badges/78.JPG` |
| Block 286 | `286.JPG` | `assets/badges/286.JPG` |
| Block 666 | `666.JPG` | `assets/badges/666.JPG` |
| Common | *(no badge)* | — |
| Uncommon | `UNCOMMON.JPG` | `assets/badges/UNCOMMON.JPG` |
| Black Uncommon | `BLACKUNCOMMON.JPG` | `assets/badges/BLACKUNCOMMON.JPG` |
| First Transaction | `FIRSTTX.JPG` | `assets/badges/FIRSTTX.JPG` |
| Nakamoto | `NAKAMOTO.JPG` | `assets/badges/NAKAMOTO.JPG` |
| Pizza | `PIZZA.JPG` | `assets/badges/PIZZA.JPG` |
| Silk Road | `SILKROAD.JPG` | `assets/badges/SILKROAD.JPG` |
| Vintage | `VINTAGE.JPG` | `assets/badges/VINTAGE.JPG` |
| Alpha | `ALPHA.JPG` | `assets/badges/ALPHA.JPG` |
| Omega | `OMEGA.JPG` | `assets/badges/OMEGA.JPG` |
| JPEG | `JPEG.JPG` | `assets/badges/JPEG.JPG` |
| Palindrome | *(no badge)* | — |
| Palin Block | `PALINBLOCK.JPG` | `assets/badges/PALINBLOCK.JPG` |
| Pali Block Palindrome | `PALIBLOCKPALINDROME.JPG` | `assets/badges/PALIBLOCKPALINDROME.JPG` |
| Hitman | `HITMAN.JPG` | `assets/badges/HITMAN.JPG` |

### Badge Mapping Code

```javascript
const BADGE_MAP = {
  'Block 9': '9.JPG',
  'Block 78': '78.JPG',
  'Block 286': '286.JPG',
  'Block 666': '666.JPG',
  'Common': null, // Common doesn't get a badge
  'Uncommon': 'UNCOMMON.JPG',
  'Black Uncommon': 'BLACKUNCOMMON.JPG',
  'First Transaction': 'FIRSTTX.JPG',
  'Nakamoto': 'NAKAMOTO.JPG',
  'Pizza': 'PIZZA.JPG',
  'Silk Road': 'SILKROAD.JPG',
  'Vintage': 'VINTAGE.JPG',
  'Alpha': 'ALPHA.JPG',
  'Omega': 'OMEGA.JPG',
  'JPEG': 'JPEG.JPG',
  'Palindrome': null, // Not in badge assets
  'Palin Block': 'PALINBLOCK.JPG',
  'Pali Block Palindrome': 'PALIBLOCKPALINDROME.JPG',
  'Hitman': 'HITMAN.JPG'
};
```

**Note:** "Common" and "Palindrome" satributes do not have corresponding badge images and are filtered out during rendering.

---

## Visual Design Implementation

### Design Direction: Rustic / Ancient / Mythic

The gallery implements the visual identity specified in `PROJECT_BRIEF.md`:

#### Color Palette
- **Background:** Deep black (`#0a0a0a`) with weathered texture overlay
- **Primary text:** Parchment (`#d4c5a9`)
- **Accent:** Muted gold (`#d4a574`, `#b8860b`)
- **Borders:** Bronze/copper tones (`rgba(139, 90, 43, ...)`)
- **Secondary text:** Weathered brown (`#8b7355`, `#6a5545`)

#### Typography
- **Headers:** `Cinzel` (serif) — ancient, carved aesthetic
- **Body:** `Lato` (sans-serif) — readable, modern balance
- **Uppercase + letter-spacing** for archival/registry feel

#### Visual Elements
1. **Weathered texture overlay** — repeating line pattern + radial gradients
2. **Subtle accent lines** — horizontal gold gradients as dividers
3. **Dark wood/stone backgrounds** — gradient layers in card backgrounds
4. **Bronze/iron borders** — muted metallic tones
5. **Soft shadows** — atmospheric depth without harsh edges

#### Card Design
- Dark gradient background (wood/stone feel)
- Bronze borders with glow on hover
- Gold accent line appears on top edge on hover
- Rank badge: dark background with gold border (runic style)
- Badge grid: small icons with bronze borders
- Tooltip on hover: shows full satribute name

---

## Mutant Identity Presentation

Each mutant card clearly displays:

1. **Mutant Number** (e.g., "Mutant #7")
   - Small, uppercase, serif font
   - Positioned above the name
   - Color: `#8b7355`

2. **Mutant Name** (e.g., "ORDIMUTANT OG#7")
   - Large, prominent serif heading
   - Color: `#d4a574` (muted gold)
   - 18px font size

3. **Rank Badge**
   - Overlaid on top-right of image
   - Dark background with gold border
   - Format: "Rank #75"

4. **Rarity Status**
   - Colored badge below name
   - Color-coded by rarity tier:
     - Common: Gray
     - Uncommon: Green
     - Rare: Blue
     - Epic: Purple
     - Legendary: Gold
     - Mythic: Gradient (pink/gold)

5. **Rare Satributes Section**
   - Only shows satributes that have badge images
   - Grid of 32×32px badge icons
   - Hover to see full satribute name
   - Bronze borders with glow effect on hover

---

## Search Functionality

Users can search by:
- **Mutant number** (e.g., "7" finds mutant #7)
- **Name** (e.g., "OG" finds all OG mutants)
- **Inscription ID** (full or partial)
- **Inscription number**

Search is case-insensitive and filters in real-time as the user types.

---

## Performance Considerations

- **Initial load:** Displays first 50 mutants for fast rendering
- **Search results:** Shows all matching mutants
- **Image loading:** Lazy browser-native loading
- **Fallback handling:** Graceful error handling for missing images

---

## File Structure

```
/Users/goobbotv3/Documents/ORDIMUTANTSDB/
├── gallery.html               ← Main gallery file
├── data/
│   └── mutants.json          ← 2,226 mutant records (loaded via fetch)
└── assets/
    └── badges/               ← 17 badge image files (referenced by cards)
        ├── 9.JPG
        ├── NAKAMOTO.JPG
        ├── PIZZA.JPG
        └── ... (14 more)
```

---

## Browser Compatibility

- Modern browsers (Chrome, Firefox, Safari, Edge)
- Requires JavaScript enabled
- Uses Fetch API (no polyfill needed for modern browsers)
- CSS Grid and Flexbox for layout
- Google Fonts (Cinzel, Lato) loaded from CDN

---

## Future Enhancements

Potential improvements for V2:
- Pagination or infinite scroll for full collection
- Advanced filters (by trait, satribute, rarity)
- Mutant detail modal on click
- Trait breakdown visualization
- Collector tracking integration (favorites, watchlist)
- Link to ordinals.com for each mutant

---

**End of Documentation**
