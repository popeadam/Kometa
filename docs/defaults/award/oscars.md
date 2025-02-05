---
hide:
  - toc
---
{%
    include-markdown "./../templates/award_header.md"
    replace='{
        "FULL_NAME": "Academy Awards (Oscars)",
        "CODE_NAME": "oscars",
        "LIBRARY_TYPE": "Movie"
    }'
%}
| `Oscars Best Picture Winners`  | `best_picture`  | Collection of Oscars Best Picture Award Winners.  |
| `Oscars Best Director Winners` | `best_director` | Collection of Oscars Best Director Award Winners. |
{%
    include-markdown "./../templates/award_mid_movie.md"
    replace='{
        "FULL_NAME": "Academy Awards (Oscars)",
        "CODE_NAME": "oscars",
        "SHORT_NAME": "Oscars"
    }'
    rewrite-relative-urls=false
%}