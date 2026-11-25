# Omarchy theme backgrounds

The background stills for the built-in Omarchy themes. They ship as the `omarchy-themes-backgrounds` package, which installs `<theme>/<name>` here to `/usr/share/omarchy/themes/<theme>/backgrounds/<name>`, beside the theme itself from [omacom/omarchy](https://github.com/omacom/omarchy).

Backgrounds cycle in name order, so a leading number sets their place: `tokyo-night/0-liftoff.webp` is Tokyo Night's first. An intro from [omarchy-themes-intros](https://github.com/omacom/omarchy-themes-intros) or a loop from [omarchy-themes-loops](https://github.com/omacom/omarchy-themes-loops) belongs to the still here with the same name. A theme with no stills here gets one Omarchy draws from its colors. See `docs/theming.md` in omacom/omarchy for sizes and formats.

To add or change a background, open a pull request here. Once it merges, cut a release tagged with the date, `vYYYY.MM.DD` (or `vYYYY.MM.DD.1` for a second one that day). [omacom/omarchy-pkgs](https://github.com/omacom/omarchy-pkgs) picks the release up and updates `omarchy-themes-backgrounds` to it.
