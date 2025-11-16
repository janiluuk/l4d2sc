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

