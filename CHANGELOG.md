## Release Notes

## [1.2.5-srcdslab]

### Changed

- srcdslab layout (`addons/sourcemod/scripting/AntiTeamFlash.sp`), CI build for SourceMod 1.12 and 1.13
  with release archives, Dependabot.
- Methodmaps (`ConVar`, `ArrayList`, `Event`) instead of the old handle functions.
- `myinfo` URL points to this repository.

### Fixed

- Timer and event callbacks returned no value (compiler warnings).
- Changing `css_anti_team_flash_time` during a round, or a `round_freeze_end` without a `round_end`
  before it, started a second disable timer and lost the handle of the first one.

ConVar names, defaults and behaviour are unchanged.

## [1.2.4] - 2020-12-31 (vertigo)

- New syntax and optimized code.
- No longer reads the flashbang queue when it is empty.

## [1.2.3] - 2011-11-18 (thetwistedpanda)

- Last release of the original thread.
