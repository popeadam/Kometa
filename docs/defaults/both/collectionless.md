---
hide:
  - toc
---
{%
    include-markdown "./../templates/defaults_header.md"
    replace='{
        "COLLECTION": "Collectionless", 
        "CODE_NAME": "collectionless",
        "LIBRARY_TYPE": "Movie, Show",
        "DESCRIPTION": "create a [Collectionless collection](../../files/builders/plex.md#plex-collectionless) to help Show/Hide Movies/Shows properly in your library."
    }'
    end="<!--space-->"
%}

Requirements: 

* This file needs to run last under `collection_files`.

* All other normal collections must use `collection_mode: hide_items`.

* Disable the `Minimum automatic collection size` option when using the `Plex Movie` Agent. (Use the 
[`franchise` Default](../movie/franchise.md) for automatic collections)

## Collection

| Collection       | Description                                                                                                                            |
|:-----------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| `Collectionless` | [Collectionless collection](../../files/builders/plex.md#plex-collectionless) to help Show/Hide Movies/Shows properly in your library. |

{% include-markdown "./../templates/defaults_config.md" %}
  Movies:
    template_variables:
      collection_mode: hide_items
    collection_files:
      - default: collectionless
  TV Shows:
    template_variables:
      collection_mode: hide_items
    collection_files:
      - default: collectionless
{% include-markdown "./../templates/defaults_template_variables.md" %}
    ```yaml
    libraries:
      Movies:
        template_variables:
          collection_mode: hide_items
        collection_files:
          - default: collectionless
            template_variables:
              exclude:
                - Marvel Cinematic Universe
              collection_order: release
    ```

{% include-markdown "./../templates/defaults_variables_header.md" start="<!--space-->" end="<!--space2-->" %}
{% include-markdown "./../templates/defaults_no_shared_variables.md" %}
{% include-markdown "./../templates/defaults_variables_header.md" start="<!--space2-->" %}
    | `collection_order`       | **Description:** Changes the Collection Order for all collections in this file.<br>**Default:** `alpha`<br>**Values:**<table class="clearTable"><tr><td>`release`</td><td>Order Collection by Release Dates</td></tr><tr><td>`alpha`</td><td>Order Collection Alphabetically</td></tr><tr><td>`custom`</td><td>Order Collection Via the Builder Order</td></tr><tr><td>[Any `plex_search` Sort Option](../../files/builders/plex.md#sort-options)</td><td>Order Collection by any `plex_search` Sort Option</td></tr></table> |
    | `exclude_prefix`         | **Description:** Overrides the default exclude_prefix list. Exclude Collections with one of these prefixes from being considered for collectionless.<br>**Default:** default exclude_prefix list<br>**Values:** List of Prefixes                                                                                                                                                                                                                                                                                              |  |
    | `exclude`                | **Description:** Exclude these Collections from being considered for collectionless.<br>**Values:** List of Collections                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `name_collectionless`    | **Description:** Changes the name of the collection.<br>**Values:** New Collection Name                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `sort_title`             | **Description:** Sets the sort title for the collection.<br>**Default:** `~_Collectionless`<br>**Values:** Any String                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `summary_collectionless` | **Description:** Changes the summary of the collection.<br>**Values:** New Collection Summary                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `url_poster`             | **Description:** Changes the poster url of the collection.<br>**Values:** URL directly to the Image                                                                                                                                                                                                                                                                                                                                                                                                                           |

{% include-markdown "./../templates/defaults_values.md" rewrite-relative-urls=false %}