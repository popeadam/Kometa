---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Streaming", 
        "CODE_NAME": "streaming",
        "LIBRARY_TYPE": "Movie, Show", 
        "SECTION_NUMBER": "030", 
        "DESCRIPTION": "dynamically create collections based on the streaming Services that your media is available on"
    }'
%}
{% include-markdown "./../templates/separator_line.md" replace='{"SEPARATOR": "Streaming"}' %}
| `All 4 Movies/Shows`       | `all4`        | Collection of Movies/Shows Streaming on All 4.       |
| `Apple TV+ Movies/Shows`   | `appletv`     | Collection of Movies/Shows Streaming on Apple TV+.   |
| `BET+ Movies/Shows`        | `bet`         | Collection of Movies/Shows Streaming on BET+.        |
| `BritBox Movies/Shows`     | `britbox`     | Collection of Movies/Shows Streaming on BritBox.     |
| `Crave Movies/Shows`       | `crave`       | Collection of Movies/Shows Streaming on Crave.       |
| `Crunchyroll Shows`        | `crunchyroll` | Collection of Shows Streaming on Crunchyroll.        |
| `discovery+ Shows`         | `discovery`   | Collection of Shows Streaming on discovery+.         |
| `Disney+ Movies/Shows`     | `disney`      | Collection of Movies/Shows Streaming on Disney+.     |
| `Hayu Shows`               | `hayu`        | Collection of Shows Streaming on Hulu.               |
| `Hulu Movies/Shows`        | `hulu`        | Collection of Movies/Shows Streaming on Hulu.        |
| `Max Movies/Shows`         | `max`         | Collection of Movies/Shows Streaming on Max.         |
| `Netflix Movies/Shows`     | `netflix`     | Collection of Movies/Shows Streaming on Netflix.     |
| `NOW Movies/Shows`         | `now`         | Collection of Movies/Shows Streaming on NOW.         |
| `Paramount+ Movies/Shows`  | `paramount`   | Collection of Movies/Shows Streaming on Paramount+.  |
| `Peacock Movies/Shows`     | `peacock`     | Collection of Movies/Shows Streaming on Peacock.     |
| `Prime Video Movies/Shows` | `amazon`      | Collection of Movies/Shows Streaming on Prime Video. |
| `Showtime Movies/Shows`    | `showtime`    | Collection of Movies/Shows Streaming on Showtime.    |
| `YouTube Movies/Shows`     | `youtube`     | Collection of Movies/Shows Streaming on YouTube.     |

## Regional Variants

Some logic is applied for specific regions to prevent collections appearing which do not exist in said region.

| Region           | Key                              | Description                                                                                                                                |
|:-----------------|:---------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| `CA`             | `max`, `showtime`                | These collections will not be created if the region is `CA` as these streaming services are part of the Crave streaming service in Canada. |
| any besides `CA` | `crave`                          | These collections will not be created if the region is not `CA` as these streaming services are Canada-focused.                            |
| any besides `GB` | `all4`, `britbox`, `hayu`, `now` | These collections will not be created if the region is not `GB` as these streaming services are UK-focused.                                |

{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "streaming"}' %}    
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: streaming
            template_variables:
              region: FR #(1)!
              sep_style: amethyst #(2)!
              visible_library_disney: true #(3)!
              visible_home_disney: true #(4)!
              visible_shared_disney: true #(5)!
              sonarr_add_missing_hulu: true #(6)!
              radarr_add_missing_amazon: true #(7)!
              sort_by: random #(8)!
    ```

    1.  Use French region to determine streaming data from JustWatch/TMDb.
    2.  Use the amethyst [Separator Style](../separators.md#separator-styles)
    3.  Pin the "Disney+ Movies/Shows" collection to the Recommended tab of the library
    4.  Pin the "Disney+ Movies/Shows" collection to the home screen of the server owner
    5.  Pin the "Disney+ Movies/Shows" collection to the home screen of other users of the server
    6.  Add missing shows in your library from the "Hulu Shows" list to your Sonarr
    7.  Add missing movies in your library from the "Prime Video Movies" list to your Radarr
    8.  Sort all the collections created by this file randomly

{% include-markdown "./../templates/defaults_variables_header.md" %}
    | `discover_with_<<key>>`         | **Description:** Overrides the TMDb Watch Provider used for the specified key. This is only needed if a specific `region` has a different ID for the watch provider.<br>**Default:** `<<discover_with>>`<br>**Values:** Any TMDb Watch Provider ID for [Movies](https://developer.themoviedb.org/reference/watch-providers-movie-list) / [Shows](https://developer.themoviedb.org/reference/watch-provider-tv-list) based on the user's region |
    | `exclude`                       | **Description:** Exclude these Streaming Services from creating a Dynamic Collection.<br>**Values:** List of Streaming Service Keys                                                                                                                                                                                                                                                                                                            |
    | `limit_<<key>>`<sup>1</sup>     | **Description:** Changes the Builder Limit of the [key's](#collection_section) collection.<br>**Default:** `limit`<br>**Values:** Number Greater than 0                                                                                                                                                                                                                                                                                        |
    | `limit`                         | **Description:** Changes the Builder Limit for all collections in a Defaults File.<br>**Default:** `500`<br>**Values:** Number Greater than 0                                                                                                                                                                                                                                                                                                  |
    | `name_format`                   | **Description:** Changes the title format of the Dynamic Collections.<br>**Default:** `<<key_name>> <<library_translationU>>s`<br>**Values:** Any string with `<<key_name>>` in it.                                                                                                                                                                                                                                                            |
    | `originals_only`                | **Description:** Changes Streaming Service lists to only show original content produced by the service.<br>**Note**: Cannot be used with `region`, and only produces collections for `amazon`, `appletv`, `disney`, `max`, `hulu`, `netflix`, `paramount`, `peacock`<br>**Default:** `false`<br>**Values:** `true`, `false`                                                                                                                    |
    | `region`                        | **Description:** Changes some Streaming Service lists to regional variants (see below table for more information.<br>**Default:** `us`<br>**Values:** Any [ISO 3166-1 Code](https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) of the region where the streaming information should be based on.                                                                                                                                          |
    | `sort_by_<<key>>`<sup>1</sup>   | **Description:** Changes the Smart Filter Sort of the [key's](#collection_section) collection.<br>**Default:** `sort_by`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                                                                                                                                                                                                            |
    | `sort_by`                       | **Description:** Changes the Smart Filter Sort for all collections in a Defaults File.<br>**Default:** `release.desc`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                                                                                                                                                                                                               |
    | `style`                         | **Description:** Changes the color scheme of the collection posters.<br>**Default:** `color`<br>**Values:** `color` or `white`                                                                                                                                                                                                                                                                                                                 |
    | `summary_format`                | **Description:** Changes the summary format of the Dynamic Collections.<br>**Default:** `<<library_translationU>>s streaming on <<key_name>>.`<br>**Values:** Any string.                                                                                                                                                                                                                                                                      |
    | `sync_mode_<<key>>`<sup>1</sup> | **Description:** Changes the Sync Mode of the [key's](#collection_section) collection.<br>**Default:** `sync_mode`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>                                                                                                                                  |
    | `sync_mode`                     | **Description:** Changes the Sync Mode for all collections in a Defaults File.<br>**Default:** `sync`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>                                                                                                                                               |

    1. Each default collection has a [`key`](#collection_section) that you must replace `<<key>>` with when using 
    this Template Variable. These keys are found in the table at the top of this page.

{% include-markdown "./../templates/defaults_variables.md" %}