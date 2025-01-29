---
hide:
  - toc
---
# Resolution/Edition Overlay

The `resolution` Default Overlay File is used to create an overlay based on the resolutions and editions available on 
each item within your library.

![](images/resolution.png)

## Requirements & Recommendations

Supported Overlay Level: Movie, Show, Episode

Recommendations: Editions overlay is designed to use the Editions field within Plex [which requires Plex Pass to use] or 
the [TRaSH Guides](https://trash-guides.info/) filename naming scheme

## Supported Resolutions

| Weight | Key               | Resolution      |
| :----- | :---------------- | :-------------- |
| `1`    | `hdr`             | HDR             |
| `5`    | `dv`              | DV              |
| `7`    | `plus`            | HDR10+          |
| `8`    | `dvhdr`           | DV/HDR          |
| `9`    | `dvhdrplus`       | DV/HDR10+       |
| `10`   | `480p`            | 480P            |
| `20`   | `480p_hdr`        | 480P HDR        |
| `30`   | `480p_dv`         | 480P DV         |
| `35`   | `480p_plus`       | 480P HDR10+     |
| `38`   | `480p_dvhdr`      | 480P DV/HDR     |
| `39`   | `480p_dvhdrplus`  | 480P DV/HDR10+  |
| `40`   | `576p`            | 576P            |
| `50`   | `576p_hdr`        | 576P HDR        |
| `60`   | `576p_dv`         | 576P DV         |
| `65`   | `576p_plus`       | 576P HDR10+     |
| `68`   | `576p_dvhdr`      | 576P DV/HDR     |
| `69`   | `576p_dvhdrplus`  | 576P DV/HDR10+  |
| `70`   | `720p`            | 720P            |
| `80`   | `720p_hdr`        | 720P HDR        |
| `90`   | `720p_dv`         | 720P DV         |
| `95`   | `720p_plus`       | 720P HDR10+     |
| `98`   | `720p_dvhdr`      | 720P DV/HDR     |
| `99`   | `720p_dvhdrplus`  | 720P DV/HDR10+  |
| `100`  | `1080p`           | 1080P           |
| `110`  | `1080p_hdr`       | 1080P HDR       |
| `120`  | `1080p_dv`        | 1080P DV        |
| `125`  | `1080p_plus`      | 1080P HDR10+    |
| `128`  | `1080p_dvhdr`     | 1080P DV/HDR    |
| `129`  | `1080p_dvhdrplus` | 1080p DV/HDR10+ |
| `130`  | `4k`              | 4K              |
| `140`  | `4k_hdr`          | 4K HDR          |
| `150`  | `4k_dv`           | 4K DV           |
| `155`  | `4k_plus`         | 4K HDR10+       |
| `158`  | `4k_dvhdr`        | 4K DV/HDR       |
| `159`  | `4k_dvhdrplus`    | 4K DV/HDR10+    |

## Supported Editions

| Weight | Key             | Edition             |
| :----- | :-------------- | :------------------ |
| `5`    | `ulysses`       | Ulysses             |
| `6`    | `openmatte`     | Open Matte          |
| `7`    | `definitive`    | Definitive          |
| `8`    | `blackchrome`   | Black and Chrome    |
| `9`    | `richarddonner` | Richard Donner      |
| `10`   | `criterion`     | Criterion           |
| `20`   | `remastered`    | Remastered          |
| `30`   | `imax`          | IMAX                |
| `40`   | `enhanced`      | IMAX Enhanced       |
| `50`   | `coda`          | Coda Cut            |
| `60`   | `alternate`     | Alternate Cut       |
| `70`   | `ultimate`      | Ultimate Cut        |
| `80`   | `theatrical`    | Theatrical Cut      |
| `90`   | `international` | International Cut   |
| `100`  | `final`         | Final Cut           |
| `110`  | `directors`     | Director's Cut      |
| `120`  | `platinum`      | Platinum Edition    |
| `130`  | `diamond`       | Diamond Edition     |
| `140`  | `collector`     | Collector's Edition |
| `150`  | `anniversary`   | Anniversary Edition |
| `160`  | `special`       | Special Edition     |
| `170`  | `unrated`       | Unrated Edition     |
| `180`  | `uncut`         | Uncut Edition       |
| `190`  | `extended`      | Extended Edition    |

## "Dovetail" versions

In the Kometa log, you may see references to versions of these overlays with `-Dovetail` appended:

```
| 4K-Plus-Dovetail Overlay in Movies |
| 4K-DV-Dovetail Overlay in Movies |
| 4K-Dovetail Overlay in Movies |
| 4K-HDR-Dovetail Overlay in Movies |
...
| Extended-Edition-Dovetail Overlay in Movies |
| Uncut-Edition-Dovetail Overlay in Movies |
| Unrated-Edition-Dovetail Overlay in Movies |
...
```

These `-Dovetail` variations are used when resolution and edition are combined so that one "dovetails" into the other.  
This is not something you can enable or disable independently; it's an internal implementation detail.

## Config

The below YAML in your config.yml will create the overlays:

```yaml
libraries:
  Movies:
    overlay_files:
      - default: resolution
  TV Shows:
    overlay_files:
      - default: resolution
      - default: resolution
        template_variables:
          builder_level: season
      - default: resolution
        template_variables:
          builder_level: episode
```

## Template Variables

Template Variables can be used to manipulate the file in various ways to slightly change how it works without having to 
make your own local copy.

Note that the `template_variables:` section only needs to be used if you do want to actually change how the defaults 
work. Any value not specified will use its default value if it has one if not it's just ignored.

??? example "Example Template Variable Amendments (Click to Expand)"

    The below is an example config.yml extract with some Template Variables added in to change how the file works.
    
    ```yaml
    libraries:
      Movies:
        overlay_files:
          - default: resolution
            template_variables:
              use_dvhdrplus: false
              use_dv: false
              use_hdr: false
              use_1080p: false
              use_720p: false
              use_576p: false
              use_480p: false
              use_1080p_hdr: false
              use_1080p_dv: false
    ```

* **File-Specific Template Variables** are variables available specifically for this Kometa Defaults File.

* **Overlay Template Variables** are additional variables shared across the Kometa Overlay Defaults.

??? example "Default Template Variable Values (click to expand)"

    | Variable            | Default     |
    |:--------------------|:------------|
    | `horizontal_offset` | `15`        |
    | `horizontal_align`  | `left`      |
    | `vertical_offset`   | `15`        |
    | `vertical_align`    | `top`       |
    | `back_color`        | `#00000099` |
    | `back_radius`       | `30`        |
    | `back_width`        | `305`       |
    | `back_height`       | `105`/`189` |
    
=== "File-Specific Template Variables"

    | Variable                     | Description & Values                                                                                                                           |
    | :--------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------- |
    | `builder_level`              | **Description:** Choose the Overlay Level.<br>**Values:** `season` or `episode`                                                                |
    | `use_edition`                | **Description:** Turns off all Edition Overlays in the Defaults File.<br>**Values:** `false` to turn off the overlays                          |
    | `use_resolution`             | **Description:** Turns off all Resolution Overlays in the Defaults File.<br>**Values:** `false` to turn off the overlays                       |
    | `weight_<<key>>`<sup>1</sup> | **Description:** Controls the weight of the Overlay. Higher numbers have priority. **Only works with Edition keys.**<br>**Values:** Any Number |

    1. Each default overlay has a `key` that when calling to effect a specific overlay you must replace `<<key>>` 
    with when calling.

=== "Overlay Template Variables"

    {%
        include-markdown "../overlay_variables.md"
    %}

