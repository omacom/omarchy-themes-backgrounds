# Instructions for agents

This repository holds the background stills for Omarchy's built-in themes. Every `<theme>/<file>` entry ships in the `omarchy-themes-backgrounds` package and lands in every Omarchy ISO.

## Rules

- Keep every still at or under **5120 px** on both width and height (5K cap).
- Do not add non-hidden top-level directories for tooling or docs. The Arch `PKGBUILD` installs every `*/*` path as a theme background, so repo helper scripts live under `.github/scripts/`.
- Never rename or change the extension of an existing background unless its matching intro in `omacom/omarchy-themes-intros`, loop in `omacom/omarchy-themes-loops`, and user symlinks (`~/.local/state/omarchy/current/background`) are updated together.
- Use `.github/scripts/prepare <file>` when adding or resizing stills larger than 5120 px. It downscales photographs in linear RGB with Lanczos3, encodes WebP with `-sharp_yuv -m 6` targeting >= 42 dB PSNR, preserves alpha channels and RGB ICC profiles with `webpmux`, and keeps lossless low-color (<= 256 colors) illustrations palette-preserved and lossless.
- Do not re-encode stills that are already at or under 5120 px.
- Run `.github/scripts/check` before committing. CI runs it on every pull request and push to `master`.
