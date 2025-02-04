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
    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: separator_award
            template_variables:
              sep_style: purple #(1)!
    ```

    1.  Use the purple [Separator Style](../separators.md#separator-styles)

{% include-markdown "./../templates/defaults_variables_header.md" start="<!--space-->" end="<!--space2-->" %}
{% include-markdown "./../templates/defaults_variables.md" start="<!--space-->" %}