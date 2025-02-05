---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Trakt Charts", 
        "CODE_NAME": "trakt",
        "LIBRARY_TYPE": "Movie, Show", 
        "DESCRIPTION": "create collections based on Trakt charts",
        "SECTION_NUMBER": "020"
    }'
    replace-tags='{"space": "Requirements: [Trakt Authentication](../../config/trakt.md)."}'
%}
| `Trakt Collected`   | `collected`   | Collection of the Most Collected Movies/Shows on Trakt. |
| `Trakt Popular`     | `popular`     | Collection of the Most Popular Movies/Shows on Trakt.   |
| `Trakt Recommended` | `recommended` | Collection of Recommended Movies/Shows on Trakt.        |
| `Trakt Trending`    | `trending`    | Collection of Trending Movies/Shows on Trakt.           |
| `Trakt Watched`     | `watched`     | Collection of the Most Watched Movies/Shows on Trakt.   |

{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "trakt"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: trakt
            template_variables:
              use_collected: false #(1)!
              use_recommended: false #(2)!
              limit: 20 #(3)!
              visible_library_popular: true #(4)!
              visible_home_popular: true #(5)!
              visible_shared_popular: true #(6)!
    ```

    1.  Do not create the "Trakt Collected" collection
    2.  Do not create the "Trakt Recommended" collection
    3.  Change all collections built by this file to have a maximum of 20 items
    4.  Pin the "Trakt Popular" collection to the Recommended tab of the library
    5.  Pin the "Trakt Popular" collection to the home screen of the server owner
    6.  Pin the "Trakt Popular" collection to the home screen of other users of the server

{% include-markdown "./../templates/defaults_variables_header.md" exclude-tags="separator" %}
    | `collection_order_<<key>>`<sup>1</sup> | **Description:** Changes the Collection Order of the [key's](#collection_section) collection.<br>**Default:** `collection_order`<br>**Values:**<table class="clearTable"><tr><td>`release`</td><td>Order Collection by Release Dates</td></tr><tr><td>`alpha`</td><td>Order Collection Alphabetically</td></tr><tr><td>`custom`</td><td>Order Collection Via the Builder Order</td></tr><tr><td>[Any `plex_search` Sort Option](../../files/builders/plex.md#sort-options)</td><td>Order Collection by any `plex_search` Sort Option</td></tr></table> |
    | `collection_order`                     | **Description:** Changes the Collection Order for all collections in a Defaults File.<br>**Default:** `custom`<br>**Values:**<table class="clearTable"><tr><td>`release`</td><td>Order Collection by Release Dates</td></tr><tr><td>`alpha`</td><td>Order Collection Alphabetically</td></tr><tr><td>`custom`</td><td>Order Collection Via the Builder Order</td></tr><tr><td>[Any `plex_search` Sort Option](../../files/builders/plex.md#sort-options)</td><td>Order Collection by any `plex_search` Sort Option</td></tr></table>                   |
    | `limit_<<key>>`<sup>1</sup>            | **Description:** Changes the Builder Limit of the [key's](#collection_section) collection.<br>**Default:** `limit`<br>**Values:** Number Greater than 0                                                                                                                                                                                                                                                                                                                                                                                                |
    | `limit`                                | **Description:** Changes the Builder Limit for all collections in a Defaults File.<br>**Default:** `100`<br>**Values:** Number Greater than 0                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `style`                                | **Description:** Changes the color scheme of the collection posters.<br>**Default:** `color`<br>**Values:** `color` or `white`                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `sync_mode_<<key>>`<sup>1</sup>        | **Description:** Changes the Sync Mode of the [key's](#collection_section) collection.<br>**Default:** `sync_mode`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>                                                                                                                                                                                                                                          |
    | `sync_mode`                            | **Description:** Changes the Sync Mode for all collections in a Defaults File.<br>**Default:** `sync`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>                                                                                                                                                                                                                                                       |

    1. Each default collection has a `key` that when calling to effect a specific collection you must replace `<<key>>` with when calling.

{% include-markdown "./../templates/defaults_variables.md" end="<!--space-->" %}
