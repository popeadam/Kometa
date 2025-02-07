| `use_year_collections`    | **Description:** Turn the individual year collections off.<br>**Values:** `false` to turn of the collections |
| `year_collection_section` | **Description:** Change the collection section for year collections only. (Use quotes to not lose leading zeros `"05"`)<br>**Values:** Any number |
| `data`                    | **Description:** Replaces the `data` dynamic collection value.<br><table class="clearTable"><tr><th>Attribute</th><th>Description & Values</th></tr><tr><td><code>starting</code></td><td>Controls the starting year for collections<br><strong>Default:</strong> latest-5<br><strong>Values:</strong> Number greater than 0</td></tr><tr><td><code>ending</code></td><td>Controls the ending year for collections<br><strong>Default:</strong> latest<br><strong>Values:</strong> Number greater than 1</td></tr><tr><td><code>increment</code></td><td>Controls the increment (i.e. every 5th year)<br><strong>Default:</strong> 1<br><strong>Values:</strong> Number greater than 0</td><td></td></tr></table><ul><li><strong><code>starting</code> and <code>ending</code> can also have the value <code>latest</code></strong></li><li><strong>You can also use a value relative to the <code>latest</code> by doing <code>latest-5</code></strong></li></ul> | 
| `collection_order`                     | **Description:** Changes the Collection Order for all collections in a Defaults File.<br>**Default:** `custom`<br>**Values:**{% include-markdown "./collection_order_options.md" replace='{"\n": "", "\t": ""}' rewrite-relative-urls=false %} |
| `collection_order_<<key>>`<sup>1</sup> | **Description:** Changes the Collection Order of the [key's](#collection_section) collection.<br>**Default:** `collection_order`<br>**Values:**{% include-markdown "./collection_order_options.md" replace='{"\n": "", "\t": ""}' rewrite-relative-urls=false %} |
{%
    include-markdown "./variable_list.md"
    only-include="exclude|sync_mode|format"
    replace='{
        "DYNAMIC_NAME": "Years", 
        "DYNAMIC_VALUE": "Years",
        "NAME_FORMAT": "SHORT_NAME <<key_name>>",
        "SUMMARY_FORMAT": "<<key_name>> SHORT_NAME Award Winners."
    }'
    rewrite-relative-urls=false
%}

{% include-markdown "./variable_list.md" only-include="sup1" rewrite-relative-urls=false %}