# atoll Theme Model

This file documents the cross-repo theme strategy for the `atoll-cms` organization.

## Where themes live

- Core fallback theme: `atoll-core/themes/default`
- Official external themes:
  - `atoll-theme-skeleton`
  - `atoll-theme-business`
  - `atoll-theme-editorial`
  - `atoll-theme-portfolio`

## Why external repositories

- Clear separation between runtime and design assets
- Independent release cadence for themes
- Better collaboration with designers (theme-only repos)
- Real-world example package for community theme authors

## Runtime resolution order

1. `templates/` (site-level hard overrides)
2. `themes/<active>/templates/` (installed project theme)
3. `core/themes/<active>/templates/` (if core ships one)
4. `core/themes/default/templates/` (fallback)

Assets via `theme_asset('main.css')`:
1. `themes/<active>/assets/main.css`
2. `core/themes/<active>/assets/main.css`
3. `core/themes/default/assets/main.css`

## Registry + install

Theme registry is stored in each site at:
- `content/data/theme-registry.json`

Typical flow:

```bash
php bin/atoll theme:install:registry business
php bin/atoll theme:activate business
```

Presets can auto-install required themes before activation.
