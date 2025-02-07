---
hide:
  - toc
---
{%
    include-markdown "./../templates/award_header.md"
    replace='{
        "FULL_NAME": "British Academy of Film and Television Arts",
        "CODE_NAME": "bafta",
        "LIBRARY_TYPE": "Movie"
    }'
%}
| `BAFTA Best Films` | `best` | Collection of British Academy of Film and Television Arts Best Film Award Winners. |
{%
    include-markdown "./../templates/award_mid_movie.md"
    replace='{
        "FULL_NAME": "British Academy of Film and Television Arts",
        "CODE_NAME": "bafta",
        "SHORT_NAME": "BAFTA", "testtest": "test"
    }'
    rewrite-relative-urls=false
%}