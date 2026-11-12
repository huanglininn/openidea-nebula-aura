# Nebula Aura Theme for OpenIDEA

A data-only colour theme plugin for OpenIDEA. It adds five themes to
_Settings › Plugins_ and applies them as design-token overrides; it ships no
WebAssembly, asks for no capability and runs no code.

| Theme | `kind` | Character |
|---|---|---|
| Nebula Aura Dark | `dark` | Neutral cool-grey surfaces, blue-violet accent, muted syntax palette |
| Nebula Aura Violet | `dark` | The same structure with a violet-tinted accent and slightly warmer syntax |
| Nebula Aura Midnight | `dark` | Deepest blue-black base, teal-leaning accent, highest surface separation |
| Nebula Aura Light | `light` | Near-white layered surfaces, pale violet selection, neutral borders |
| Nebula Aura Sorbet Mint | `light` | Eye-comfort mint surfaces, Sorbet's teal keywords and plum types |

## What it themes

- **UI:** all 121 tokens of the OpenIDEA 0.1.39 UI theme file — surfaces,
  lines, text, states, gutters, search, VCS (including the diff stripe marks),
  status, terminal, shadows and the Islands contract.
- **Editor:** all 121 tokens of the editor colour scheme — syntax groups
  (including the Python and PHP names), caret, line numbers, selection, search
  results, inlay hints, ANSI palettes.

Each theme is complete rather than partial: all **242 themeable tokens** of
OpenIDEA 0.1.39 (plugin API 1.3) are set, so the look does not drift when the
IDE's built-in palette changes.

## Design

- Structure is carried by **neutral, low-chroma cool greys**; pink and violet
  appear only as accents, never on borders, gutters or block selections.
- Depth is expressed by **lightness steps between surfaces**, not by borders.
- `hover`, `current line`, `selection` and `selection-strong` are four distinct
  values in every theme, including Light.
- Light is an independent design, not a desaturated dark theme: near-white
  layered surfaces, neutral borders, and body text at WCAG AA (≥ 4.5:1).
- Sorbet Mint keeps that structure but moves it to mint: editor `#EDF3EE`,
  panels `#E1EBE2`, chrome `#D5E3D7`. Syntax follows Cosmic Sorbet Day — teal
  keywords, deep-green strings, plum types — and every text token is solved to
  ≥ 4.5:1 on all seven surfaces it can appear on, including the comment and
  line-number tokens the reference palette left below the threshold.
- The plugin icon is a vector redraw of the original Nebula Aura artwork: a
  violet-to-cyan ring with stray aura motes. `icons/nebula-aura.svg` is the
  muted variant for light themes, `icons/nebula-aura-dark.svg` the bright one
  for dark themes.

## Screenshots

Taken in OpenIDEA 0.1.36 with a synthetic demo project (TypeScript, Markdown,
JSON); no real project is shown.

| Dark | Violet |
|---|---|
| ![Nebula Aura Dark](screenshots/nebula-aura-dark.png) | ![Nebula Aura Violet](screenshots/nebula-aura-violet.png) |

| Midnight | Light |
|---|---|
| ![Nebula Aura Midnight](screenshots/nebula-aura-midnight.png) | ![Nebula Aura Light](screenshots/nebula-aura-light.png) |

## Install

1. Copy this folder, or a `.zip` of it, and pick it in
   _Settings › Plugins › ⚙ › Install Plugin from Disk…_.
2. In _Settings › Plugins_, select the plugin and press **Apply** next to the
   theme you want.
3. _Use Default Theme_ switches back to the built-in theme.

The plugin needs **OpenIDEA with plugin API 1.2 or later** (0.1.38 and newer),
because the manifest declares `icon` and `icon-dark`.

For development, place (or symlink) the folder in
`<project>/.openidea/plugins/nebula-aura/`; it loads as a dev plugin and
_Reload Plugins_ picks up edits.

## Layout

```
plugin.toml                       manifest (engines.openidea = "^1.2")
icons/nebula-aura.svg             plugin icon, light themes
icons/nebula-aura-dark.svg        plugin icon, dark themes
themes/nebula-aura-*.theme.json   UI tokens (121 per theme)
themes/nebula-aura-*.scheme.json  editor scheme tokens (121 per theme)
LICENSE                           MIT — original Nebula Aura Theme
LICENSE.openidea                  Apache-2.0 — OpenIDEA format reference
NOTICE                            attribution and change log
```

## Attribution and licence

The colour palettes and the original VS Code theme are
**Nebula Aura Theme** by Luis Mauro Penholato
(<https://github.com/luismpenholato/nebula-aura-theme>), released under the MIT
License; see `LICENSE`. This plugin is a port and redesign of those palettes to
OpenIDEA design tokens and keeps the MIT terms. The OpenIDEA plugin format,
token names and the Harbor Night completeness reference are Apache-2.0 by the
OpenIDEA contributors; see `LICENSE.openidea`. Redistribution and modification
are permitted by both licences; `NOTICE` records what changed.

## Validation

```sh
openidea-plugin check .
```

checks the manifest, the theme contributions, the token names and values, the
sanitised plugin icons, and that every referenced file exists inside the
package.
