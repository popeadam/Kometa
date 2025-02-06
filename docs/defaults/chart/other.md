---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Other Charts", 
        "CODE_NAME": "other_chart",
        "LIBRARY_TYPE": "Movie, Show", 
        "DESCRIPTION": "create collections based on other charts",
        "SECTION_NUMBER": "020"
    }'
    replace-tags='{"space": "Recommendations: The `StevenLu\'s Popular Movies` and `Top 10 Pirated Movies of the Week` Collections only work with Movie Libraries."}'
%}
| `AniDB Popular`                     | `anidb`       | Collection of the most Popular Anime on AniDB.       |
| `Common Sense Selection`            | `commonsense` | Collection of Common Sense Selection Movies/Shows.   |
| `Metacritic Must See Movies`        | `metacritic`  | Collection of Metacritic Must See Movies.            |
| `StevenLu's Popular Movies`         | `stevenlu`    | Collection of StevenLu's Popular Movies.             |
| `Top 10 Pirated Movies of the Week` | `pirated`     | Collection of the Top 10 Pirated Movies of the Week. |

{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "other_chart"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: other_chart
            template_variables:
              use_anidb: false #(1)!
              visible_library_commonsense: true #(2)!
              visible_home_commonsense: true #(3)!
              visible_shared_commonsense: true #(4)!
    ```

    1.  Do not create the "AniDB Popular" collection
    2.  Pin the "Common Sense Selection" collection to the Recommended tab of the library
    3.  Pin the "Common Sense Selection" collection to the home screen of the server owner
    4.  Pin the "Common Sense Selection" collection to the home screen of other users of the server

{% include-markdown "./../templates/defaults_variables_header.md" exclude-tags="separator" %}
    | `collection_order_<<key>>`<sup>1</sup> | **Description:** Changes the Collection Order of the [key's](#collection_section) collection.<br>**Default:** `collection_order`<br>**Values:**<table class="clearTable"><tr><td>`release`</td><td>Order Collection by Release Dates</td></tr><tr><td>`alpha`</td><td>Order Collection Alphabetically</td></tr><tr><td>`custom`</td><td>Order Collection Via the Builder Order</td></tr><tr><td>[Any `plex_search` Sort Option](../../files/builders/plex.md#sort-options)</td><td>Order Collection by any `plex_search` Sort Option</td></tr></table> |
    | `collection_order`                     | **Description:** Changes the Collection Order for all collections in a Defaults File.<br>**Default:** `custom`<br>**Values:**<table class="clearTable"><tr><td>`release`</td><td>Order Collection by Release Dates</td></tr><tr><td>`alpha`</td><td>Order Collection Alphabetically</td></tr><tr><td>`custom`</td><td>Order Collection Via the Builder Order</td></tr><tr><td>[Any `plex_search` Sort Option](../../files/builders/plex.md#sort-options)</td><td>Order Collection by any `plex_search` Sort Option</td></tr></table>                   |
    | `limit_anidb`                          | **Description:** Changes the Builder Limit of the AniDB Popular Collection.<br>**Default:** `30`<br>**Values:** Number greater than 0                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `style`                                | **Description:** Changes the color scheme of the collection posters.<br>**Default:** `color`<br>**Values:** `color` or `white`                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `sync_mode_<<key>>`<sup>1</sup>        | **Description:** Changes the Sync Mode of the [key's](#collection_section) collection.<br>**Default:** `sync_mode`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>                                                                                                                                                                                                                                          |
    | `sync_mode`                            | **Description:** Changes the Sync Mode for all collections in a Defaults File.<br>**Default:** `sync`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>                                                                                                                                                                                                                                                       |

    1. Each default collection has a [`key`](#collection_section) that you must replace `<<key>>` with when using 
    this Template Variable. These keys are found in the table at the top of this page.

{% include-markdown "./../templates/defaults_variables.md" end="<!--space-->" %}