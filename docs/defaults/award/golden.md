---
hide:
  - toc
---
{%
    include-markdown "./award_1.md"
    replace='[["FULL_NAME", "Golden Globes"], ["CODE_NAME", "golden"], ["LIBRARY_TYPE", "Movie, Show"]]'
    end="<!--space-->"
%}

Recommendations: The `Golden Globe Best Motion Pictures` and `Golden Globes Best Director Winners` Collections only work 
with Movie Libraries.

{%
    include-markdown "./award_1.md"
    replace='[["FULL_NAME", "Golden Globes"], ["CODE_NAME", "golden"], ["LIBRARY_TYPE", "Movie, Show"]]'
    start="<!--space-->"
%}
| `Golden Globes Best Picture Winners`  | `best_picture`  | Collection of Golden Globe Best Picture Award Winners.  |
| `Golden Globes Best Director Winners` | `best_director` | Collection of Golden Globe Best Director Award Winners. |
{%
    include-markdown "./award_2.md"
    replace='[["FULL_NAME", "Golden Globes"], ["SHORT_NAME", "Golden Globe"]]'
%}
{%
    include-markdown "./../movie_example.md"
    replace='["CODE_NAME", "golden"]'
%}
{%
    include-markdown "./../show_example.md"
    replace='["CODE_NAME", "golden"]'
%}
{%
    include-markdown "./award_3.md"
    replace='[["SHORT_NAME", "Golden Globe"], ["CODE_NAME", "golden"]]'
%}