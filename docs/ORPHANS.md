# Potential Orphaned Assets

The following gamedata files are not referenced by any SourcePawn file in `src/`.
They may be historical leftovers that can likely be removed or archived after manual verification:

- CAI_Concept.txt
- DataTable.txt
- LagExploitFix_3_7_2020.txt
- M60_GrenadeLauncher_patches.txt
- Realistico.GameData.txt
- SuperTanks.txt
- abm.txt
- antimedkit.txt
- charger_collision_patch.txt
- control_zombies.txt
- defib_fix.txt
- dhooks-test.games.txt
- dhooks.weapon_shootposition.txt
- dynamic_soundtrack.txt
- hunter_pounce_alignment_fix.txt
- l4d2_air_data.txt
- l4d2_bm_sig.txt
- l4d2_bots_fix_gamedata.txt
- l4d2_car_alarm_bots.txt
- l4d2_charger_action.txt
- l4d2_charger_punch.txt
- l4d2_collision.txt
- l4d2_csweapons.txt
- l4d2_deceptive_bosses.txt
- l4d2_detonationforce.txt
- l4d2_dlc2_levelup.txt
- l4d2_gascan_data.txt
- l4d2_gibs.txt
- l4d2_gift_rewards.txt
- l4d2_grenade_missile.txt
- l4d2_infected_release.txt
- l4d2_items_pass_rework.txt
- l4d2_ladderrambos.txt
- l4d2_melee_range.txt
- l4d2_minigun_victim.txt
- l4d2_nav_loot.txt
- l4d2_patch_air.txt
- l4d2_pounce_damage.txt
- l4d2_release_victim_data.txt
- l4d2_revive_gamedata.txt
- l4d2_rock_gamedata.txt
- l4d2_shove_fix.txt
- l4d2_spitter_acid_damage.txt
- l4d2_spitter_projectile.txt
- l4d2_stringtable_control.txt
- l4d2_throwable_melee.txt
- l4d2_tickrate_enabler.txt
- l4d2_viciousinfected.txt
- l4d2_viciousplugins.txt
- l4d2_vomitjar_shove.txt
- l4d2_zcs.txt
- l4d2_zoom_hack.txt
- l4d2customcmds.txt
- l4d_car_alarm_bots.txt
- l4d_car_alarm_vomit.txt
- l4d_console_spam.txt
- l4d_coop_markers.txt
- l4d_dissolve_infected.txt
- l4d_extinguisher.txt
- l4d_god_frames.txt
- l4d_incapped_shove.txt
- l4d_incapped_weapons.txt
- l4d_info_editor.txt
- l4d_pipebomb_shove.txt
- l4d_reload_fix.txt
- l4d_reservecontrol.txt
- l4d_survivor_identity_fix.txt
- l4d_survivor_shove.txt
- l4d_tank_punch_force.txt
- l4d_use_priority.txt
- l4dslots.txt
- pipe_bomb.txt
- plugin.perkmod.txt
- rock_lagcomp.txt
- smlib_colors.games.txt
- spawn_infected_nolimit.txt
- transitionzombiespawnfix.txt
- usermsg_hooks.games.txt
- witch_allow_in_safezone.txt
- witch_target_patch.txt
- witch_update_nbm.txt
- witchred.txt

Revisit each file to confirm whether a legacy plugin still relies on it before deletion.

## Verified in use

The following files were originally flagged but are still referenced by active plugins and **should not** be removed:

- `WeaponHandling.txt` (used by `src/utilities/weapon_handling.sp`)
- `command_buffer.games.txt` (used by `src/utilities/command_buffer.sp`)
- `infected_ability_touch_hook.txt` (used by `src/utilities/infected_ability_touch_hook.sp` and dependent gameplay modules)
- `input_hooks.games.txt` (used by `src/utilities/input_hooks.sp`)
- `spray_exploit_fixer.txt` (used by `src/utilities/spray_exploit_fixer.sp`)
- `staggersolver.txt` (used by `src/left4dead2/gameplay/ai_damagefix.sp` and related plugins)
