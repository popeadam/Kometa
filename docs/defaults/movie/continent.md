---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Continent", 
        "CODE_NAME": "continent",
        "DESCRIPTION": "dynamically create collections based on the countries within your library. The collection aims to be inclusive, with all 230 countries incorporated into seven continents"
    }'
    end="<!--before-image-->"
%}

**[This file has a Show Library Counterpart.](../show/continent.md)**

{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "CODE_NAME": "continent",
        "LIBRARY_TYPE": "Movie",
        "SECTION_NUMBER": "082"
    }'
    start="<!--before-image-->"
%}
{% include-markdown "./../templates/separator_line.md" replace='{"SEPARATOR": "Continent"}' %}
| `<<Continent>>`<br>**Example:** `South America` | `<<Continent>>`<br>**Example:** `South America` | Collection of Movies that have this Continent.              |
| `Other Continents`                              | `other`                                         | Collection of Movies that are in other uncommon Continents. |

{% include-markdown "./../templates/location_style.md" replace='{"CODE_NAME": "continent"}' %}
{% include-markdown "./../templates/defaults_mid_movie.md" replace='{"CODE_NAME": "continent"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: continent
            template_variables:
              use_other: false #(1)!
              use_separator: false #(2)!
              style: color #(3)!
              exclude:
                - Europe #(4)!
              sort_by: title.asc
    ```

    1.  Do not create the "Other Continents" collection
    2.  Do not create a "Continent Collections" separator
    3.  Set the [Color Style](#color-style)
    4.  Exclude "Europe" from the list of collections that are created

{% include-markdown "./../templates/defaults_variables_header.md" %}
    | `addons`                      | **Description:** Overrides the [default addons dictionary](#default-values). Defines how multiple keys can be combined under a parent key. The parent key doesn't have to already exist in Plex<br>**Values:** Dictionary List of Countries found in your library |
    | `append_addons`               | **Description:** Appends to the [default addons dictionary](#default-values).<br>**Values:** Dictionary List of Countries found in your library                                                                                                                   |
    | `append_include`              | **Description:** Appends to the [default include list](#default-values).<br>**Values:** List of Countries found in your library                                                                                                                                   |
    | `exclude`                     | **Description:** Exclude these Countries from creating a Dynamic Collection.<br>**Values:** List of Countries found in your library                                                                                                                               |
    | `include`                     | **Description:** Overrides the [default include list](#default-values).<br>**Values:** List of Countries found in your library                                                                                                                                    |
    | `key_name_override`           | **Description:** Overrides the [default key_name_override dictionary](#default-values).<br>**Values:** Dictionary with `key: new_key_name` entries                                                                                                                |
    | `limit_<<key>>`<sup>1</sup>   | **Description:** Changes the Builder Limit of the [key's](#collection_section) collection.<br>**Default:** `limit`<br>**Values:** Number Greater than 0                                                                                                           |
    | `limit`                       | **Description:** Changes the Builder Limit for all collections in a Defaults File.<br>**Values:** Number Greater than 0                                                                                                                                           |
    | `name_format`                 | **Description:** Changes the title format of the Dynamic Collections.<br>**Default:** `<<key_name>>`<br>**Values:** Any string with `<<key_name>>` in it.                                                                                                         |
    | `remove_addons`               | **Description:** Removes from the [default addons dictionary](#default-values).<br>**Values:** Dictionary List of Countries found in your library                                                                                                                 |
    | `remove_include`              | **Description:** Removes from the [default include list](#default-values).<br>**Values:** List of Countries found in your library                                                                                                                                 |
    | `sort_by_<<key>>`<sup>1</sup> | **Description:** Changes the Smart Filter Sort of the [key's](#collection_section) collection.<br>**Default:** `sort_by`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                               |
    | `sort_by`                     | **Description:** Changes the Smart Filter Sort for all collections in a Defaults File.<br>**Default:** `release.desc`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                                  |
    | `style`                       | **Description:** Controls the visual theme of the collections created<table class="clearTable"><tr><th>Values:</th></tr><tr><td><code>white</code></td><td>White Theme</td></tr><tr><td><code>color</code></td><td>Color Theme</td></tr></table>                  |
    | `summary_format`              | **Description:** Changes the summary format of the Dynamic Collections.<br>**Default:** `<<library_translationU>>s filmed in <<key_name>>.`<br>**Values:** Any string.                                                                                            |

    1. Each default collection has a [`key`](#collection_section) that you must replace `<<key>>` with when using 
    this Template Variable. These keys are found in the table at the top of this page.

{% include-markdown "./../templates/defaults_variables.md" %}
{% include-markdown "./../templates/defaults_values.md" rewrite-relative-urls=false %}