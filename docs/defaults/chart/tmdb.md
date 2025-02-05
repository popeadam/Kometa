---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "TMDb Charts", 
        "CODE_NAME": "tmdb",
        "LIBRARY_TYPE": "Movie, Show", 
        "DESCRIPTION": "create collections based on TMDb charts",
        "SECTION_NUMBER": "020"
    }'
    replace-tags='{"space": "Recommendations: The `TMDb Airing Today` and `TMDb On The Air` Collections only work with Show Libraries."}'
%}
| `TMDb Airing Today` | `airing`   | Collection of Shows Airing Today on TMDb.            |
| `TMDb On The Air`   | `air`      | Collection of Shows currently On The Air on TMDb.    |
| `TMDb Popular`      | `popular`  | Collection of the Most Popular Movies/Shows on TMDb. |
| `TMDb Top Rated`    | `top`      | Collection of the Top Rated Movies/Shows on TMDb.    |
| `TMDb Trending`     | `trending` | Collection of Trending Movies/Shows on TMDb.         |

{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "tmdb"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: tmdb
            template_variables:
              use_trending: false #(1)!
              limit_popular: 20 #(2)!
              visible_library_popular: true #(3)!
              visible_home_popular: true #(4)!
              visible_shared_popular: true #(5)!
    ```

    1.  Do not create the "TMDb Trending" collection
    2.  Change "TMDb Popular" to have a maximum of 20 items
    3.  Pin the "TMDb Popular" collection to the Recommended tab of the library
    4.  Pin the "TMDb Popular" collection to the home screen of the server owner
    5.  Pin the "TMDb Popular" collection to the home screen of other users of the server

{% include-markdown "./../templates/defaults_variables_header.md" exclude-tags="separator" %}
    | `collection_order_<<key>>`<sup>1</sup> | **Description:** Changes the Collection Order of the [key's](#collection_section) collection.<br>**Default:** `collection_order`<br>**Values:**<table class="clearTable"><tr><td>`release`</td><td>Order Collection by Release Dates</td></tr><tr><td>`alpha`</td><td>Order Collection Alphabetically</td></tr><tr><td>`custom`</td><td>Order Collection Via the Builder Order</td></tr><tr><td>[Any `plex_search` Sort Option](../../files/builders/plex.md#sort-options)</td><td>Order Collection by any `plex_search` Sort Option</td></tr></table> |
    | `collection_order`                     | **Description:** Changes the Collection Order for all collections in a Defaults File.<br>**Default:** `custom`<br>**Values:**<table class="clearTable"><tr><td>`release`</td><td>Order Collection by Release Dates</td></tr><tr><td>`alpha`</td><td>Order Collection Alphabetically</td></tr><tr><td>`custom`</td><td>Order Collection Via the Builder Order</td></tr><tr><td>[Any `plex_search` Sort Option](../../files/builders/plex.md#sort-options)</td><td>Order Collection by any `plex_search` Sort Option</td></tr></table>                   |
    | `limit_<<key>>`<sup>1</sup>            | **Description:** Changes the Builder Limit of the [key's](#collection_section) collection.<br>**Default:** `limit`<br>**Values:** Number greater than 0                                                                                                                                                                                                                                                                                                                                                                                                |
    | `limit`                                | **Description:** Changes the Builder Limit for all collections in a Defaults File.<br>**Default:** `100`<br>**Values:** Number greater than 0                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `style`                                | **Description:** Changes the color scheme of the collection posters.<br>**Default:** `color`<br>**Values:** `color` or `white`                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `sync_mode_<<key>>`<sup>1</sup>        | **Description:** Changes the Sync Mode of the [key's](#collection_section) collection.<br>**Default:** `sync_mode`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>                                                                                                                                                                                                                                          |
    | `sync_mode`                            | **Description:** Changes the Sync Mode for all collections in a Defaults File.<br>**Default:** `sync`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>                                                                                                                                                                                                                                                       |

    1. Each default collection has a [`key`](#collection_section) that you must replace `<<key>>` with when using 
    this Template Variable. These keys are found in the table at the top of this page.

{% include-markdown "./../templates/defaults_variables.md" end="<!--space-->" %}