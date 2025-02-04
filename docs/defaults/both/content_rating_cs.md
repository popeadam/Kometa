---
hide:
  - toc
---
{%
    include-markdown "./../templates/content_rating.md"
    replace='{
        "COLLECTION": "Common Sense Media Content Rating", 
        "CODE_NAME": "content_rating_cs",
        "SHORT_NAME": "Common Sense",
        "LIBRARY_TYPE": "Movie, Show",
        "EXAMPLE_NAME": "Age 5+",
        "EXAMPLE1": "5",
        "EXAMPLE2": "G"
    }'
    end="<!--rec-start-->"
    rewrite-relative-urls=false
%}
Recommendation: Use the [Mass Content Rating Update Library Operation](../../config/operations.md#mass-content-rating-update) with either `mdb_commonsense` or `mdb_commonsense0` to update Plex to the Common Sense Rating.
{%
    include-markdown "./../templates/content_rating.md"
    replace='{
        "COLLECTION": "Common Sense Media Content Rating", 
        "CODE_NAME": "content_rating_cs",
        "SHORT_NAME": "Common Sense",
        "LIBRARY_TYPE": "Movie, Show",
        "RECOMMENDATION": "",
        "EXAMPLE_NAME": "Age 5+",
        "EXAMPLE1": "5",
        "EXAMPLE2": "G"
    }'
    start="<!--rec-end-->"
    rewrite-relative-urls=false
%}