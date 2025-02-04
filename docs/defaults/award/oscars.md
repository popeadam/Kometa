{%
    include-markdown "./../templates/award_1.md"
    replace='[["FULL_NAME", "Academy Awards (Oscars)"], ["CODE_NAME", "oscars"], ["LIBRARY_TYPE", "Movie"]]'
%}
| `Oscars Best Picture Winners`  | `best_picture`  | Collection of Oscars Best Picture Award Winners.  |
| `Oscars Best Director Winners` | `best_director` | Collection of Oscars Best Director Award Winners. |
{%
    include-markdown "./../templates/award_2.md"
    replace='[["FULL_NAME", "Academy Awards (Oscars)"], ["SHORT_NAME", "Oscars"]]'
%}
{%
    include-markdown "./../templates/movie_example.md"
    replace='["CODE_NAME", "oscars"]'
%}
{%
    include-markdown "./../templates/award_3.md"
    replace='[["SHORT_NAME", "Oscars"], ["CODE_NAME", "oscars"]]'
%}