# Lunaris Content Repository

> Wallpaper images, collection data, and remote configuration for **Lunaris: Beyond the Screen**  
> Served via **GitHub Pages** to the Lunaris Android app.

---

## Repository Structure

```
lunaris-content/
│
├── data/
│   ├── collections.json       ← All collection metadata
│   ├── wallpapers.json        ← Full wallpaper catalogue
│   └── app_config.json        ← Announcements, featured, popular, force-update
│
├── images/
│   ├── wallpapers/
│   │   ├── demon-slayer/      ← ds-001.jpg, ds-002.jpg, ..., cover.jpg
│   │   ├── attack-on-titan/   ← aot-001.jpg, ..., cover.jpg
│   │   ├── jujutsu-kaisen/    ← jjk-001.jpg, ..., cover.jpg
│   │   ├── dragon-ball/       ← db-001.jpg, ..., cover.jpg
│   │   ├── dc/                ← dc-001.jpg, ..., cover.jpg
│   │   └── invincible/        ← inv-001.jpg, ..., cover.jpg
│   │
│   └── announcements/
│       ├── teasers/           ← Teaser poster images
│       └── whats-new/         ← What's New poster images
│
└── index.html                 ← GitHub Pages landing (not for browsing)
```

---

## Wallpaper Naming Convention

All wallpapers must follow this naming format:

```
{collection-prefix}-{zero-padded-number}.jpg
```

| Collection      | Prefix | Example      |
|-----------------|--------|--------------|
| Demon Slayer    | `ds`   | `ds-001.jpg` |
| Attack on Titan | `aot`  | `aot-001.jpg`|
| Jujutsu Kaisen  | `jjk`  | `jjk-001.jpg`|
| Dragon Ball     | `db`   | `db-001.jpg` |
| DC              | `dc`   | `dc-001.jpg` |
| Invincible      | `inv`  | `inv-001.jpg`|

Each collection folder must also contain a **`cover.jpg`** — the collection thumbnail shown in the app.

---

## Adding Wallpapers

1. Rename file to match the naming convention (e.g., `ds-049.jpg`)
2. Place in the correct collection folder under `images/wallpapers/`
3. Open `data/wallpapers.json`
4. Add a new entry with the correct `id`, `collectionId`, `title`, `imageUrl`, `tags`, etc.
5. Update `wallpaperCount` in `data/collections.json` for that collection
6. Update `lastUpdated` date in both JSON files
7. Commit & push — Lunaris fetches the update automatically, no app update needed

---

## Adding an Announcement

1. Open `data/app_config.json`
2. Under `announcement`:
   - Set `"enabled": true`
   - Set a **unique** `id` (e.g., `"ann-002"`) — a new ID triggers re-display
   - Set `type`: `GENERAL` | `UPDATE_TEASER` | `WHATS_NEW`
   - Set `imageUrl` (upload poster to `images/announcements/`)
   - Set `title`, `message`, version range, `ctaLabel`, `ctaUrl`
3. Commit & push

> Announcements display **once per day per ID**. A new ID shows immediately.

---

## GitHub Pages Setup

- Branch: `main`
- Source: root `/`
- URL: `https://xiiidimensions.github.io/lunaris-content/`

Ensure the repository is **public** so the app can fetch without authentication.

---

## Base URLs (reference)

```
Data:   https://xiiidimensions.github.io/lunaris-content/data/
Images: https://xiiidimensions.github.io/lunaris-content/images/wallpapers/
```
