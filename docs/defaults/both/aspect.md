---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Aspect Ratio", 
        "CODE_NAME": "aspect",
        "LIBRARY_TYPE": "Movie, Show", 
        "SECTION_NUMBER": "125", 
        "DESCRIPTION": "create collections with items that are based on their aspect ratio"
    }'
%}
{% include-markdown "./../templates/separator_line.md" replace='{"SEPARATOR": "Aspect Ratio"}' %}
| `1.33 - Academy Aperture`      | `1.33`      | Collection of Movies/Shows with a 1.33 aspect ratio                            |
| `1.65 - Early Widescreen`      | `1.65`      | Collection of Movies/Shows with a 1.65 aspect ratio                            |
| `1.66 - European Widescreen`   | `1.66`      | Collection of Movies/Shows with a 1.66 aspect ratio                            |
| `1.78 - Widescreen TV`         | `1.78`      | Collection of Movies/Shows with a 1.78 aspect ratio                            |
| `1.85 - American Widescreen`   | `1.85`      | Collection of Movies/Shows with a 1.85 aspect ratio                            |
| `2.2 - 70mm Frame`             | `2.2`       | Collection of Movies/Shows with a 2.2 aspect ratio                             |
| `2.35 - Anamorphic Projection` | `2.35`      | Collection of Movies/Shows with a 2.35 aspect ratio                            |
| `2.77 - Cinerama`              | `2.77`      | Collection of Movies/Shows with a 2.77 aspect ratio                            |

{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "aspect"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: aspect
            template_variables:
              use_1.65: false #(1)!
              sep_style: plum #(2)!
    ```

    1.  Do not create a "1.65 - Early Widescreen" collection
    2.  Use the plum [Separator Style](../separators.md#separator-styles)

{% include-markdown "./../templates/defaults_variables_header.md" %}
    | `exclude`                       | **Description:** Exclude these Media Outlets from creating a Dynamic Collection.<br>**Values:** List of Media Outlet Keys                                                                                                                                                                                     |
    | `limit_<<key>>`<sup>1</sup>     | **Description:** Changes the Builder Limit of the [key's](#collection_section) collection.<br>**Default:** `limit`<br>**Values:** Number Greater than 0                                                                                                                                                       |
    | `limit`                         | **Description:** Changes the Builder Limit for all collections in a Defaults File.<br>**Values:** Number Greater than 0                                                                                                                                                                                       |
    | `name_format`                   | **Description:** Changes the title format of the Dynamic Collections.<br>**Default:** `Based on a <<key_name>>`<br>**Values:** Any string with `<<key_name>>` in it.                                                                                                                                          |
    | `sort_by_<<key>>`<sup>1</sup>   | **Description:** Changes the Smart Filter Sort of the [key's](#collection_section) collection.<br>**Default:** `sort_by`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                                                                           |
    | `sort_by`                       | **Description:** Changes the Smart Filter Sort for all collections in a Defaults File.<br>**Default:** `release.desc`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                                                                              |
    | `summary_format`                | **Description:** Changes the summary format of the Dynamic Collections.<br>**Default:** `<<library_translationU>>s based on or inspired by <<translated_key_name>>s.`<br>**Values:** Any string.                                                                                                              |
    | `sync_mode_<<key>>`<sup>1</sup> | **Description:** Changes the Sync Mode of the [key's](#collection_section) collection.<br>**Default:** `sync_mode`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table> |
    | `sync_mode`                     | **Description:** Changes the Sync Mode for all collections in a Defaults File.<br>**Default:** `sync`<br>**Values:**<table class="clearTable"><tr><td>`sync`</td><td>Add and Remove Items based on Builders</td></tr><tr><td>`append`</td><td>Only Add Items based on Builders</td></tr></table>              |

    1. Each default collection has a [`key`](#collection_section) that you must replace `<<key>>` with when using 
    this Template Variable. These keys are found in the table at the top of this page.

{% include-markdown "./../templates/defaults_variables.md" %}
