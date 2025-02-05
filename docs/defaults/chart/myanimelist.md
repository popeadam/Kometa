---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "MyAnimeList Charts", 
        "CODE_NAME": "myanimelist",
        "LIBRARY_TYPE": "Movie, Show", 
        "SECTION_NUMBER": "020", 
        "DESCRIPTION": "create collections based on MyAnimeList charts"
    }'
%}
| `MyAnimeList Favorited`  | `favorited` | Collection of most Favorited Anime on MyAnimeList.      |
| `MyAnimeList Popular`    | `popular`   | Collection of the most Popular Anime on MyAnimeList.    |
| `MyAnimeList Season`     | `season`    | Collection of the Current Seasons Anime on MyAnimeList. |
| `MyAnimeList Top Airing` | `airing`    | Collection of the Top Rated Airing on MyAnimeList.      |
| `MyAnimeList Top Rated`  | `top`       | Collection of the Top Rated Anime on MyAnimeList.       |

{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "myanimelist"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: myanimelist
            template_variables:
              use_season: false #(1)!
              order_popular: 01 #(2)!
              limit_popular: 20 #(3)!
              visible_library_popular: true #(4)!
              visible_home_popular: true #(5)!
              visible_shared_popular: true #(6)!
    ```

    1.  Do not create the "MyAnimeList Season" collection
    2.  Change the order of "MyAnimeList Popular" to appear before all other collections created by this file
    3.  Limit the "MyAnimeList Popular" collection to 20 items.
    4.  Pin the "MyAnimeList Popular" collection to the Recommended tab of the library
    5.  Pin the "MyAnimeList Popular" collection to the home screen of the server owner
    6.  Pin the "MyAnimeList Popular" collection to the home screen of other users of the server

{% include-markdown "./../templates/defaults_variables_header.md" exclude-tags="separator" %}
    | `collection_order_<<key>>`<sup>1</sup> | **Description:** Changes the Collection Order of the [key's](#collection_section) collection.<br>**Default:** `collection_order`<br>**Values:**<table class="clearTable"><tr><td>`release`</td><td>Order Collection by Release Dates</td></tr><tr><td>`alpha`</td><td>Order Collection Alphabetically</td></tr><tr><td>`custom`</td><td>Order Collection Via the Builder Order</td></tr><tr><td>[Any `plex_search` Sort Option](../../files/builders/plex.md#sort-options)</td><td>Order Collection by any `plex_search` Sort Option</td></tr></table> |
    | `collection_order`                     | **Description:** Changes the Collection Order for all collections in a Defaults File.<br>**Default:** `custom`<br>**Values:**<table class="clearTable"><tr><td>`release`</td><td>Order Collection by Release Dates</td></tr><tr><td>`alpha`</td><td>Order Collection Alphabetically</td></tr><tr><td>`custom`</td><td>Order Collection Via the Builder Order</td></tr><tr><td>[Any `plex_search` Sort Option](../../files/builders/plex.md#sort-options)</td><td>Order Collection by any `plex_search` Sort Option</td></tr></table>                   |
    | `limit_<<key>>`<sup>1</sup>            | **Description:** Changes the Builder Limit of the [key's](#collection_section) collection.<br>**Default:** `limit`<br>**Values:** Number greater than 0                                                                                                                                                                                                                                                                                                                                                                                                |
    | `limit`                                | **Description:** Changes the Builder Limit for all collections in a Defaults File.<br>**Default:** `100`<br>**Values:** Number greater than 0                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `starting_only`                        | **Description:** Changes the season collection to only use anime listed under the new section on [MAL Seasons](https://myanimelist.net/anime/season/)<br>**Default:** `False`<br>**Values:** `True` or `False`                                                                                                                                                                                                                                                                                                                                         |
    | `style`                                | **Description:** Changes the color scheme of the collection posters.<br>**Default:** `color`<br>**Values:** `color` or `white`                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `sync_mode_<<key>>`<sup>1</sup>        | **Description:** Changes the Sync Mode of the [key's](#collection_section) collection.<br>**Default:** `sync_mode`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>                                                                                                                                                                                                                                          |
    | `sync_mode`                            | **Description:** Changes the Sync Mode for all collections in a Defaults File.<br>**Default:** `sync`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>                                                                                                                                                                                                                                                       |

    1. Each default collection has a [`key`](#collection_section) that you must replace `<<key>>` with when using 
    this Template Variable. These keys are found in the table at the top of this page.

{% include-markdown "./../templates/defaults_variables.md" end="<!--space-->" %}