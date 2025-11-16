# Left 4 Dead 2 SourcePawn Collection

This repository aggregates dozens of custom SourcePawn plugins, shared include files, and gamedata used to extend **Left 4 Dead** and **Left 4 Dead 2**.  The tree has been refactored so every file lives in a predictable location with lower_snake_case naming, all user-facing phrases are in English, and fresh documentation explains how to build or selectively deploy each component.

## Repository layout

```
├── src/
│   ├── left4dead/            # L4D-specific plugins grouped under gameplay/
│   ├── left4dead2/
│   │   ├── gameplay/         # General L4D2 plugins (one .sp per feature)
│   │   └── skill_framework/  # All l4d2sf_* skill framework modules
│   ├── new_mode_pack/        # Former nmp_* scripts
│   ├── sourcemod/            # Former sm_* utilities
│   ├── utilities/            # Miscellaneous plugins with no strict domain
│   └── modules/              # AI helpers and spawn system modules
├── include/                 # Stock and custom include files (*.inc)
├── configs/                 # Example config files and SQL init scripts
├── data/                    # Plugin data tables (loot tables, etc.)
├── gamedata/                # Signature/offset definitions loaded at runtime
├── translations/            # English phrase files for all plugins
└── docs/                    # Reports (e.g., potential orphaned assets)
```

Every original `.sp` file lives under `src/` and uses lower_snake_case naming.  Includes now live under `include/` (the former `includes/` folder was merged here), and SourceMod modules that used to live at the repository root can now be found in `src/modules/` for consistency.

### Naming and ownership conventions

* Each plugin filename mirrors its `PLUGIN_NAME` or historical prefix (e.g., `l4d2sf_idle_blocker.sp` ⇒ `src/left4dead2/skill_framework/idle_blocker.sp`).
* Shared logic belongs inside `include/` or `src/utilities/` so gameplay plugins can depend on them without circular references.
* If you add new gamedata or translations, place them under `gamedata/` and `translations/` respectively, keeping the same basename used in the SourcePawn code.

## Prerequisites

1. Install the SourceMod compiler (`spcomp`) that matches your game server build.  The compiler is included with every SourceMod release.
2. Ensure `spcomp` is on your `PATH`, or call it with the absolute path (e.g., `~/sourcemod/scripting/spcomp`).
3. Optionally install helper scripts such as `compile.sh` that iterate through `src/**/**/*.sp` if you routinely build multiple plugins.

## Building plugins

1. From the repository root, run `spcomp` against the desired source file inside `src/`:
   ```bash
   spcomp -i include src/left4dead2/gameplay/idle_blocker.sp
   ```
2. Copy the resulting `.smx` into your server's `addons/sourcemod/plugins/` directory.
3. Deploy any required config (`configs/`), translation (`translations/`), gamedata (`gamedata/`), or data files (`data/`).  Each plugin header documents which supporting files it expects.
4. Repeat for any additional plugins you need.  When scripting bulk builds, respect the directory layout (for example, you may wish to build only `src/left4dead2/gameplay/*.sp` for an L4D2-only server).

### Verifying the restructure

* Spot-check a handful of migrated files (`src/left4dead2/gameplay/fly_you_fools.sp`, `src/utilities/left4dhooks.sp`, `src/modules/AI_Tank.sp`, etc.) with `git diff` to confirm no unintended edits occurred during the renames.
* If you maintain CI/CD scripts, update their paths to point at the new `src/` hierarchy and the merged `include/` folder.
* When running `spcomp`, include `-i include` (and additional `-i` paths if you keep private includes) so dependencies such as `hardcoop_util.inc` resolve correctly.

## Translation cleanup

All phrase files inside `translations/` now provide English text, and the legacy `translations/chi` / `translations/zho` folders have been removed.  To update text:

1. Edit the `"en"` entry for the relevant phrase.
2. Keep `%T` keys synchronized with the SourcePawn code—review `translations/l4d2_simplecombat2.phrases.txt` and `translations/l4d2sf_*.phrases.txt` for formatting examples.
3. If you require additional locales, add new language blocks under each phrase without removing English.

## Potentially orphaned gamedata

A scripted scan flagged gamedata files whose basenames never appear in the new `src/` tree.  The curated list (with obvious false positives removed) lives in [`docs/ORPHANS.md`](docs/ORPHANS.md).  Review each entry before deleting files—some plugins may load gamedata dynamically.

## Maintenance checklist

* **Before committing:** run `git status -sb` to ensure only intentional renames/edits are staged.
* **Before deploying:** compile a sampling of plugins for both games to ensure includes resolve after future refactors.
* **Periodically:** re-run the orphan scan (or manually search for `FetchGameData("<name>")`) so `gamedata/` stays lean, and audit translations to make sure new menus or messages stay in English.

## Next steps

* Delete or archive gamedata files confirmed unused.
* Create CI scripts or GitHub Actions to compile the plugin subsets you actually run on production servers.
* Convert any remaining non-English comments in the source code if they surface in user-facing log lines or chat output.
