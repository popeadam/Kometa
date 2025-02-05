---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "US Content Rating", 
        "CODE_NAME": "content_rating_us",
        "DESCRIPTION": "dynamically create collections based on the content ratings available in your library"
    }'
    end="<!--before-image-->"
%}

If you do not use the US-based rating system within Plex, this file will attempt to match the ratings in your library to
the respective rating system.

**[This file has a Movie Library Counterpart.](../movie/content_rating_us.md)**

![](../images/showcontent_rating_us.png)

{%
    include-markdown "./../templates/defaults_header.md"
    replace='{"LIBRARY_TYPE": "Show"}'
    start="<!--after-image-->"
    end="<!--space-->"
%}

Recommendation: Set the Certification Country within your library's advanced settings to "United States".

{%
    include-markdown "./../templates/defaults_header.md"
    replace='{"SECTION_NUMBER": "110"}'
    start="<!--space-->"
%}
{% include-markdown "./../templates/separator_line.md" replace='{"SEPARATOR": "Ratings"}' %}
| `<<Content Rating>> Shows`<br>**Example:** `TV-14 Shows` | `<<Content Rating>>`<br>**Example:** `TV-14` | Collection of Shows that have this Content Rating.                             |
| `Not Rated Shows`                                        | `other`                                      | Collection of Shows that are Unrated, Not Rated or any other uncommon Ratings. |

{% include-markdown "./../templates/defaults_mid_show.md" replace='{"CODE_NAME": "content_rating_us"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: content_rating_us
            template_variables:
              sep_style: blue #(1)!
              use_other: false #(2)!
              append_addons:
                R: #(3)!
                  - "de/18" #(4)!
              sort_by: title.asc
    ```

    1.  Use the blue [Separator Style](../separators.md#separator-styles)
    2.  Do not create a "Not Rated Movies" collection
    3.  Defines a collection which will be called "R", this does not need to already exist in your library
    4.  Adds the "de/18" content rating to the "R" addon list, "de/18" must exist in your library if the "R" content rating does not

{% include-markdown "./../templates/defaults_variables_header.md" %}
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

    1. Each default collection has a `key` that when calling to effect a specific collection you must replace `<<key>>` with when calling.

{% include-markdown "./../templates/defaults_variables.md" %}
{% include-markdown "./../templates/defaults_values.md" rewrite-relative-urls=false %}