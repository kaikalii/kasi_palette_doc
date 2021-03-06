# Kasi - Palette Tutorial

Kasi allows you to create custom palettes that control colors as well as some other things.

## What are Palettes?

Palettes control colors and some geometry in Kasi. They are specified as [TOML](https://github.com/toml-lang/toml/blob/master/README.md) files and are placed in `C:\Users\<your username>\AppData\Local\kasi`.

To choose the palette for a plant, open the menu and go to `This Plant` > `Palette`.

To choose the default palette used for new plants, go to `Settings` > `Gameplay` > `Default Palette`.

## Types

Palette fields can have the following types:

- Color
    - A single 6 or 8 digit hexadecimal color string
    - Format is `rrggbb` for solid colors, `rrggbbaa` for colors with transparency
    - The corresponding game item uses this color
    - ex. `"#80ff40"`
- Multicolor
    - A single or list of 6 or 8 digit hexadecimal color strings
    - Each of the corresponding game items uses a random color from a list
    - ex. `["#19cc19", "#26bf19", "#33cc19"]`
- Polygon
    - A list of 2D points defining a closed polygon
    - The corresponding game item uses this polygon for its shape
    - Points should be bound between `-1` and `1` on both axes to roughly match default sizes
    - ex. `[[0, 1], [-0.7 -1], [0.7, -1]]`

## Fields

All available palette fields can be found [here](field_list.html).

All fields are optional.

## Meta Palettes

Instead of defining the standard palette fields, a palette can define a single field called `priority`, with a list of strings that refer to other palettes to be loaded. If a field is not present in a palette in the list, the game will try to use the field in the next palette in the list.

```
priority = ["first", "second", "third"]
```

## Example Palettes

This palette makes leaves rainbow colors:

`rainbow.toml`
```toml
spring_leaf = ["ff0000", "00ff00", "0000ff", "ffff00", "ff00ff", "00ffff"]
summer_leaf = ["ff0000", "00ff00", "0000ff", "ffff00", "ff00ff", "00ffff"]
fall_leaf = ["ff0000", "00ff00", "0000ff", "ffff00", "ff00ff", "00ffff"]
```

This palette turns birds into bats by making them black and turning their beaks transparent:

`bats.toml`
```toml
bird_body = "333333"
bird_wings = "191919"
bird_beak = "00000000"
```

This palette combines the rainbow and bats palettes:

`rainbow_and_bats.toml`
```toml
priority = ["rainbow", "bats"]
```
