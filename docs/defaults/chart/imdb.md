---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "IMDb Charts", 
        "CODE_NAME": "imdb",
        "LIBRARY_TYPE": "Movie, Show", 
        "DESCRIPTION": "create collections based on IMDb charts",
        "SECTION_NUMBER": "020"
    }'
    replace-tags='{"space": "Recommendations: The `IMDb Lowest Rated` Collection only works with Movie Libraries."}'
%}
| `IMDb Lowest Rated` | `lowest`  | Collection of the lowest Rated Movies on IMDb.       |
| `IMDb Popular`      | `popular` | Collection of the most Popular Movies/Shows on IMDb. |
| `IMDb Top 250`      | `top`     | Collection of Top 250 Movies/Shows on IMDb.          |

{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "imdb"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: imdb
            template_variables:
              use_lowest: false #(1)!
              visible_library_top: true #(2)!
              visible_home_top: true #(3)!
              visible_shared_top: true #(4)!
    ```

    1.  Do not create the "IMDb Lowest Rated" collection
    2.  Pin the "IMDB Top 250" collection to the Recommended tab of the library
    3.  Pin the "IMDB Top 250" collection to the home screen of the server owner
    4.  Pin the "IMDB Top 250" collection to the home screen of other users of the server

{% include-markdown "./../templates/defaults_variables_header.md" exclude-tags="separator" %}
    | `collection_order_<<key>>`<sup>1</sup> | **Description:** Changes the Collection Order of the [key's](#collection_section) collection.<br>**Default:** `collection_order`<br>**Values:**<table class="clearTable"><tr><td>`release`</td><td>Order Collection by Release Dates</td></tr><tr><td>`alpha`</td><td>Order Collection Alphabetically</td></tr><tr><td>`custom`</td><td>Order Collection Via the Builder Order</td></tr><tr><td>[Any `plex_search` Sort Option](../../files/builders/plex.md#sort-options)</td><td>Order Collection by any `plex_search` Sort Option</td></tr></table> |
    | `collection_order`                     | **Description:** Changes the Collection Order for all collections in a Defaults File.<br>**Default:** `custom`<br>**Values:**<table class="clearTable"><tr><td>`release`</td><td>Order Collection by Release Dates</td></tr><tr><td>`alpha`</td><td>Order Collection Alphabetically</td></tr><tr><td>`custom`</td><td>Order Collection Via the Builder Order</td></tr><tr><td>[Any `plex_search` Sort Option](../../files/builders/plex.md#sort-options)</td><td>Order Collection by any `plex_search` Sort Option</td></tr></table>                   |
    | `style`                                | **Description:** Changes the color scheme of the collection posters.<br>**Default:** `color`<br>**Values:** `color` or `white`                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `sync_mode_<<key>>`<sup>1</sup>        | **Description:** Changes the Sync Mode of the [key's](#collection_section) collection.<br>**Default:** `sync_mode`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>                                                                                                                                                                                                                                          |
    | `sync_mode`                            | **Description:** Changes the Sync Mode for all collections in a Defaults File.<br>**Default:** `sync`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>                                                                                                                                                                                                                                                       |

    1. Each default collection has a [`key`](#collection_section) that you must replace `<<key>>` with when using 
    this Template Variable. These keys are found in the table at the top of this page.

{% include-markdown "./../templates/defaults_variables.md" end="<!--space-->" %}