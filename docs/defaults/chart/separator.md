---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Chart Separator",
        "CODE_NAME": "separator_chart",
        "LIBRARY_TYPE": "Movie, Show",
        "SECTION_NUMBER": "020",
        "DESCRIPTION": "create a separator collection for Charts"
    }'
%}
{% include-markdown "./../templates/separator_line.md" replace='{"SEPARATOR": "Chart"}' %}
{% include-markdown "./../templates/defaults_mid_both.md" replace='{"CODE_NAME": "separator_chart"}' %}
    {% include-markdown "./../templates/separator_example.md" replace='{"CODE_NAME": "separator_chart"}' %}
{% include-markdown "./../templates/defaults_variables_header.md" only-include="separator" %}
{% include-markdown "./../templates/defaults_variables.md" start="<!--space-->" %}