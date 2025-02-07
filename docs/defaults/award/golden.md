---
hide:
  - toc
---
{%
    include-markdown "./../templates/award_header.md"
    replace='{
        "FULL_NAME": "Golden Globes",
        "CODE_NAME": "golden",
        "LIBRARY_TYPE": "Movie, Show"
    }'
    replace-tags='{"space": "Recommendations: The `Golden Globe Best Motion Pictures` and 
`Golden Globes Best Director Winners` Collections only work with Movie Libraries."}'
%}
| `Golden Globes Best Picture Winners`  | `best_picture`  | Collection of Golden Globe Best Picture Award Winners.  |
| `Golden Globes Best Director Winners` | `best_director` | Collection of Golden Globe Best Director Award Winners. |
{%
    include-markdown "./../templates/award_mid_both.md"
    replace='{
        "FULL_NAME": "Golden Globes",
        "CODE_NAME": "golden",
        "SHORT_NAME": "Golden Globe"
    }'
    rewrite-relative-urls=false
%}