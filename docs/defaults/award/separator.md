---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Award Separator",
        "CODE_NAME": "separator_award",
        "LIBRARY_TYPE": "Movie, Show",
        "SECTION_NUMBER": "130",
        "DESCRIPTION": "create a separator collection for Awards"
    }'
%}
{% include-markdown "./../templates/separator_line.md" replace='{"SEPARATOR": "Award"}' %}
{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "separator_award"}' %}
    {% include-markdown "./../templates/separator_example.md" replace='{"CODE_NAME": "separator_award"}' %}
{% include-markdown "./../templates/defaults_variables_header.md" only-include="separator" %}
{% include-markdown "./../templates/defaults_variables.md" start="<!--space-->" %}