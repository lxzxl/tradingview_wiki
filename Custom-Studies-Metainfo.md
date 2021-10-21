The `metainfo` field is designed to contain the main info about the custom study.
For color information in `metainfo` `#RRGGBB` or `rgba()` can be used. Transparency can be set using `rgba()` color format.
Custom Study Metainfo contains following fields:

`* - Required`

* `_metainfoVersion` - a number, metainfo version of the Charting Library, the current is `51`. Default is `0`.
* `id`* - a string, should have the form `<study name>@tv-basicstudies-1`, where `study name` - your custom study name.
* `description`* - a string, it will be displayed in the Indicators window and will be used as a `name` argument when calling the createStudy method
* `shortDescription`* - a string, will be displayed on the chart.
* `isCustomIndicator` - boolean, should be `true` in Custom Study.
* `format` - an object with the info about the Price Scale formatting. It has 2 possible keys: `type` and `precision`. The format can `inherit` type from the base series, or it can have `price` / `volume` / `percent` type and an optional integer field `precision` - precision of the study's output values (quantity of digits after the decimal separator).
* `is_hidden_study` - boolean, shows whether the study should appear in Indicators list.
* `is_price_study` - boolean, shows whether the study should appear on the main series pane.
* `linkedToSeries` - boolean flag, shows whether the study price scale should be the same as the main series one.
* `plots` - an array with study plots info, see [dedicated article](Custom-Studies-Plots).
* `ohlcPlots` - ohlc plots style info, [advanced use article](Custom-Studies-OHLC-Plots).
* `defaults`* - an object containing settings that are applied when user clicks `Apply Defaults`, [details](Custom-Studies-Defaults).
* `bands` - an array with study band info objects with fields:
  * `name`* - string, appears near band settings in Style tab.
  * `id` - string, can be used in `filledAreas` as `objAId` or `objBId`.
  * `isHidden` - boolean flag, set it `false` if the band should appear in properties dialog.
* `filledAreas` - an array of filled areas info. Filled area is a special object, which allows coloring an area between two plots or hlines. Please note, that it is impossible to fill the area between a band and a hline. Filled area contains fields:
  * `id`* - string, id of the filled area, will be used in `defaults` field.
  * `objAId`* - string, `id` of plot or band (hline).
  * `objBId`* - string, `id` of second plot or band (hline).
  * `title`* - string, will appear on the Style tab.
  * `type`* - field describing which area should be filled, can be `hline_hline` (for bands) or `plot_plot`.
* `palettes` - an object with the definitions of palletes that are used in `plots` and `defaults`. Palettes allows you use different styles (not only colors) for each line point. This object contains palette names as keys, and palette info as values: `[palette.name]: { colors, valToIndex, addDefaultColor }`, where
  * `colors`* - an object `{ [color_id]: { name: 'name' }}`, where `name` is a string that will appear on Style tab of study properties dialog.
  * `valToIndex` - an object, the mapping between the values that are returned by the script and palette colors.
  * `addDefaultColor` - boolean, if `true` the defaults are used for `colorer` type plot, when its value is `null` or `undefined`.
* `styles` - an object with `plot id` as keys and style info as values. Style info is an object with keys:
  * `title` - a string, will be displayed in the Style tab.
  * `histogramBase` - number, price value which will be considered as a start base point when rendering plot with histogram, columns or area style.
  * `joinPoints` - boolean, if `true` then plot points will be joined with line, applicable only to `Circles` and `Cross` type plots. Default is false.
  * `isHidden` - boolean, it is `true` if the plot settings should appear in Style tab.
  * `minHeight` - plotarrow minimal possible arrow height in pixels. Applicable to arrow plot style.
  * `maxHeight` - plotarrow maximum possible arrow height in pixels. Applicable to arrow plot style.
  * `size` - size of characters on the chart. Possible values are: `auto`, `tiny`, `small`, `normal`, `large`,`huge`. Applicable to `chars` and `shapes` plot types.
  * `text` - text to display with the plot. Applicable to `chars` and `shapes` plot types.
  * `showLast` - if set, defines the number of bars (from the last bar back to the past) to plot on chart.
* `inputs` - study inputs, an array with inputs info depending on type, see [details](Custom-Studies-Inputs).
