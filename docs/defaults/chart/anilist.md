---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Anilist Charts", 
        "CODE_NAME": "anilist",
        "LIBRARY_TYPE": "Movie, Show", 
        "SECTION_NUMBER": "020", 
        "DESCRIPTION": "create collections based on Anilist charts"
    }'
%}
| `AniList Popular`   | `popular`  | Collection of the most Popular Anime on AniList.     |
| `AniList Season`    | `season`   | Collection of the Current Season's Anime on AniList. |
| `AniList Top Rated` | `top`      | Collection of the Top Rated Anime on AniList.        |
| `AniList Trending`  | `trending` | Collection of the Trending Anime on AniList.         |

{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "anilist"}' %}    
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: anilist
            template_variables:
              use_season: false #(1)!
              order_top: 01 #(2)!
              summary_top: "Top 10 Rated movies on AniList" #(3)!
              limit_top: 10 #(4)!
              visible_library_popular: true #(5)!
              visible_home_popular: true #(6)!
              visible_shared_popular: true #(7)!
    ```

    1.  Do not create the "AniList Season" collection
    2.  Change the order of "AniList Top Rated" to appear before other collections created by this file
    3.  Amend the summary of the "AniList Top Rated" collection
    4.  Only allow a maximum of 10 items to appear in the "AniList Top Rated" collection
    5.  Pin the "AniList Popular" collection to the Recommended tab of the library
    6.  Pin the "AniList Popular" collection to the home screen of the server owner
    7.  Pin the "AniList Popular" collection to the home screen of other users of the server

end="<!--space-->"
* **File-Specific Template Variables** are variables available specifically for this Kometa Defaults File.

* **Shared Template Variables** are additional variables shared across the Kometa Defaults.

=== "File-Specific Template Variables"

    | Variable                               | Description & Values                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | :------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | `collection_order_<<key>>`<sup>1</sup> | **Description:** Changes the Collection Order of the [key's](#collection_section) collection.<br>**Default:** `collection_order`<br>**Values:**<table class="clearTable"><tr><td>`release`</td><td>Order Collection by Release Dates</td></tr><tr><td>`alpha`</td><td>Order Collection Alphabetically</td></tr><tr><td>`custom`</td><td>Order Collection Via the Builder Order</td></tr><tr><td>[Any `plex_search` Sort Option](../../files/builders/plex.md#sort-options)</td><td>Order Collection by any `plex_search` Sort Option</td></tr></table> |
    | `collection_order`                     | **Description:** Changes the Collection Order for all collections in a Defaults File.<br>**Default:** `custom`<br>**Values:**<table class="clearTable"><tr><td>`release`</td><td>Order Collection by Release Dates</td></tr><tr><td>`alpha`</td><td>Order Collection Alphabetically</td></tr><tr><td>`custom`</td><td>Order Collection Via the Builder Order</td></tr><tr><td>[Any `plex_search` Sort Option](../../files/builders/plex.md#sort-options)</td><td>Order Collection by any `plex_search` Sort Option</td></tr></table>                   |
    | `limit_<<key>>`<sup>1</sup>            | **Description:** Changes the number of items in a collection of the [key's](#collection_section) collection.<br>**Default:** `limit`<br>**Values:** Number greater than 0                                                                                                                                                                                                                                                                                                                                                                              |
    | `limit`                                | **Description:** Changes the number of items in a collection for all collections in a Defaults File.<br>**Default:** `100`<br>**Values:** Number greater than 0                                                                                                                                                                                                                                                                                                                                                                                        |
    | `style`                                | **Description:** Changes the color scheme of the collection posters.<br>**Default:** `color`<br>**Values:** `color` or `white`                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `sync_mode_<<key>>`<sup>1</sup>        | **Description:** Changes the Sync Mode of the [key's](#collection_section) collection.<br>**Default:** `sync_mode`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>                                                                                                                                                                                                                                          |
    | `sync_mode`                            | **Description:** Changes the Sync Mode for all collections in a Defaults File.<br>**Default:** `sync`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>                                                                                                                                                                                                                                                       |

    1. Each default collection has a [`key`](#collection_section) that you must replace `<<key>>` with when using 
    this Template Variable. These keys are found in the table at the top of this page.

{%
  include-markdown "./../templates/defaults_variables.md"
  end="<!--space-->"
%}
