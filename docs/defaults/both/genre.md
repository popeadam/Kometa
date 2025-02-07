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
    {%
        include-markdown "./../templates/variable_list.md"
        only-include="addons|addons-extra|exclude|limit|sort_by|format"
        replace='{
            "DYNAMIC_NAME": "Genres", 
            "DYNAMIC_VALUE": "Genres",
            "NAME_FORMAT": "<<key_name>> <<library_translationU>>s",
            "SUMMARY_FORMAT": "<<library_translationU>>s that have the genre <<key_name>>."
        }'
        rewrite-relative-urls=false
    %}

    {% include-markdown "./../templates/variable_list.md" only-include="sup1" rewrite-relative-urls=false %}

{% include-markdown "./../templates/defaults_variables.md" %}
{% include-markdown "./../templates/defaults_values.md" rewrite-relative-urls=false %}