---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Genre", 
        "CODE_NAME": "genre",
        "DESCRIPTION": "dynamically create collections based on the genres available in your library"
    }'
    end="<!--before-image-->"
%}

This file also merges similarly named genres (such as "Sci-Fi", "SciFi" and "Sci-Fi & Fantasy") into one ("Science Fiction").

{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "CODE_NAME": "genre",
        "LIBRARY_TYPE": "Movie, Show", 
        "SECTION_NUMBER": "060"
    }'
    start="<!--before-image-->"
%}
{% include-markdown "./../templates/separator_line.md" replace='{"SEPARATOR": "Genre"}' %}
| `<<Genre>> Movies/Shows`<br>**Example:** `Action Movies` | `<<Genre>>`<br>**Example:** `Action` | Collection of Movies/Shows that have this Genre. |

{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "genre"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: genre
            template_variables:
              sep_style: red #(1)!
              exclude:
                - Politics #(2)!
                - News #(3)!
              append_addons:
                Horror: #(4)!
                  - Thriller #(5)! # Adds all thriller items to the Horror collection
    ```

    1.  Use the red [Separator Style](../separators.md#separator-styles)
    2.  Do not create a "Politics" collection, and do not include it in any other collections that it may be in as part of an "include"
    3.  Do not create a "News" collection, and do not include it in any other collections that it may be in as part of an "include"
    4.  Create a "Horror" collection, this genre does not need to exist in your library
    5.  Include the "Thriller" genre in the "Horror" collection, the "Thriller" genre must exist in your library if the "Horror" genre does not

{% include-markdown "./../templates/defaults_variables_header.md" %}
    | `addons`                      | **Description:** Overrides the [default addons dictionary](#default-values). Defines how multiple keys can be combined under a parent key. The parent key doesn't have to already exist in Plex<br>**Values:** Dictionary List of Genres found in your library |
    | `append_addons`               | **Description:** Appends to the [default addons dictionary](#default-values).<br>**Values:** Dictionary List of Genres found in your library                                                                                                                   |
    | `exclude`                     | **Description:** Exclude these Genres from creating a Dynamic Collection.<br>**Values:** List of Genres found in your library                                                                                                                                  |
    | `limit_<<key>>`<sup>1</sup>   | **Description:** Changes the Builder Limit of the [key's](#collection_section) collection.<br>**Default:** `limit`<br>**Values:** Number Greater than 0                                                                                                        |
    | `limit`                       | **Description:** Changes the Builder Limit for all collections in a Defaults File.<br>**Values:** Number Greater than 0                                                                                                                                        |
    | `name_format`                 | **Description:** Changes the title format of the Dynamic Collections.<br>**Default:** `<<key_name>> <<library_translationU>>s`<br>**Values:** Any string with `<<key_name>>` in it.                                                                            |
    | `remove_addons`               | **Description:** Removes from the [default addons dictionary](#default-values).<br>**Values:** Dictionary List of Genres found in your library                                                                                                                 |
    | `sort_by_<<key>>`<sup>1</sup> | **Description:** Changes the Smart Filter Sort of the [key's](#collection_section) collection.<br>**Default:** `sort_by`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                            |
    | `sort_by`                     | **Description:** Changes the Smart Filter Sort for all collections in a Defaults File.<br>**Default:** `release.desc`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                               |
    | `summary_format`              | **Description:** Changes the summary format of the Dynamic Collections.<br>**Default:** `<<library_translationU>>s that have the genre <<key_name>>.`<br>**Values:** Any string.                                                                               |

    1. Each default collection has a [`key`](#collection_section) that you must replace `<<key>>` with when using 
    this Template Variable. These keys are found in the table at the top of this page.

{% include-markdown "./../templates/defaults_variables.md" %}
{% include-markdown "./../templates/defaults_values.md" rewrite-relative-urls=false %}