---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Audio Language", 
        "CODE_NAME": "audio_language",
        "LIBRARY_TYPE": "Movie, Show", 
        "SECTION_NUMBER": "090", 
        "DESCRIPTION": "dynamically create collections based on the audio languages available in your library"
    }'
%}
{% include-markdown "./../templates/separator_line.md" replace='{"SEPARATOR": "Audio Language"}' %}
| `<<Audio Language>> Audio`<br>**Example:** `Japanese` | `<<ISO 639-1 Code>>`<br>**Example:** `ja` <br>`<<ISO 639-2 Code>>`<br>**Example:** `myn` | Collection of Movies/Shows that have this Audio Language. |
| `Other Audio` | `other` | Collection of Movies/Shows that are less common Languages. |

{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "audio_language"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: audio_language
            template_variables:
              use_other: false #(1)!
              use_separator: false #(2)!
              exclude:
                - fr  #(3)!
              sort_by: title.asc
    ```

    1.  Do not create an "Other Audio" collection
    2.  Do not create an "Audio Language Collections" separator
    3.  Exclude "French" from having an Audio Collection

{% include-markdown "./../templates/defaults_variables_header.md" %}
    | `append_include`              | **Description:** Appends to the [default include list](#default-values)<br>**Values:** List of [ISO 639-1 codes](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)<br>**Values:** List of [ISO 639-2 codes](https://en.wikipedia.org/wiki/List_of_ISO_639-2_codes)            |
    | `exclude`                     | **Description:** Exclude these Audio Languages from creating a Dynamic Collection.<br>**Values:** List of [ISO 639-1 codes](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)<br>**Values:** List of [ISO 639-2 codes](https://en.wikipedia.org/wiki/List_of_ISO_639-2_codes) |
    | `include`                     | **Description:** Overrides the [default include list](#default-values)<br>**Values:** List of [ISO 639-1 codes](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)<br>**Values:** List of [ISO 639-2 codes](https://en.wikipedia.org/wiki/List_of_ISO_639-2_codes)             |
    | `key_name_override`           | **Description:** Overrides the [default key_name_override dictionary](#default-values).<br>**Values:** Dictionary with `key: new_key_name` entries                                                                                                                                 |
    | `limit_<<key>>`<sup>1</sup>   | **Description:** Changes the Builder Limit of the [key's](#collection_section) collection.<br>**Default:** `limit`<br>**Values:** Number Greater than 0                                                                                                                            |
    | `limit`                       | **Description:** Changes the Builder Limit for all collections in a Defaults File.<br>**Values:** Number Greater than 0                                                                                                                                                            |
    | `name_format`                 | **Description:** Changes the title format of the Dynamic Collections.<br>**Default:** `<<key_name>> Audio`<br>**Values:** Any string with `<<key_name>>` in it.                                                                                                                    |
    | `remove_include`              | **Description:** Removes from the [default include list](#default-values)<br>**Values:** List of [ISO 639-1 codes](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)<br>**Values:** List of [ISO 639-2 codes](https://en.wikipedia.org/wiki/List_of_ISO_639-2_codes)          |
    | `sort_by_<<key>>`<sup>1</sup> | **Description:** Changes the Smart Filter Sort of the [key's](#collection_section) collection.<br>**Default:** `sort_by`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                                                |
    | `sort_by`                     | **Description:** Changes the Smart Filter Sort for all collections in a Defaults File.<br>**Default:** `release.desc`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                                                   |
    | `summary_format`              | **Description:** Changes the summary format of the Dynamic Collections.<br>**Default:** `<<library_translationU>>s filmed in the <<key_name>> Language.`<br>**Values:** Any string.                                                                                                |

    1. Each default collection has a [`key`](#collection_section) that you must replace `<<key>>` with when using 
    this Template Variable. These keys are found in the table at the top of this page.

{% include-markdown "./../templates/defaults_variables.md" %}
{% include-markdown "./../templates/defaults_values.md" rewrite-relative-urls=false %}
