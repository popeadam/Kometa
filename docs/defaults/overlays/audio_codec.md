---
hide:
  - toc
---
# Audio Codec Overlay

The `audio_codec` Default Overlay File is used to create an overlay based on the audio codec available on each item 
within your library.

![](images/audio_codec.png)

## Requirements & Recommendations

Supported Overlay Level: Movie, Show, Season, Episode

Recommendations: Designed for [TRaSH Guides](https://trash-guides.info/) filename naming scheme

## Supported Audio Codecs

| Weight | Key            | Audio Codec            |
| :----- | :------------- | :--------------------- |
| `10`   | `opus`         | Opus                   |
| `20`   | `mp3`          | MP3                    |
| `30`   | `aac`          | AAC                    |
| `40`   | `digital`      | Dolby Digital          |
| `50`   | `dts`          | DTS                    |
| `60`   | `dtses`        | DTS-ES                 |
| `70`   | `plus`         | Dolby Digital+         |
| `80`   | `hra`          | DTS-HD-HRA             |
| `90`   | `pcm`          | PCM                    |
| `100`  | `flac`         | FLAC                   |
| `110`  | `ma`           | DTS-HD-MA              |
| `120`  | `truehd`       | Dolby TrueHD           |
| `130`  | `dolby_atmos`  | Dolby Atmos            |
| `140`  | `plus_atmos`   | Dolby Digital+ / E-AC3 |
| `150`  | `dtsx`         | DTS-X                  |
| `160`  | `truehd_atmos` | Dolby TrueHD Atmos     |


### Standard Style

Below is a screenshot of the alternative Standard (`standard`) style which can be set via the `style` Template Variable.

![](images/audio_codec2.png)

## Config

The below YAML in your config.yml will create the overlays:

```yaml
libraries:
  Movies:
    overlay_files:
      - default: audio_codec
  TV Shows:
    overlay_files:
      - default: audio_codec
      - default: audio_codec
        template_variables:
          builder_level: season
      - default: audio_codec
        template_variables:
          builder_level: episode
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
          - default: audio_codec
            template_variables:
              use_opus: false
              use_mp3: false
              style: standard
    ```

* **File-Specific Template Variables** are variables available specifically for this Kometa Defaults File.

* **Overlay Template Variables** are additional variables shared across the Kometa Overlay Defaults.

??? example "Default Template Variable Values (click to expand)"

    | Variable            | Default     |
    |:--------------------|:------------|
    | `horizontal_offset` | `0`         |
    | `horizontal_align`  | `center`    |
    | `vertical_offset`   | `15`        |
    | `vertical_align`    | `top`       |
    | `back_color`        | `#00000099` |
    | `back_radius`       | `30`        |
    | `back_width`        | `305`       |
    | `back_height`       | `105`/`189` |
    
=== "File-Specific Template Variables"

    | Variable                     | Description & Values                                                                                         |
    | :--------------------------- | :----------------------------------------------------------------------------------------------------------- |
    | `builder_level`              | **Description:** Choose the Overlay Level.<br>**Values:** `season` or `episode`                              |
    | `regex_<<key>>`<sup>1</sup>  | **Description:** Controls the regex of the Overlay Search.<br>**Values:** Any Proper Regex                   |
    | `style`                      | **Description:** Choose the Overlay Style.<br>**Default:** `compact`<br>**Values:** `compact` or `standard`  |
    | `weight_<<key>>`<sup>1</sup> | **Description:** Controls the weight of the Overlay. Higher numbers have priority.<br>**Values:** Any Number |

    1. Each default overlay has a `key` that when calling to effect a specific overlay you must replace `<<key>>` 
    with when calling.

=== "Overlay Template Variables"

    {%
        include-markdown "../overlay_variables.md"
    %}

