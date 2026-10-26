# CyoriaSMP Experimental Folia Port

- Upstream: [nulli0n/ExcellentEnchants-spigot](https://github.com/nulli0n/ExcellentEnchants-spigot)
- License: GPL-3.0 (see `LICENSE`); all upstream authors retain credit.
- Target: Minecraft 1.21.11 / Folia 1.21.11 build 14 / Java 25.
- Base plugin: ExcellentEnchants 5.4.3, paired with nightcore 3.1.1.
- Stage: **Experimental / pre-release**, not a claim of 100% Folia safety.

## Changes

Existing compatibility edits port callback scheduling and supported event handlers.
The 2026-10-26 follow-up routes passive enchant callbacks that access entity
inventory through the owning entity's Folia EntityScheduler rather than the
global region scheduler. This fixes the ArmorStand equipment thread exception
seen in production logs before this patch. The same JAR started on isolated
Folia with 61 loaded enchantments, a summoned Armor Stand and Zombie, and no
passive scheduler thread violation; production subsequently cold-booted with
61 enchantments and zero errors in the observed boot log.

## Limitations

Cross-region combat, enchant item effects, async arrow/block effects and
long-duration multi-player behavior are **not fully validated**. Requires
nightcore and appropriate tooltip provider for tooltip integration. Back up
world and plugin data before testing. Report logs and reproducible steps.

The project contains source changes under the original GPL; the downloadable
JAR must be tested on a non-production server before general use.
