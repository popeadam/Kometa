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
    {%
        include-markdown "./../templates/variable_list.md"
        only-include="addons|addons-extra|exclude|include|include-extra|limit|sort_by|format"
        replace='{
            "DYNAMIC_NAME": "Content Ratings", 
            "DYNAMIC_VALUE": "Content Ratings",
            "NAME_FORMAT": "<<key_name>> <<library_translationU>>so",
            "SUMMARY_FORMAT": "<<library_translationU>>s that are rated <<key_name>>."
        }'
        rewrite-relative-urls=false
    %}

    {% include-markdown "./../templates/variable_list.md" only-include="sup1" rewrite-relative-urls=false %}

{% include-markdown "./defaults_variables.md" %}
{% include-markdown "./defaults_values.md" rewrite-relative-urls=false %}