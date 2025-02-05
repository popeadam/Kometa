---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Resolution", 
        "CODE_NAME": "resolution",
        "LIBRARY_TYPE": "Movie, Show", 
        "SECTION_NUMBER": "120", 
        "DESCRIPTION": "dynamically create collections based on the resolutions available in your library"
    }'
%}
{% include-markdown "./../templates/separator_line.md" replace='{"SEPARATOR": "Resolution"}' %}
| `<<Resolution>> Movies/Shows`<br>**Example:** `1080p Movies` | `<<Number>>`<br>**Example:** `1080` | Collection of Movies/Shows that have this Resolution. |

### Standards Style

Below is a screenshot of the alternative Standards (`standards`) style which can be set via the `style` template 
variable.

Standards Style takes the base resolutions ("4K" and "720p") and turns them into the commonly-known standards name 
("Ultra HD" and "HD Ready")

![](../images/resolution_standards.png)

{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "resolution"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: resolution
            template_variables:
              sep_style: green #(1)!
              exclude:
                - sd #(2)!
              sort_by: title.asc
    ```

    1.  Use the green [Separator Style](../separators.md#separator-styles)
    2.  Do not use the "sd" resolution as part of the "480p Movies/Shows" Collections

{% include-markdown "./../templates/defaults_variables_header.md" %}
    | `addons`                      | **Description:** Overrides the [default addons dictionary](#default-values). Defines how multiple keys can be combined under a parent key. The parent key doesn't have to already exist in Plex<br>**Values:** Dictionary List of Resolutions found in your library |
    | `append_addons`               | **Description:** Appends to the [default addons dictionary](#default-values).<br>**Values:** Dictionary List of Resolutions found in your library                                                                                                                   |
    | `append_include`              | **Description:** Appends to the [default include list](#default-values).<br>**Values:** List of Resolutions found in your library                                                                                                                                   |
    | `exclude`                     | **Description:** Exclude these Resolutions from creating a Dynamic Collection.<br>**Values:** List of Resolutions found in your library                                                                                                                             |
    | `include`                     | **Description:** Overrides the [default include list](#default-values).<br>**Values:** Any Resolutions found in your library                                                                                                                                        |
    | `limit_<<key>>`<sup>1</sup>   | **Description:** Changes the Builder Limit of the [key's](#collection_section) collection.<br>**Default:** `limit`<br>**Values:** Number Greater than 0                                                                                                             |
    | `limit`                       | **Description:** Changes the Builder Limit for all collections in a Defaults File.<br>**Values:** Number Greater than 0                                                                                                                                             |
    | `name_format`                 | **Description:** Changes the title format of the Dynamic Collections.<br>**Default:** `<<key_name>> <<library_translationU>>s`<br>**Values:** Any string with `<<key_name>>` in it.                                                                                 |
    | `remove_addons`               | **Description:** Removes from the [default addons dictionary](#default-values).<br>**Values:** Dictionary List of Resolutions found in your library                                                                                                                 |
    | `remove_include`              | **Description:** Removes from the [default include list](#default-values).<br>**Values:** List of Resolutions found in your library                                                                                                                                 |
    | `sort_by_<<key>>`<sup>1</sup> | **Description:** Changes the Smart Filter Sort of the [key's](#collection_section) collection.<br>**Default:** `sort_by`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                                 |
    | `sort_by`                     | **Description:** Changes the Smart Filter Sort for all collections in a Defaults File.<br>**Default:** `release.desc`<br>**Values:** [Any `smart_filter` Sort Option](../../files/builders/plex.md#sort-options)                                                    |
    | `style`                       | **Description:** Controls the visual theme of the collections created.<table class="clearTable"><tr><th>Values:</th></tr><tr><td><code>default</code></td><td>Default Theme</td></tr><tr><td><code>standards</code></td><td>Standards Theme</td></tr></table>       |
    | `summary_format`              | **Description:** Changes the summary format of the Dynamic Collections.<br>**Default:** `<<library_translationU>>s that have the resolution <<key_name>>.`<br>**Values:** Any string.                                                                               |

    1. Each default collection has a [`key`](#collection_section) that you must replace `<<key>>` with when using 
    this Template Variable. These keys are found in the table at the top of this page.

{% include-markdown "./../templates/defaults_variables.md" %}
{% include-markdown "./../templates/defaults_values.md" rewrite-relative-urls=false %}