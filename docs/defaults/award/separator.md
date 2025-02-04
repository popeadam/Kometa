---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_1.md"
    replace='[["COLLECTION", "Award Separator"], ["CODE_NAME", "separator_award"], ["LIBRARY_TYPE", "Movie, Show"], ["SECTION_NUMBER", "130"], ["DESCRIPTION", "create a separator collection for Awards"]]'
%}
| `Award Collections` | `separator` | [Separator Collection](../separators.md) to denote the Section of Collections. |

{%
    include-markdown "./../templates/defaults_2.md"
%}
{%
    include-markdown "./../templates/movie_example.md"
    replace='["CODE_NAME", "actor"]'
%}
{%
    include-markdown "./../templates/show_example.md"
    replace='["CODE_NAME", "actor"]'
%}
{%
    include-markdown "./../templates/defaults_3.md"
%}
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: separator_award
            template_variables:
              sep_style: purple #(1)!
    ```

    1.  Use the purple [Separator Style](../separators.md#separator-styles)

{%
  include-markdown "./../templates/defaults_4.md"
  start="<!--space-->"
  end="<!--space2-->"
%}
{%
  include-markdown "./../templates/defaults_5.md"
  start="<!--space-->"
%}