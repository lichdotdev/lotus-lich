<p align="center">
    <h2 align="center">Lotus for lich</h2>
</p>

<p align="center">Pastel dark and light theme, ported from the Lotus Theme for JetBrains IDEs</p>

<p align="center">
    <a href="https://plugins.jetbrains.com/plugin/14369-lotus-theme">
        <img src="https://img.shields.io/badge/community-lotus%20theme-de67bb?labelColor=141414&style=for-the-badge" />
    </a>
</p>

## Usage

1. Open lich → **Settings → Appearance → Import**.
2. Paste the repository URL: `https://github.com/lichdotdev/lotus-lich`
3. Click **Install**.
4. Pick a variant in the theme picker. The terminal picker defaults to
   **Match app theme**, so one pick dresses both — or choose a different variant
   there if you want the panes to differ.

To take a later release, hit **Update** on the theme's row.

### Local install

An absolute path is an accepted remote, so a clone installs the same way:

```bash
git clone https://github.com/lichdotdev/lotus-lich.git
```

Then paste the absolute path of the clone into **Settings → Appearance → Import**.

## Variants

| Theme | `id` | `scheme` |
|---|---|---|
| Lotus Dark | `lotus-dark` | dark |
| Lotus Light | `lotus-light` | light |

## Port notes

Colors are read from the plugin's own source
([`blai30/Lotus-Theme`](https://github.com/blai30/Lotus-Theme)): the
`*.theme.json` UI palette and the `colors/*.xml` editor scheme, not
guessed from screenshots. A few gaps are filled by nearest source value
rather than invented:

- Both variants leave ANSI black undefined in the source scheme — the
  terminal `black`/`brightBlack` here fall back to the theme's own
  border/muted-text tokens.
- The source's ANSI **blue** slot (`CONSOLE_BLUE_OUTPUT`) is an
  orange-toned color in both Dark and Light, not blue — kept as-is for
  fidelity to the plugin rather than corrected.
- Light's console foreground/background are unset in the source (falls
  back to the editor default), resolved here to the theme's own
  `background`/`foreground`.

## Status tones

`tone-pass` and `tone-wait` are what lich 0.53.0 reads for "passed" and "waiting
on you". The status line sets them at 12px, where WCAG asks 4.5:1 with no
large-text exemption, so where the palette value did not clear that against the
card it sits on, its lightness was moved and its hue and saturation kept: the
same move lich makes for its own two.

| Variant | `tone-pass` | `tone-wait` |
|---|---|---|
| Lotus Dark | `#a9dc76` (ANSI green) | `#ffd866` (ANSI yellow) |
| Lotus Light | `#526c38` (ANSI green, darkened) | `#6f6517` (ANSI yellow, darkened) |

## Thanks to

- [omartelo](https://github.com/omartelo) — port author
- [blai30](https://github.com/blai30) — original Lotus Theme

## Contributing

Each variant is one lich theme file — `lotus-dark.json`, `lotus-light.json` —
beside the `lich-theme.json` manifest that carries the pack's version.

To propose a tweak:

1. Fork the repo.
2. Edit the relevant variant file.
3. Validate the **whole directory** — a repository installs all or nothing:
   `node validate.mjs .` (ships with the lich `theme` skill).
4. Bump `version` in `lich-theme.json` in the same commit. An unbumped version
   ships nothing: **Update** compares only that number.
5. Open a PR.

## License

[MIT](./LICENSE)
