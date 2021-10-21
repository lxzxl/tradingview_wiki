When adding a Custom Study to Widget Constructor, you have the possibility to customize the style of each plot.

The `plots` field is located in [metainfo](Custom-Studies-Metainfo) and contains an array with plots info.

Plot info is an object, it contains required fields `id` and `type`. Also it can contain other fields depending on the type of a plot.

Example:

```javascript
...
plots: [
    {
        id: 'plot_0',
        type: 'line'
    },
    {
        id: 'plot_1',
        palette: 'palette_0',
        target: 'plot_0',
        type: 'colorer'
    },
    {
        id: 'plot_2',
        type: 'line'
    },
],
```

## Arrows

* `type`- 'arrows'
* `visible`- boolean
* `colorup`- string
* `colordown`- string

## Chars

* `type`- 'chars'
* `visible`- boolean
* `char`- string
* `location`- string, one of the following:
  * `AboveBar`
  * `BelowBar`
  * `Top`
  * `Bottom`
  * `Right`
  * `Left`
  * `Absolute`
  * `AbsoluteUp`
  * `AbsoluteDown`
* `color`- string
* `textColor`- string

## Colorer

* `type`- 'colorer'
* `palette`- string
* `target`- string

## DataOffset

* `type`- 'dataoffset'
* `target`- string

## Line

* `type`- 'line'
* `visible`- boolean
* `plottype`- number, one of the following:
  * `0`- line
  * `1`- histogram
  * `3`- cross
  * `4`- area
  * `5`- columns
  * `6`- circles
  * `7`- line with breaks
  * `8`- area with breaks
  * `9`- step line
* `color`- string
* `linestyle`- number
* `linewidth`- number
* `trackPrice`- boolean

## Ohlc

* `type`- string, can be either `ohlc_open`, `ohlc_high`, `ohlc_low`, or `ohlc_close`
* `target`- string
* `plottype`- string, can be `ohlc_bars` or `ohlc_candles`
* `visible`- boolean
* `color`- string

If `plottype: 'ohlc_candles'`, additional fields should be provided:

* `drawWick`- boolean
* `drawBorder`- boolean
* `wickColor`- string
* `borderColor`- string

## Shapes

* `type`- 'shapes'
* `visible`- boolean
* `plottype`- string, can have following values:
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
* `location`- string, one of the following:
  * `AboveBar`
  * `BelowBar`
  * `Top`
  * `Bottom`
  * `Right`
  * `Left`
  * `Absolute`
  * `AbsoluteUp`
  * `AbsoluteDown`
* `color`- string
* `textColor`- string

## BarColorer

* `type`- 'bar_colorer'
* `palette`- string

## BgColorer

* `type`- 'bg_colorer'
* `palette`- string

## TextColorer

* `type`- 'text_colorer'
* `palette`- string
* `target`- string

## OhlcColorer

* `type`- 'ohlc_colorer'
* `palette`- string
* `target`- string
