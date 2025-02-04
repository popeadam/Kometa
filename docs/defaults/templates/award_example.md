    ```yaml
    libraries:
      Movies:
        collection_files:
          - default: CODE_NAME
            template_variables:
              collection_mode: show_items #(1)!
              collection_order: alpha #(2)!
              radarr_add_missing: true #(3)!
              name_format: SHORT_NAME <<key_name>> Winners #(4)!
              data: #(5)!
                starting: latest-10
                ending: latest
    ```

    1.  Shows the collection and all of its items within the Library tab in Plex.
    2.  Sorts the collection items alphabetically.
    3.  Adds items from the source list which are not in Plex to Radarr.
    4.  Change the name of the collections to "SHORT_NAME yearhere Winners".
    5.  Creates collections from 10 award shows back to the latest award show.
