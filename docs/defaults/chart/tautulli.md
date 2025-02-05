---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Tautulli Charts", 
        "CODE_NAME": "tautulli",
        "LIBRARY_TYPE": "Movie, Show", 
        "DESCRIPTION": "create collections based on Tautulli/Plex charts",
        "SECTION_NUMBER": "020"
    }'
    replace-tags='{"space": "Requirements: [Tautulli Authentication](../../config/tautulli.md)."}'
%}
| `Plex Popular` | `popular` | Collection of the most Popular Movies/Shows on Plex. |
| `Plex Watched` | `watched` | Collection of the most Watched Movies/Shows on Plex. |

{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "tautulli"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: tautulli
            template_variables:
              use_watched: false #(1)!
              list_days_popular: 7 #(2)!
              list_size_popular: 10 #(3)!
              visible_library_popular: true #(4)!
              visible_home_popular: true #(5)!
              visible_shared_popular: true #(6)!
    ```

    1.  Do not create the "Plex Watched" collection
    2.  Change "Plex Popular" to look at items from the past 7 days
    3.  Change "Plex Popular" to have a maximum of 10 items
    4.  Pin the "Plex Popular" collection to the Recommended tab of the library
    5.  Pin the "Plex Popular" collection to the home screen of the server owner
    6.  Pin the "Plex Popular" collection to the home screen of other users of the server

{% include-markdown "./../templates/defaults_variables_header.md" exclude-tags="separator" %}
    | `collection_order_<<key>>`<sup>1</sup> | **Description:** Changes the Collection Order of the [key's](#collection_section) collection.<br>**Default:** `collection_order`<br>**Values:**<table class="clearTable"><tr><td>`release`</td><td>Order Collection by Release Dates</td></tr><tr><td>`alpha`</td><td>Order Collection Alphabetically</td></tr><tr><td>`custom`</td><td>Order Collection Via the Builder Order</td></tr><tr><td>[Any `plex_search` Sort Option](../../files/builders/plex.md#sort-options)</td><td>Order Collection by any `plex_search` Sort Option</td></tr></table> |
    | `collection_order`                     | **Description:** Changes the Collection Order for all collections in a Defaults File.<br>**Default:** `custom`<br>**Values:**<table class="clearTable"><tr><td>`release`</td><td>Order Collection by Release Dates</td></tr><tr><td>`alpha`</td><td>Order Collection Alphabetically</td></tr><tr><td>`custom`</td><td>Order Collection Via the Builder Order</td></tr><tr><td>[Any `plex_search` Sort Option](../../files/builders/plex.md#sort-options)</td><td>Order Collection by any `plex_search` Sort Option</td></tr></table>                   |
    | `list_days_<<key>>`<sup>1</sup>        | **Description:** Changes the `list_days` attribute of the Builder of the [key's](#collection_section) collection.<br>**Values:** Number greater than 0                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `list_days`                            | **Description:** Changes the `list_days` attribute of the Builder for all collections in a Defaults File.<br>**Values:** Number greater than 0                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `list_size_<<key>>`<sup>1</sup>        | **Description:** Changes the `list_size` attribute of the Builder of the [key's](#collection_section) collection.<br>**Values:** Number greater than 0                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `list_size`                            | **Description:** Changes the `list_size` attribute of the Builder for all collections in a Defaults File.<br>**Values:** Number greater than 0                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `style`                                | **Description:** Changes the color scheme of the collection posters.<br>**Default:** `color`<br>**Values:** `color` or `white`                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `sync_mode_<<key>>`<sup>1</sup>        | **Description:** Changes the Sync Mode of the [key's](#collection_section) collection.<br>**Default:** `sync_mode`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>                                                                                                                                                                                                                                          |
    | `sync_mode`                            | **Description:** Changes the Sync Mode for all collections in a Defaults File.<br>**Default:** `sync`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>                                                                                                                                                                                                                                                       |

    1. Each default collection has a `key` that when calling to effect a specific collection you must replace `<<key>>` with when calling.

{% include-markdown "./../templates/defaults_variables.md" end="<!--space-->" %}