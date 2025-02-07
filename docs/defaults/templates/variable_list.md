
<!--exclude-->
| `exclude` | **Description:** Exclude these NAME from creating a Dynamic Collection.<br>**Values:** List of VALUE |
<!--exclude-->
<!--include-->
| `include` | **Description:** Force these NAME to be included to create a Dynamic Collection.<br>**Values:** List of VALUE |
<!--include-->
<!--limit-->
| `limit`                     | **Description:** Changes the Builder Limit for all collections in a Defaults File.<br>**Values:** Number Greater than 0                                 |
| `limit_<<key>>`<sup>1</sup> | **Description:** Changes the Builder Limit of the [key's](#collection_section) collection.<br>**Default:** `limit`<br>**Values:** Number Greater than 0 |
<!--limit-->
<!--sort_by-->
| `sort_by` | **Description:** Changes the Smart Filter Sort for all collections in a Defaults File.<br>**Default:** `release.desc`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options) |
| `sort_by_<<key>>`<sup>1</sup> | **Description:** Changes the Smart Filter Sort of the [key's](#collection_section) collection.<br>**Default:** `sort_by`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options) |
<!--sort_by-->
<!--style-->
| `style` | **Description:** Controls the visual theme of the collections created.<br>**Default:** `bw`<br>**Values:** `bw`, `rainier`, `signature`, `diiivoy`, or `diiivoycolor` |
<!--style-->
<!--sync_mode-->
| `sync_mode`                     | **Description:** Changes the Sync Mode for all collections in a Defaults File.<br>**Default:** `sync`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>              |
| `sync_mode_<<key>>`<sup>1</sup> | **Description:** Changes the Sync Mode of the [key's](#collection_section) collection.<br>**Default:** `sync_mode`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table> |
<!--sync_mode-->
<!--format-->
| `name_format` | **Description:** Changes the title format of the Dynamic Collections.<br>**Default:** `NAME_FORMAT`<br>**Values:** Any string with `<<key_name>>` in it. |
| `summary_format` | **Description:** Changes the summary format of the Dynamic Collections.<br>**Default:** `SUMMARY_FORMAT`<br>**Values:** Any string with `<<key_name>>` in it. |
<!--format-->
<!--tmdb_birthday-->
| `tmdb_birthday` | **Description:** Controls if the Definition is run based on `tmdb_person`'s Birthday. Has 3 possible attributes `this_month`, `before` and `after`.<br>**Values:**<table class="clearTable"><tr><td>`this_month`</td><td>Run's if Birthday is in current Month</td><td>`true`/`false`</td></tr><tr><td>`before`</td><td>Run if X Number of Days before the Birthday</td><td>Number 0 or greater</td></tr><tr><td>`after`</td><td>Run if X Number of Days after the Birthday</td><td>Number 0 or greater</td></tr></table> |
<!--tmdb_birthday-->
<!--tmdb_person_offset-->
| `tmdb_person_offset_<<key>>`<sup>1</sup> | **Description:** Changes the summary tmdb_person_offset for the specific key.<br>**Default:** `0`<br>**Values:** Dictionary of Actor Name as the keys and the tmdb_person_offset as the value. |
<!--tmdb_person_offset-->

<!--sup1-->
1. Each default collection has a [`key`](#collection_section) that you must replace `<<key>>` with when using this Template Variable. These keys are found in the table at the top of this page.
<!--sup1-->