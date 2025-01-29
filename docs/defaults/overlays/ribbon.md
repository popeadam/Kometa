---
hide:
  - toc
---
# Ribbon Overlays

The `ribbon` Default Overlay File is used to create a ribbon overlay based on the Top Lists of various sites on each 
item within your library.

![](images/ribbon.png)

## Requirements & Recommendations

Supported Overlay Level: Movie, Show

## Supported Ribbon

| Weight | Key               | Ribbon                          |
| :----- | :---------------- | :------------------------------ |
| `150`  | `bafta`           | BAFTA Winner                    |
| `130`  | `berlinale`       | Berlinale Winner                |
| `140`  | `cannes`          | Cannes Winner                   |
| `70`   | `cesar`           | César Winner                    |
| `20`   | `common`          | Common Sense Selection          |
| `90`   | `choice`          | Critic's Choice Winner          |
| `100`  | `emmys`           | Emmys Winner                    |
| `160`  | `golden_director` | Golden Globe Director           |
| `170`  | `golden`          | Golden Globe Winner             |
| `60`   | `imdb`            | IMDb Top 250                    |
| `80`   | `spirit`          | Independent Spirit Award Winner |
| `50`   | `letterboxd`      | Letterboxd Top 250              |
| `30`   | `metacritic`      | Metacritic Must See             |
| `180`  | `oscars_director` | Oscars Best Director            |
| `190`  | `oscars`          | Oscars Best Picture             |
| `10`   | `razzie`          | Razzies Winner                  |
| `40`   | `rotten`          | Rotten Tomatoes Certified Fresh |
| `45`   | `rottenverified`  | Rotten Tomatoes Verified Hot    |
| `110`  | `sundance`        | Sundance Winner                 |
| `120`  | `venice`          | Venice Winner                   |

## Config

The below YAML in your config.yml will create the overlays:

```yaml
libraries:
  Movies:
    overlay_files:
      - default: ribbon
  TV Shows:
    overlay_files:
      - default: ribbon
```

## Template Variables

Template Variables can be used to manipulate the file in various ways to slightly change how it works without having to 
make your own local copy.

Note that the `template_variables:` section only needs to be used if you do want to actually change how the defaults 
work. Any value not specified will use its default value if it has one if not it's just ignored.

??? abstract "Variable Lists (click to expand)"

    * **File-Specific Template Variables** are variables available specifically for this Kometa Defaults File.

    * **Overlay Template Variables** are additional variables shared across the Kometa Overlay Defaults.

    ??? example "Default Template Variable Values (click to expand)"

        | Variable            | Default  |
        |:--------------------|:---------|
        | `horizontal_offset` | `0`      |
        | `horizontal_align`  | `right`  |
        | `vertical_offset`   | `0`      |
        | `vertical_align`    | `bottom` |
        
    === "File-Specific Template Variables"

        | Variable                     | Description & Values                                                                                                    |
        | :--------------------------- | :---------------------------------------------------------------------------------------------------------------------- |
        | `style`                      | **Description:** Controls the color of the ribbon. <br>**Default:** `yellow` <br>**Values:** `yellow, gray, black, red` |
        | `use_all`                    | **Description:** Used to turn on/off all keys. <br>**Default:** `true` <br>**Values:** `true` or `false`                |
        | `weight_<<key>>`<sup>1</sup> | **Description:** Controls the weight of the Overlay. Higher numbers have priority.<br>**Values:** Any Number            |

        1. Each default overlay has a `key` that when calling to effect a specific overlay you must replace `<<key>>` 
        with when calling.

    === "Overlay Template Variables"

        {%
           include-markdown "../overlay_variables.md"
        %}
    
???+ example "Example Template Variable Amendments"

    The below is an example config.yml extract with some Template Variables added in to change how the file works.
    
    ```yaml
    libraries:
      Movies:
        overlay_files:
          - default: ribbon
            template_variables:
              style: black
              weight_metacritic: 35
              use_common: false
    ```
