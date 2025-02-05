---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Studio", 
        "CODE_NAME": "studio",
        "DESCRIPTION": "dynamically create collections based on the studios available in your library"
    }'
    end="<!--before-image-->"
%}

This file also merges similarly named studios (such as "20th Century Fox" and "20th Century Animation") into one ("20th Century Studios")

{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "CODE_NAME": "studio",
        "LIBRARY_TYPE": "Movie, Show", 
        "SECTION_NUMBER": "070"
    }'
    start="<!--before-image-->"
%}
{% include-markdown "./../templates/separator_line.md" replace='{"SEPARATOR": "Studio"}' %}
| `<<Studio>>`<br>**Example:** `Blumhouse Productions` | `<<Studio>>`<br>**Example:** `Blumhouse Productions` | Collection of Movies/Shows that have this Studio. |

{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "studio"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: studio
            template_variables:
              append_include:
                - Big Bull Productions #(1)!
              sort_by: title.asc
              collection_mode: show_items #(2)!
              sep_style: gray #(3)!
    ```

    1.  add "Big Bull Productions" to the list of items that should be included in the Collection list
    2.  Show these collections and their items within the "Library" tab
    3.  Use the gray [Separator Style](../separators.md#separator-styles)

{% include-markdown "./../templates/defaults_variables_header.md" %}
    | `addons`                      | **Description:** Overrides the [default addons dictionary](#default-values). Defines how multiple keys can be combined under a parent key. The parent key doesn't have to already exist in Plex<br>**Values:** Dictionary List of Studios found in your library |
    | `append_addons`               | **Description:** Appends to the [default addons dictionary](#default-values).<br>**Values:** Dictionary List of Studios found in your library                                                                                                                   |
    | `append_include`              | **Description:** Appends to the [default include list](#default-values).<br>**Values:** List of Studios found in your library                                                                                                                                   |
    | `exclude`                     | **Description:** Exclude these Studios from creating a Dynamic Collection.<br>**Values:** List of Studios found in your library                                                                                                                                 |
    | `include`                     | **Description:** Overrides the [default include list](#default-values).<br>**Values:** List of Studios found in your library                                                                                                                                    |
    | `limit_<<key>>`<sup>1</sup>   | **Description:** Changes the Builder Limit of the [key's](#collection_section) collection.<br>**Default:** `limit`<br>**Values:** Number Greater than 0                                                                                                         |
    | `limit`                       | **Description:** Changes the Builder Limit for all collections in a Defaults File.<br>**Values:** Number Greater than 0                                                                                                                                         |
    | `name_format`                 | **Description:** Changes the title format of the Dynamic Collections.<br>**Default:** `<<key_name>> <<library_translationU>>s`<br>**Values:** Any string with `<<key_name>>` in it.                                                                             |
    | `remove_addons`               | **Description:** Removes from the [default addons dictionary](#default-values).<br>**Values:** Dictionary List of Studios found in your library                                                                                                                 |
    | `remove_include`              | **Description:** Removes from the [default include list](#default-values).<br>**Values:** List of Studios found in your library                                                                                                                                 |
    | `sort_by_<<key>>`<sup>1</sup> | **Description:** Changes the Smart Filter Sort of the [key's](#collection_section) collection.<br>**Default:** `sort_by`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                             |
    | `sort_by`                     | **Description:** Changes the Smart Filter Sort for all collections in a Defaults File.<br>**Default:** `release.desc`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                                |
    | `summary_format`              | **Description:** Changes the summary format of the Dynamic Collections.<br>**Default:** `<<library_translationU>>s that have the resolution <<key_name>>.`<br>**Values:** Any string.                                                                           |

    1. Each default collection has a [`key`](#collection_section) that you must replace `<<key>>` with when using 
    this Template Variable. These keys are found in the table at the top of this page.

{% include-markdown "./../templates/defaults_variables.md" %}
{% include-markdown "./../templates/defaults_values.md" rewrite-relative-urls=false %}