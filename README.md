# RockMigrations1

This module can be used in parallel to RockMigrations (v2022) for backwards compatibility (in case you need some functionality that the 2022 version of RockMigrations does not provide).

If you are using both modules, the `$rockmigrations` API variable will be the newer version of RM and you can access the old version via `$wire->rockmigrations1`.

## Setup of RM1 + RM

If you are using RockMigrations < 0.0.87 and you want to add the new version of RM to your project do the following:

* Remove RockMigrations from your system by deleting `/site/modules/RockMigrations`
* Clone the new version to `/site/modules/RockMigrations`
* Clone RM1 to `/site/modules/RockMigrations1`
* Do a modules refresh
