---
hide:
  - toc
---
{%
    include-markdown "./../templates/award_header.md"
    replace='{
        "FULL_NAME": "National Film Registry",
        "CODE_NAME": "nfr",
        "LIBRARY_TYPE": "Movie"
    }'
%}
| `National Film Registry All Time` | `all_time` | Collection of Films added to the National Film Registry. |
{%
    include-markdown "./../templates/award_mid_movie.md"
    replace='{
        "FULL_NAME": "National Film Registry",
        "CODE_NAME": "nfr",
        "SHORT_NAME": "National Film Registry"
    }'
    rewrite-relative-urls=false
%}