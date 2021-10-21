`defaults` is a field in [Metainfo](Custom-Studies-Metainfo) of Custom Study, containing an object with settings that are applied when user clicks `Apply Defaults`.

This object has following fields:

`* - required`

* `bands` - an array with band styles. Band style is an object with fields:
  * `color`* - string
  * `linestyle`* - number
  * `linewidth`* - number
  * `value`* - number
  * `visible`* - boolean
* `filledAreasStyle` - an object. The keys are filled area ids, the values are style objects with fields:
  * `color`* - string
  * `visible`* - boolean
* `inputs` - an object with `input id` as a key and default value for this input. The default value can be `string`, `number` or `bool` depending on input type. The field is required if your study has inputs
* `palettes` - an object with `pallette id` as a key and palette definition: `[name]: { colors, valToIndex, addDefaultColor }`, where
  * `colors`* - an object `{ [color_id]: color_info }`. The color is an object with following fields:
    * `color`* - string
    * `style`* - number
    * `width`* - number
  * `valToIndex` - an object, the mapping between the values that are returned by the script and palette color indexes
  * `addDefaultColor` - boolean, if `true` the defaults are used for `colorer` type plot, when its value is `NaN`
* `precision`* - precision of the study's output values (quantity of digits after the decimal separator)
* `styles` - an object with `plot id` as keys and style info as values. `plot style` is an object with keys, specific for each plot `type` ([see below](#default-styles))

## Default Styles

Here is a short reference for `plot style` object in `defaults`.
Some of fields are the same for all of plot types:

* `visible`* - boolean

Additional fields should be added depending on `plot type`.

### Line

* `color`* - string, plot color
* `linestyle`* - number
* `linewidth`* - number
* `trackPrice`* - boolean, if `true`, price line is displayed

### Shapes

* `plottype`* - string, can have following values:
  * `shape_arrow_down`
  * `shape_arrow_up`
  * `shape_circle`
  * `shape_cross`
  * `shape_xcross`
  * `shape_diamond`
  * `shape_flag`
  * `shape_square`
  * `shape_label_down`
  * `shape_label_up`
  * `shape_triangle_down`
  * `shape_triangle_up`
* `location`*- string, one of the following:
  * `AboveBar`
  * `BelowBar`
  * `Top`
  * `Bottom`
  * `Right`
  * `Left`
  * `Absolute`
  * `AbsoluteUp`
  * `AbsoluteDown`
* `color`* - string, plot color
* `textColor`* - string, text color

### Chars

* `char*`* - string
* `location`*- string, one of the following:
  * `AboveBar`
  * `BelowBar`
  * `Top`
  * `Bottom`
  * `Right`
  * `Left`
  * `Absolute`
  * `AbsoluteUp`
  * `AbsoluteDown`
* `color`* - string, plot color
* `textColor`* - string, color

### Arrows

* `colorup`* - string, color
* `colordown`* - string, color
