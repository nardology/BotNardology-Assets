# BotNardology-Assets

Public image and audio assets for the KAI Discord bot, served via **jsDelivr CDN**.

**Base URL:**
```
https://cdn.jsdelivr.net/gh/nardology/BotNardology-Assets@main/assets/
```

---

## Folder Structure

```
assets/
├── style_images/          # Main character portraits (embeds, inventory)
│   └── {name}.png         # e.g. pirate.png, saas.png
│
├── emotions/              # Per-character emotion images
│   └── {character_id}/    # e.g. emotions/dog/
│       ├── affectionate.{ext}
│       ├── confused.{ext}
│       ├── excited.{ext}
│       ├── happy.{ext}
│       ├── mad.{ext}
│       ├── neutral.{ext}
│       └── sad.{ext}
│
├── bonds/                 # Per-character bond tier images
│   └── {character_id}/    # e.g. bonds/pirate/
│       ├── tier1.{ext}
│       ├── tier2.{ext}
│       ├── tier3.{ext}
│       ├── tier4.{ext}
│       └── tier5.{ext}
│
├── ui/                    # UI elements, animations, and sound effects
│   ├── box.gif            # Box opening animation
│   ├── common1.gif        # Spin animation — common rarity
│   ├── uncommon1.gif      # Spin animation — uncommon rarity
│   ├── rare1.gif          # Spin animation — rare rarity
│   ├── legendary1.gif     # Spin animation — legendary rarity
│   ├── mythic1.gif        # Spin animation — mythic rarity
│   ├── start.png          # KAI mascot onboarding image
│   ├── roll1.wav          # Spin sound (common/uncommon)
│   ├── roll2.wav          # Spin sound (rare/legendary/mythic)
│   ├── open1–5.wav        # Box open sounds (one per rarity tier)
│   └── reward1–5.wav      # Reward reveal sounds (one per rarity tier)
│
└── cosmetics/             # Profile cosmetic images
    ├── tails.png
    ├── strong.png
    ├── cow.png
    ├── tam.png
    ├── joe.png
    ├── sans.png
    └── walter.png
```

---

## Current Characters

| Character ID      | Style Image         | Emotions | Bonds |
|--------------------|---------------------|----------|-------|
| `pirate`           | pirate.png          | 7        | 5     |
| `robot`            | robot.png           | 7        | 5     |
| `nardology`        | saas.png            | 6*       | 5     |
| `peasant`          | peasant.png         | 7        | 5     |
| `dog`              | dog.png             | 7        | 5     |
| `cat`              | cat.png             | 7        | 5     |
| `common_man`       | commonman.png       | 7        | 5     |
| `knight`           | knight.png          | 7        | 5     |
| `samurai`          | samurai.png         | 7        | 5     |
| `millionaire_ceo`  | millionaire.png     | 7        | 5     |
| `dude`             | dude.png            | 7        | 5     |
| `billionaire_ceo`  | billionaire.png     | 7        | 5     |
| `dragon`           | dragon.png          | 7        | 5     |

\* `nardology` is missing `sad.png` — needs to be generated/uploaded.

---

## Supported Emotion Keys

Every character should have one image per emotion:

| Key             | Description                  |
|-----------------|------------------------------|
| `affectionate`  | Loving / warm expression     |
| `confused`      | Puzzled / uncertain          |
| `excited`       | Energetic / thrilled         |
| `happy`         | Smiling / content            |
| `mad`           | Angry / frustrated           |
| `neutral`       | Default / resting expression |
| `sad`           | Unhappy / sorrowful          |

More emotion keys may be added in the future. The structure is flat files inside the character folder, not hardcoded to exactly 7.

---

## Bond Tiers

Each character has 5 bond tier images representing relationship progression:

| Tier    | Meaning          |
|---------|------------------|
| `tier1` | Acquaintance     |
| `tier2` | Friendly         |
| `tier3` | Close friend     |
| `tier4` | Best friend      |
| `tier5` | Soulmate / max   |

---

## How to Add a New Character

1. **Choose a `character_id`** — lowercase, underscores for spaces (e.g., `captain_blackthorn`).

2. **Add the style image:**
   ```
   assets/style_images/{character_id}.png
   ```

3. **Add 7 emotion images:**
   ```
   assets/emotions/{character_id}/
   ├── affectionate.{ext}
   ├── confused.{ext}
   ├── excited.{ext}
   ├── happy.{ext}
   ├── mad.{ext}
   ├── neutral.{ext}
   └── sad.{ext}
   ```

4. **Add 5 bond tier images:**
   ```
   assets/bonds/{character_id}/
   ├── tier1.{ext}
   ├── tier2.{ext}
   ├── tier3.{ext}
   ├── tier4.{ext}
   └── tier5.{ext}
   ```

5. **Update `manifest.json`** — add the character ID to the `characters` array and all file paths to the `files` array.

6. **Commit and push.** jsDelivr will serve the new files immediately from the `@main` branch, or tag a release for stable caching.

---

## CDN URL Format

All files are accessible at:

```
https://cdn.jsdelivr.net/gh/nardology/BotNardology-Assets@main/{path}
```

**Examples:**
```
# Style portrait
https://cdn.jsdelivr.net/gh/nardology/BotNardology-Assets@main/assets/style_images/pirate.png

# Emotion image
https://cdn.jsdelivr.net/gh/nardology/BotNardology-Assets@main/assets/emotions/pirate/happy.jpg

# Bond tier image
https://cdn.jsdelivr.net/gh/nardology/BotNardology-Assets@main/assets/bonds/pirate/tier3.jpg

# UI element
https://cdn.jsdelivr.net/gh/nardology/BotNardology-Assets@main/assets/ui/box.gif
```

For pinned versions (recommended for production), use a tagged release:
```
https://cdn.jsdelivr.net/gh/nardology/BotNardology-Assets@v1.0/assets/...
```

---

## Image Guidelines

- **Preferred formats:** PNG or JPG for static images, GIF for animations only.
- **Existing formats are preserved** — the bot handles PNG, JPG, WEBP, AVIF, and GIF.
- **Do not convert** existing file formats unless there's a specific reason.
- **Keep the repo lightweight** — optimize images before committing.

---

## Legacy Files

The old flat filenames (e.g., `dogaffectionate.avif`, `piratebond1.gif`) still exist in `assets/ui/` for backward compatibility during the transition period. **Do not delete them** until the bot code is fully updated to reference the new organized paths.

---

## Future Plans

- `backgrounds/` — Scene background images
- `icons/` — UI icon assets
- Additional emotion keys beyond the core 7
- Shop-exclusive and seasonal character folders (e.g., `emotions/captain_blackthorn/`)
