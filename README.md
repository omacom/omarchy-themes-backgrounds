# Omarchy theme backgrounds

This repository holds the background stills for built-in Omarchy themes. They ship in the `omarchy-themes-backgrounds` package, which installs `<theme>/<name>` to `/usr/share/omarchy/themes/<theme>/backgrounds/<name>`, beside each theme from [omacom/omarchy](https://github.com/omacom/omarchy).

Backgrounds cycle in name order, so a leading number sets their position. For example, `tokyo-night/0-liftoff.webp` is Tokyo Night's first still. An intro from [omarchy-themes-intros](https://github.com/omacom/omarchy-themes-intros) or a loop from [omarchy-themes-loops](https://github.com/omacom/omarchy-themes-loops) matches the still here with the same stem. A theme with no stills here gets a generated background from its palette. See `docs/theming.md` in [omacom/omarchy](https://github.com/omacom/omarchy) for how themes use backgrounds.

## Image requirements

- **Maximum size:** 5120 px on the long edge (5K, such as `5120x2880` for 16:9). Qt6's WebP decoder expands full native pixels before scaling, so larger files spike shell memory and decode latency.
- **Format:** single-frame WebP (`.webp`) for new additions. Existing `.jpg` stills stay as-is unless replaced. CI checks that every file matches its extension, decodes cleanly, has one frame, and stays within 5120 px.
- **Color and quality:** downscale photographs in linear RGB with Lanczos3, then encode with `cwebp -m 6 -sharp_yuv` (`-sharp_yuv` preserves saturated RGB edges on high-DPI displays). Preserve embedded RGB ICC profiles (such as Display P3 or sRGB) with `webpmux -set icc`. Keep lossless low-color (<= 256 colors) illustrations palette-preserved and lossless (`-lossless -z 9`).

## Preparing and checking backgrounds

Install ImageMagick and the WebP CLI tools (`webp` on Ubuntu/Debian/Homebrew, `libwebp-utils` on Arch Linux). Run `.github/scripts/prepare` on any new or updated image over 5120 px, then run `.github/scripts/check` before opening a pull request:

```bash
.github/scripts/prepare <theme>/<file>.webp
.github/scripts/check
```

CI runs `.github/scripts/check` on every pull request and push to `master`. Helper scripts live under `.github/scripts/` because the Arch `PKGBUILD` installs every `*/*` entry as a theme background.

## Releasing

Open a pull request here to add or change a background. Once it merges, cut a release tagged with the date: `vYYYY.MM.DD` (or `vYYYY.MM.DD.1` for a second release that day). [omacom/omarchy-pkgs](https://github.com/omacom/omarchy-pkgs) picks up the release and updates `omarchy-themes-backgrounds`.
