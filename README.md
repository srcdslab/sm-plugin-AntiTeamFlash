# sm-plugin-AntiTeamFlash

### Stop flashbangs from blinding teammates, the thrower, spectators and dead players in Counter-Strike: Source.

srcdslab port of **Anti Team Flash** 1.2.4 ([AlliedModders thread](https://forums.alliedmods.net/showthread.php?t=139505)).

## How it works

Every `flashbang_projectile` is queued with its thrower and the thrower's team (first in, first out). When a flashbang blinds a player (`player_blind`), the plugin compares the player with the oldest queued flashbang and cancels the blindness of teammates (and, if wanted, of the thrower), dead players and spectators by setting `m_flFlashMaxAlpha` to `0.5`. The queue entry is removed on `flashbang_detonate`.

The plugin only uses game events, SDKHooks' `OnEntityCreated` and network properties: no gamedata, offsets or SDK calls, so it runs unchanged on the x86 and x86_64 (SourceMod 1.13) builds of Counter-Strike: Source.

## Requirements

- Counter-Strike: Source
- SourceMod 1.12 or newer (SDKHooks is bundled with SourceMod)

## Installation

Download `sm-plugin-AntiTeamFlash-<version>-sm1.12.tar.gz` or `-sm1.13.tar.gz` from the [releases](https://github.com/srcdslab/sm-plugin-AntiTeamFlash/releases) and extract it in `cstrike/`:

```
addons/sourcemod/plugins/AntiTeamFlash.smx
```

## ConVars

| ConVar | Default | Description |
|---|---|---|
| `css_anti_team_flash` | `1` | Enables/disables all features of this plugin. |
| `css_anti_team_flash_team` | `1` | If enabled, players will be unable to team flash their teammates. |
| `css_anti_team_flash_dead` | `1` | If disabled, flashbangs will flash dead players. |
| `css_anti_team_flash_spec` | `1` | If disabled, flashbangs will flash spectators. |
| `css_anti_team_flash_owner` | `0` | If disabled, flashbangs will flash their owners. |
| `css_anti_team_flash_time` | `0.0` | Number of seconds after `round_freeze_end` after which the plugin stops protecting players (`0` = always protect). |
| `css_anti_team_flash_none` | `0` | If enabled, flashbangs do not explode at all and are deleted after `css_anti_team_flash_life` seconds. |
| `css_anti_team_flash_life` | `2.0` | Lifetime of a flashbang when `css_anti_team_flash_none` is enabled. |
| `sm_anti_team_flash_version` | | Plugin version (public, shown in the server rules). |

The config file is `cfg/sourcemod/anti_team_flash.cfg` (created on first load).

## Credits

- [thetwistedpanda](https://forums.alliedmods.net/member.php?u=41467) (Twisted|Panda): Anti Team Flash 1.0 - 1.2.3.
- [vertigo](https://forums.alliedmods.net/member.php?u=291024): 1.2.4, new syntax ([post](https://forums.alliedmods.net/showthread.php?p=2730840)).
- SAMURAI16 and Kigen: original idea.

The first commit of this repository is the unmodified 1.2.4 source. See [CHANGELOG.md](CHANGELOG.md) for the srcdslab changes.
