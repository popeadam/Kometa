---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Based On...", 
        "CODE_NAME": "based",
        "LIBRARY_TYPE": "Movie, Show", 
        "SECTION_NUMBER": "085", 
        "DESCRIPTION": "create collections with items that are based on or inspired by various media outlets (such as Books or Video Games)"
    }'
%}
{% include-markdown "./../templates/separator_line.md" replace='{"SEPARATOR": "Based on..."}' %}
| `Based on a Book`       | `books`       | Collection of Movies/Shows based on or inspired by books        |
| `Based on a Comic`      | `comics`      | Collection of Movies/Shows based on or inspired by comics       |
| `Based on a True Story` | `true_story`  | Collection of Movies/Shows based on or inspired by true stories |
| `Based on a Video Game` | `video_games` | Collection of Movies/Shows based on or inspired by video games  |

{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "based"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: based
            template_variables:
              sep_style: navy #(1)!
              use_comics: false #(2)!
              order_true_story: 01 #(3)!
              visible_library_video_games: true #(4)!
              visible_home_video_games: true #(5)!
              visible_shared_video_games: true #(6)!
    ```

    1.  Use the navy [Separator Style](../separators.md#separator-styles)
    2.  Do not create a "Based on a Comic" collection
    3.  Make the "Based on a True Story" collection appear in the collection list before the other collections in this file
    4.  Pin the "Based on a Video Game" collection to the Recommended tab of the library
    5.  Pin the "Based on a Video Game" collection to the home screen of the server owner
    6.  Pin the "Based on a Video Game" collection to the home screen of other users of the server

{% include-markdown "./../templates/defaults_variables_header.md" %}
    {%
        include-markdown "./../templates/variable_list.md"
        only-include="exclude|limit|sort_by|sync_mode|format"
        replace='{
            "DYNAMIC_NAME": "Media Outlets", 
            "DYNAMIC_VALUE": "Media Outlet Keys",
            "NAME_FORMAT": "Based on a <<key_name>>",
            "SUMMARY_FORMAT": "<<library_translationU>>s based on or inspired by <<translated_key_name>>s."
        }'
        rewrite-relative-urls=false
    %}

    {% include-markdown "./../templates/variable_list.md" only-include="sup1" rewrite-relative-urls=false %}
{% include-markdown "./../templates/defaults_variables.md" %}
