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

Below is a screenshot of the alternative Standards (`standards`) style which can be set via the `style` template variable.

Standards Style takes the base resolutions ("4K" and "720p") and turns them into the commonly-known standards name ("Ultra HD" and "HD Ready").

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
    
    {%
        include-markdown "./../templates/variable_list.md"
        only-include="addons|addons-extra|exclude|include|include-extra|limit|sort_by|resolution-style|sync_mode|format"
        replace='{
            "DYNAMIC_NAME": "Resolutions", 
            "DYNAMIC_VALUE": "Resolutions",
            "NAME_FORMAT": "<<key_name>> <<library_translationU>>s",
            "SUMMARY_FORMAT": "<<library_translationU>>s that have the resolution <<key_name>>."
        }'
        rewrite-relative-urls=false
    %}

    {% include-markdown "./../templates/variable_list.md" only-include="sup1" rewrite-relative-urls=false %}
{% include-markdown "./../templates/defaults_variables.md" %}
{% include-markdown "./../templates/defaults_values.md" rewrite-relative-urls=false %}