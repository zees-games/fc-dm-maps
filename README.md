Deathmatch and gun game maps for [Fatal Contact](https://github.com/zees-games/game-fatal-contact) (FC), imported from community maps. Its sibling pack is fc-surf-dm-maps.

Every map is somebody else's work, imported so it can be played again. Each one is credited below, in `maps.json`, and on screen when a server changes to it. If you made one of these maps and want it credited differently or taken down, open an issue and it will be done.

## What is in it

| Path | Contents |
| --- | --- |
| `maps/` | The imported maps (not stored in git, see "Getting the maps") |
| `maps.json` | The list of maps with author and source |
| `zones/<id>.json` | Per-map attribution, kind and the modes it can host |
| `licence.json` | Licence record per map |
| `content.lock.json` | Pins each map's published pack |
| `tools/` | Pack staging and checks |

Each map is its own signed pack, `gamemann/<map id>`. All of them are listed under this repository's one Workshop page. Releases are made by tagging the repository (`.github/workflows/release.yml`).

## Getting the maps

The map files are not in git. `content.lock.json` pins each map's pack, so `../dot-bootstrap/bootstrap.sh` (or `./fetch-content.sh` here) fills `maps/`. Fatal Contact reads them through its `maps/imported_dm` link.

To offer them on a server, name them in the server's `cfg/server/content/overrides.yml`, one line per map in `maps.json`. Ids use hyphens because the site refuses an underscore in the repository segment.

```yaml
games:
  game-arena:   # the Fatal Contact project directory
    maps:
      add:
        - gamemann/aim-forts
        - gamemann/gg-canyon
        # ... one line per map in maps.json
```

## Which maps host which modes

A map's `modes` list (from `zones/<id>.json`) names the modes it can host. Without a list a map hosts free-for-all and gun game, since team modes need tagged spawns and imported maps have no objectives.

| Map | Modes |
| --- | --- |
| `cp-orange-x3` | free-for-all, gun game, snipers, team deathmatch, capture the flag |
| every other map | free-for-all and gun game |

Capture the flag needs room: each base needs its own spawns and a flag home, and the walk between flags should take over 20 seconds at run speed (about 60 m). Only `cp-orange-x3` is large enough.

`cp-orange-x3` is a Team Fortress 2 control point map. Every Valve texture and model is replaced by a free one (CC0), and none of the original art ships. Its team spawns become `red` and `blue` spawns, and `zones/cp-orange-x3.json` places a flag marker at each side's last control point.

## Quality and ongoing improvement

The models, textures, animations, sounds and maps in this pack are improved automatically and recursively by AI agents. [Nightly](https://github.com/gamemann/nightly) keeps a board of improvement items. Agents pick up an item, make the change, render fresh frames and check them with a visual judge. Judge findings become new items, and the loop repeats until the result is production quality. Improvements ship as new pack versions, and the screenshots in this README are re-shot each time. Some assets are still low quality today.

## Credits

The maps are GameBanana uploads under the site's default licence, CC BY-NC-ND 4.0, except where the table says otherwise. They are published under the credited-community-map exception in `licence.json`, with this credit, the source link and the removal offer.

| Map | Author | Source | Licence |
| --- | --- | --- | --- |
| `aim-forts` | NoBuxs | https://gamebanana.com/mods/116937 | CC BY-NC-ND 4.0 |
| `blackhawkdown` | Cc_NIPPER | https://gamebanana.com/mods/116994 | CC BY-NC-ND 4.0 |
| `crackhouse` | unknown | user-supplied archive, no source page | CC BY-NC-ND 4.0 |
| `dm-hot-cn-v1` | seigneurdesombres | https://gamebanana.com/mods/117417 | CC BY-NC-ND 4.0 |
| `dm-industrial-gamma` | warhawk3407 | https://gamebanana.com/mods/117427 | CC BY-NC-ND 4.0 |
| `dm-morpheus` | mr-thermaltake | https://gamebanana.com/mods/117486 | CC BY-NC-ND 4.0 |
| `dm-overwatch` | LikeMike213 | https://gamebanana.com/mods/117534 | CC BY-NC-ND 4.0 |
| `dm-scarletdevilmansion` | Deity Link | https://gamebanana.com/mods/117571 | CC BY-NC-ND 4.0 |
| `gg-canyon` | Devi8 | https://gamebanana.com/mods/134054 | CC BY-NC-ND 4.0 |
| `gg-fy-snow` | s1nk0 | https://gamebanana.com/mods/135022 | CC BY-NC-ND 4.0 |
| `gg-garage` | SGT_kick_ur_ass | https://gamebanana.com/mods/135049 | CC BY-NC-ND 4.0 |
| `gg-krusty-krab` | FireWavezZ | https://gamebanana.com/mods/135508 | CC BY-NC-ND 4.0 |
| `gg-lego-arena` | Jevan | https://gamebanana.com/mods/135558 | CC BY-NC-ND 4.0 |
| `gg-punishment` | Karatekaefer | https://gamebanana.com/mods/136211 | CC BY-NC-ND 4.0 |
| `gg-simpsons-x` | BasicAir | https://gamebanana.com/mods/136613 | CC BY-NC-ND 4.0 |
| `gg-woods` | X-tr3m3r | https://gamebanana.com/mods/137426 | CC BY-NC-ND 4.0 |
| `welcometomexicov6` | zaki90 | https://gamebanana.com/mods/117984 | CC BY-NC-ND 4.0 |
| `cp-orange-x3` | White wolf, GGODD2, renguard, mwhahaha (Orange_X variant; wiki: https://wiki.teamfortress.com/wiki/Orange_X) | https://gamebanana.com/mods/69885 | CC BY-NC-ND 4.0 |

If you made one of these maps and want it removed, open an issue at https://github.com/zees-games/fc-dm-maps/issues.
