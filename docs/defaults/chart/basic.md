---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Basic Charts", 
        "CODE_NAME": "basic",
        "LIBRARY_TYPE": "Movie, Show", 
        "SECTION_NUMBER": "010", 
        "DESCRIPTION": "create collections based on recently released media in your library"
    }'
%}
| `New Episodes`   | `episodes` | Collection of Episodes released in the last 7 days.            |
| `Newly Released` | `released` | Collection of Movies or TV Shows released in the last 90 days. |

{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "basic"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: basic
            template_variables:
              in_the_last_episodes: 14 #(1)!
              visible_library_released: true #(2)!
              visible_home_released: true #(3)!
              visible_shared_released: true #(4)!
    ```

    1.  Change the Smart Filter to look at episodes in the last 14 days.
    2.  Pin the "Newly Released" collection to the Recommended tab of the library
    3.  Pin the "Newly Released" collection to the home screen of the server owner
    4.  Pin the "Newly Released" collection to the home screen of other users of the server

{% include-markdown "./../templates/defaults_variables_header.md" exclude-tags="separator" %}
    | `in_the_last_<<key>>`<sup>1</sup> | **Description:** Changes how far back the Smart Filter looks.<table class="clearTable"><tr><td>**Default:**</td></tr><tr><td>`released`</td><td>`90`</td></tr><tr><td>`episodes`</td><td>`7`</td></tr></table>**Values:** Number greater than 0 |
    | `limit_<<key>>`<sup>1</sup>       | **Description:** Changes the Smart Filter Limit of the [key's](#collection_section) collection.<br>**Default:** `limit`<br>**Values:** Number greater than 0                                                                                    |
    | `limit`                           | **Description:** Changes the Smart Filter Limit for all collections in a Defaults File.<br>**Values:** Number greater than 0                                                                                                                    |
    | `sort_by_<<key>>`<sup>1</sup>     | **Description:** Changes the Smart Filter Sort of the [key's](#collection_section) collection.<br>**Default:** `sort_by`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                             |
    | `sort_by`                         | **Description:** Changes the Smart Filter Sort for all collections in a Defaults File.<br>**Default:** `release.desc`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                |
    | `style`                           | **Description:** Changes the color scheme of the collection posters.<br>**Default:** `color`<br>**Values:** `color` or `white`                                                                                                                  |

    1. Each default collection has a [`key`](#collection_section) that you must replace `<<key>>` with when using 
    this Template Variable. These keys are found in the table at the top of this page.

{% include-markdown "./../templates/defaults_variables.md" end="<!--space-->" %}