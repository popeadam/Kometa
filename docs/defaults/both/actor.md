---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Actor",
        "CODE_NAME": "actor",
        "DESCRIPTION": "dynamically create collections based on the most popular actors/actresses in your library",
        "LIBRARY_TYPE": "Movie, Show",
        "SECTION_NUMBER": "140"
    }'
    exclude-tags="image"
%}
{% include-markdown "./../templates/separator_line.md" replace='{"SEPARATOR": "Actors"}' %}
| `<<actor_name>>`<br>**Example:** `Frank Welker` | `<<actor_name>>`<br>**Example:** `Frank Welker` | Collection of Movies/Shows the actor is top billing in. |

{% include-markdown "../people.md" %}
{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "actor"}' %}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: actor
            template_variables:
              data:
                depth: 10 #(1)!
                limit: 20 #(2)!
              style: diiivoycolor #(3)!
              sort_by: title.asc
              use_separator: false #(4)!
              tmdb_person_offset_Richard Brooks: 1 #(5)!
    ```

    1.  Check the first 10 casting credits in each movie
    2.  Create 20 collections maximum
    3.  use the [diiivoy Color Style](#poster-styles)
    4.  Do not create an "Actors Collections" separator
    5.  There are two Richard Brooks, so use the 2nd [Richard Brooks](https://www.themoviedb.org/search?query=Richard%20Brooks) found on TMDb

{% include-markdown "./../templates/defaults_variables_header.md" %}
    | `data` | **Description:** Replaces the `data` dynamic collection value.<table class="clearTable"><tr><th>Attribute</th><th>Description & Values</th></tr><tr><td><code>depth</code></td><td>Controls the depth within the casting credits to search for common actors<br><strong>Default:</strong> 5<br><strong>Values:</strong> Number greater than 0</td></tr><tr><td><code>limit</code></td><td>Controls the maximum number of collections to create<br><strong>Default:</strong> 25<br><strong>Values:</strong> Number greater than 0</td></tr></table> |
    {%
        include-markdown "./../templates/variable_list.md"
        only-include="exclude|include|limit|sort_by|style|format|tmdb_birthday|tmdb_person_offset"
        replace='{
            "NAME": "Actors", 
            "VALUE": "Actor Names",
            "NAME_FORMAT": "<<key_name>>",
            "SUMMARY_FORMAT": "<<library_translationU>>s with <<key_name>>."
        }'
    %}

    {% include-markdown "./../templates/variable_list.md" only-include="sup1" %}
{% include-markdown "./../templates/defaults_variables.md" %}