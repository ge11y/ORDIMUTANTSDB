# Data Directory

This directory contains the static collection data for OrdiMutants.

## Files

### mutants.json
**Source:** `ordimutants_merged_dataset_with_rank_status.json`  
**Records:** 2,226 mutants  
**Format:** JSON array

Complete OrdiMutants collection metadata including:
- Inscription ID and number
- Sat number
- Mutant name
- Attributes (traits)
- Satributes (rare sat properties)
- Rank
- Rarity status

### Schema

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

### Satributes
Special sat properties that earn badge display:
- Block numbers (9, 78, 286, 666)
- Rarity markers (Common, Uncommon, Black Uncommon)
- Historic (Nakamoto, Pizza, Silk Road, Vintage, First Transaction)
- Special (Alpha, Omega, JPEG, Palindrome variants, Hitman)

---

**Note:** This is static collection data. User-generated data (favorites, tracking, etc.) is stored in Supabase.
