---
hide:
  - toc
---
# Streaming Services Overlay

The `streaming` Default Overlay File is used to create an overlay based on the streaming service the file is found on 
for each item within your library.

![](images/streaming.png)

## Requirements & Recommendations

Supported Overlay Level: Movie, Show

## Supported Streaming Services

| Weight | Key           | Streaming Service |
| :----- | :------------ | :---------------- |
| `10`   | `hayu`        | hayu              |
| `20`   | `bet`         | BET+              |
| `30`   | `britbox`     | britbox           |
| `40`   | `all4`        | All 4             |
| `50`   | `now`         | NOW               |
| `55`   | `crave`       | Crave             |
| `58`   | `discovery`   | discovery+        |
| `60`   | `showtime`    | Showtime          |
| `70`   | `peacock`     | Peacock           |
| `80`   | `appletv`     | AppleTV           |
| `90`   | `paramount`   | Paramount+        |
| `100`  | `hulu`        | Hulu              |
| `110`  | `youtube`     | YouTube           |
| `120`  | `Crunchyroll` | Crunchyroll       |
| `130`  | `max`         | Max               |
| `140`  | `disney`      | Disney+           |
| `150`  | `amazon`      | Prime Video       |
| `160`  | `netflix`     | Netflix           |


## Regional Variants

Some logic is applied to allow for regional streaming service lists to be available to users depending on where they 
are, as detailed below:

| Region           | Key                              | Description                                                                                                                         |
| :--------------- | :------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| `CA`             | `max`, `showtime`                | These overlays will not be used if the region is `ca` as these streaming services are part of the Crave streaming service in Canada |
| any besides `CA` | `crave`                          | These overlays will not be used if the region is not `ca` as these streaming services are Canada-focused                            |
| any besides `GB` | `all4`, `britbox`, `hayu`, `now` | These overlays will not be used if the region is not `uk` as these streaming services are UK-focused                                |


## Config

The below YAML in your config.yml will create the overlays:

```yaml
libraries:
  Movies:
    overlay_files:
      - default: streaming
  TV Shows:
    overlay_files:
      - default: streaming
```

## Template Variables

Template Variables can be used to manipulate the file in various ways to slightly change how it works without having to 
make your own local copy.

Note that the `template_variables:` section only needs to be used if you do want to actually change how the defaults 
work. Any value not specified will use its default value if it has one if not it's just ignored.

??? example "Example Template Variable Amendments"

    The below is an example config.yml extract with some Template Variables added in to change how the file works.
    
    ```yaml
    libraries:
      Movies:
        overlay_files:
          - default: streaming
            template_variables:
              originals_only: true
              use_peacock: false
              weight_netflix: 100
    ```

* **File-Specific Template Variables** are variables available specifically for this Kometa Defaults File.

* **Overlay Template Variables** are additional variables shared across the Kometa Overlay Defaults.

??? example "Default Template Variable Values (click to expand)"

    | Variable            | Default                                                                        |
    |:--------------------|:-------------------------------------------------------------------------------|
    | `horizontal_offset` | **Description:** Change the horizontal offset.<br>**Default Value:** `15`      |
    | `horizontal_align`  | **Description:** Change the horizontal alignment.<br>**Default Value:** `left` |
    | `vertical_offset`   | **Description:** Change the vertical offset.<br>**Default Value:** `390`       |
    | `vertical_align`    | **Description:** Change the vertical alignment.<br>**Default Value:** `bottom` |
    | `back_color`        | **Description:** Change the back color.<br>**Default Value:** `#00000099`      |
    | `back_radius`       | **Description:** Change the back (lozenge) radius .<br>**Default Value:** `30` |
    | `back_width`        | **Description:** Change the back (lozenge) width.<br>**Default Value:** `305`  |
    | `back_height`       | **Description:** Change the back (lozenge) height.<br>**Default Value:** `105` |
    
=== "File-Specific Template Variables"

    | Variable                     | Description & Values                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | :--------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | `discover_with_<<key>>`      | **Description:** Overrides the TMDb Watch Provider used for the specfied key. This is only needed if a specific `region` has a different ID for the watch provider.<br>**Default:** `<<discover_with>>`<br>**Values:** Any TMDb Watch Provider ID for [Movies](https://developer.themoviedb.org/reference/watch-providers-movie-list) / [Shows](https://developer.themoviedb.org/reference/watch-provider-tv-list) based on the user's region |
    | `originals_only`             | **Description:** Changes Streaming Service overlays to only apply to original content produced by the service.<br>**Note**: Cannot be used with `region`, and only produces overlays for `amazon`, `appletv`, `disney`, `max`, `hulu`, `netflix`, `paramount`, `peacock`<br>**Default:** `false`<br>**Values:** `true`, `false`                                                                                                               |
    | `region`                     | **Description:** Changes some Streaming Service lists to regional variants (see below table for more information.<br>**Default:** `US`<br>**Values:** Any [ISO 3166-1 Code](https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) of the region where the streaming information should be based on.                                                                                                                                         |
    | `weight_<<key>>`<sup>1</sup> | **Description:** Controls the weight of the Overlay. Higher numbers have priority.<br>**Values:** Any Number                                                                                                                                                                                                                                                                                                                                  |

    1. Each default overlay has a `key` that when calling to effect a specific overlay you must replace `<<key>>` 
    with when calling.

=== "Overlay Template Variables"

    {%
        include-markdown "../overlay_variables.md"
    %}

