# Themes

Version 1.7 brings basic support for themes, and 1.9 extends it to include keyboard shortcuts and support for multiple theme files.

## Creating and editing themes

* Look at the `Theme` class in [`katrain/gui/theme.py`](https://github.com/sanderland/katrain/blob/master/katrain/gui/theme.py).
* Make a `theme<yourthemename>.json` file in your `<home dir>/.katrain` directory and specify any variables from the above class you want to override, e.g. 
 ```json
 {
  "BACKGROUND_COLOR": [1,0,0,1],
  "KEY_STOP_ANALYSIS": "f10",
  "MISTAKE_SOUNDS": ["jeff.wav","what.wav"]
}
  ```
* All resources (including icons, which can not be renamed for now) will be looked up in `<home dir>/.katrain` first, so files with identical names there can be used to override sounds and images.
* If variables are specified in multiple theme files, the *latest* alphabetically takes precedence. That is, each later theme file overwrites the settings from any previous one.

## Expected territory options

* KaTrain supports different styles of display of expected territory:
  * Blended style colors the board with an intensity proportional to the likelihood of a player controlling that territory at the end of the game.
  * In the Marks style, each point of the board is marked with a square of size which is proportional to ownership likelihood.
  * The Blocks style divides the whole board into black, white, and neutral territory, based on a likelihood threshold. This style is appropriate as a counting aid, but may be misleading before endgame if much of the territory is unsettled.
* Marks can also appear on stones to indicate the likelihood of these stones living at the end of the game. Three styles are supported:
  * All stones can be marked, with the color of the mark indicating the expected ownership and the size of the mark indicating certainty.
  * Weak stones only - marks will appear only on stones which are over 50% likely to die before the end of the game.
  * No stone marks.

| <img src="https://raw.githubusercontent.com/jacobm-tech/katrain/blended-territory-display/themes/blended-all.png" width="400px"/><br><span style="font-weight:normal">Blended style, all stones marked</span> | <img src="https://raw.githubusercontent.com/jacobm-tech/katrain/blended-territory-display/themes/marks-weak.png" width="400px"/><br><span style="font-weight:normal">Marks on intersections, weak stones marked</span> |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|                    <img src="https://raw.githubusercontent.com/jacobm-tech/katrain/blended-territory-display/themes/blocks-none.png" width="400px"/><br>Territory blocks, no stones marked                    |                      <img src="https://raw.githubusercontent.com/jacobm-tech/katrain/blended-territory-display/themes/blended-weak.png" width="400px"/><br>Blended territory, weak stones marked                       |
                             

<sup>The game used in the screenshots is [Albert Yen vs. Eric Yoder](https://www.usgo.org/news/2022/03/members-edition-midwest-open-round-2-the-broken-ladder-game).</sup>

The stone marks and territory style are independent; the table above presents 4 possible variants out of 9.
The relevant variables are:
```
    TERRITORY_DISPLAY = "blended" | "marks" | "blocks"
    STONE_MARKS = "all" | "weak" | "none"
    OWNERSHIP_MAX_ALPHA = 0.7 
    BLOCKS_THRESHOLD = 0.6
    MARK_SIZE = 0.42  # as fraction of stone size
```

## Installation

* To install a theme, simply unzip the theme.zip to your .katrain folder. 
  * On Windows you can find it in C:\Users\you\\.katrain and on linux in ~/.katrain.
  * When in doubt, the general settings dialog will also show the location.
* To uninstall a theme, remove theme.json and all relevant images from that folder.

## Available themes

### Alternate board/stones theme by "koast"

[Download](https://github.com/sanderland/katrain/blob/master/themes/koast-theme.zip)

![Preview](https://raw.githubusercontent.com/sanderland/katrain/master/themes/koast.png)

### Lizzie-like theme

* Theme created by Eric W, includes modified board, stones
* Images taken from [Lizzie](https://github.com/featurecat/lizzie/) by featurecat and contributors.
* Hides hints for low visit/uncertain moves instead of showing small dots. 

[Download](https://github.com/sanderland/katrain/blob/master/themes/eric-lizzie-look.zip)

![Preview](https://raw.githubusercontent.com/sanderland/katrain/master/themes/eric-lizzie.png)


### Jeff sounds

* This theme makes Jeff comment `Ahhh?` and `What?!` when you make mistakes.
* Sounds provided by Mikkgo.

[Download](https://github.com/sanderland/katrain/blob/master/themes/jeff-sounds.zip)

