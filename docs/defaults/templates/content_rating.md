{%
    include-markdown "./defaults_header.md"
    replace='{
        "COLLECTION": "COLLECTION", 
        "CODE_NAME": "CODE_NAME", 
        "LIBRARY_TYPE": "LIBRARY_TYPE", 
        "DESCRIPTION": "dynamically create collections based on the content ratings available in your library.\n\nIf you do not use the SHORT_NAME-based rating system within Plex, this file will attempt to match the ratings in your library to the respective rating system"
    }'
    end="<!--space-->"
%}
<!--rec-start-->
Recommendation: Set the Certification Country within your library's advanced settings to "PLEX_NAME".
<!--rec-end-->
{%
    include-markdown "./defaults_header.md"
    replace='{"SECTION_NUMBER": "110"}'
    start="<!--space-->"
%}
{% include-markdown "./separator_line.md" replace='{"SEPARATOR": "Ratings"}' %}
| `<<Content Rating>> Movies/Shows`<br>**Example:** `EXAMPLE_NAME` | `<<Content Rating>>`<br>**Example:** `EXAMPLE1` | Collection of Movies/Shows that have this Content Rating.                             |
| `Not Rated Movies/Shows`                                           | `other`                                        | Collection of Movies/Shows that are Unrated, Not Rated or any other uncommon Ratings. |

{% include-markdown "./defaults_mid_both.md" replace='{"CODE_NAME": "CODE_NAME"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: CODE_NAME
            template_variables:
              sep_style: stb #(1)!
              use_other: false #(2)!
              append_addons:
                EXAMPLE1: #(3)!
                  - EXAMPLE2 #(4)!
              sort_by: title.asc
    ```

    1.  Use the stb [Separator Style](../separators.md#separator-styles)
    2.  Do not create a "Not Rated Movies/Shows" collection
    3.  Defines a collection which will be called "EXAMPLE1", this does not need to already exist in your library
    4.  Adds the "EXAMPLE2" content rating to the "EXAMPLE1" addon list, "EXAMPLE2" must exist in your library if the "EXAMPLE1" content rating does not

{% include-markdown "./defaults_variables_header.md" %}
    | `addons`                      | **Description:** Overrides the [default addons dictionary](#default-values). Defines how multiple keys can be combined under a parent key. The parent key doesn't have to already exist in Plex<br>**Values:** Dictionary List of Content Ratings found in your library |
    | `append_addons`               | **Description:** Appends to the [default addons dictionary](#default-values).<br>**Values:** Dictionary List of Content Ratings found in your library                                                                                                                   |
    | `append_include`              | **Description:** Appends to the [default include list](#default-values).<br>**Values:** List of Content Ratings found in your library                                                                                                                                   |
    | `exclude`                     | **Description:** Exclude these Content Ratings from creating a Dynamic Collection.<br>**Values:** List of Content Ratings found in your library                                                                                                                         |
    | `include`                     | **Description:** Overrides the [default include list](#default-values).<br>**Values:** List of Content Ratings found in your library                                                                                                                                    |
    | `limit_<<key>>`<sup>1</sup>   | **Description:** Changes the Builder Limit of the [key's](#collection_section) collection.<br>**Default:** `limit`<br>**Values:** Number Greater than 0                                                                                                                 |
    | `limit`                       | **Description:** Changes the Builder Limit for all collections in a Defaults File.<br>**Values:** Number Greater than 0                                                                                                                                                 |
    | `name_format`                 | **Description:** Changes the title format of the Dynamic Collections.<br>**Default:** `<<key_name>> <<library_translationU>>s`<br>**Values:** Any string with `<<key_name>>` in it.                                                                                     |
    | `remove_addons`               | **Description:** Removes from the [default addons dictionary](#default-values).<br>**Values:** Dictionary List of Content Ratings found in your library                                                                                                                 |
    | `remove_include`              | **Description:** Removes from the [default include list](#default-values).<br>**Values:** List of Content Ratings found in your library                                                                                                                                 |
    | `sort_by_<<key>>`<sup>1</sup> | **Description:** Changes the Smart Filter Sort of the [key's](#collection_section) collection.<br>**Default:** `sort_by`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                                     |
    | `sort_by`                     | **Description:** Changes the Smart Filter Sort for all collections in a Defaults File.<br>**Default:** `release.desc`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                                        |
    | `summary_format`              | **Description:** Changes the summary format of the Dynamic Collections.<br>**Default:** `<<library_translationU>>s that are rated <<key_name>>.`<br>**Values:** Any string.                                                                                             |

    1. Each default collection has a [`key`](#collection_section) that you must replace `<<key>>` with when using 
    this Template Variable. These keys are found in the table at the top of this page.

{% include-markdown "./defaults_variables.md" %}
{% include-markdown "./defaults_values.md" rewrite-relative-urls=false %}