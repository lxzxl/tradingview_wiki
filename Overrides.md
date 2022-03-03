This Charting Library section includes the chart property description. These properties are treated
as customizable ones. The customization of other properties is not supported.

The properties are listed in the following format:

`<property_path>: <default Charting Library value>`

```javascript
// supported values: large, medium, small, tiny
volumePaneSize: "large"

// fonts available in text editors (i.e., in `Text` drawing tool properties dialog)
editorFontsList: ['Verdana', 'Courier New', 'Times New Roman', 'Arial']

paneProperties.backgroundType: "solid" // or "gradient"
paneProperties.background: "#ffffff"
paneProperties.backgroundGradientStartColor: "#ffffff"
paneProperties.backgroundGradientEndColor: "#ffffff"

paneProperties.vertGridProperties.color: "rgba(42, 46, 57, 0.06)"
paneProperties.vertGridProperties.style: LINESTYLE_SOLID
 
paneProperties.horzGridProperties.color: "rgba(42, 46, 57, 0.06)"
paneProperties.horzGridProperties.style: LINESTYLE_SOLID
 
paneProperties.crossHairProperties.color: "#9598A1"
paneProperties.crossHairProperties.style: LINESTYLE_DASHED
paneProperties.crossHairProperties.transparency: 0
paneProperties.crossHairProperties.width: 1

// Margins (percentage). Used for auto scaling.
paneProperties.topMargin: 10
paneProperties.bottomMargin: 8

paneProperties.axisProperties.autoScale: true
paneProperties.axisProperties.lockScale: false
paneProperties.axisProperties.percentage: false
paneProperties.axisProperties.indexedTo100: false
paneProperties.axisProperties.log: false
paneProperties.axisProperties.alignLabels: true
paneProperties.axisProperties.isInverted: false

paneProperties.legendProperties.showStudyArguments: true
paneProperties.legendProperties.showStudyTitles: true
paneProperties.legendProperties.showStudyValues: true
paneProperties.legendProperties.showSeriesTitle: true
paneProperties.legendProperties.showSeriesOHLC: true
paneProperties.legendProperties.showLegend: true
paneProperties.legendProperties.showBarChange: true
paneProperties.legendProperties.showBackground: true
paneProperties.legendProperties.backgroundTransparency: 50

scalesProperties.backgroundColor: "#ffffff"
scalesProperties.lineColor: "rgba(42, 46, 57, 0.14)"
scalesProperties.textColor: "#131722"
scalesProperties.fontSize: 12
scalesProperties.scaleSeriesOnly: false
scalesProperties.showSeriesLastValue: true
scalesProperties.seriesLastValueMode: PriceAxisLastValueMode.LastValueAccordingToScale
scalesProperties.showSeriesPrevCloseValue: false
scalesProperties.showStudyLastValue: false
scalesProperties.showSymbolLabels: false
scalesProperties.showStudyPlotLabels: false
scalesProperties.showCurrency: true
scalesProperties.showUnit: true

timeScale.rightOffset: 5

timezone: "Etc/UTC" # See supported timezones list (at Symbology#timezone page) for available values


// Series style. See the supported values below
// Bar = 0
// Candle = 1
// Line = 2
// Area = 3
// Renko = 4
// Kagi = 5
// Point&Figure = 6
// Line Break = 7
// Heikin Ashi = 8
// Hollow Candle = 9
// Baseline = 10
// Range = 11
// HiLo = 12

mainSeriesProperties.style: 1

mainSeriesProperties.visible: true
mainSeriesProperties.showPriceLine: true
mainSeriesProperties.priceLineWidth: 1
mainSeriesProperties.priceLineColor: ""
mainSeriesProperties.baseLineColor: "#B2B5BE"
mainSeriesProperties.showPrevClosePriceLine: false
mainSeriesProperties.prevClosePriceLineWidth: 1
mainSeriesProperties.prevClosePriceLineColor: "rgba( 85, 85, 85, 1)"
mainSeriesProperties.minTick: "default" // minTick value is a string representation of 3 values: pricescale, minmove, fractional (see below)
mainSeriesProperties.showCountdown: true


mainSeriesProperties.priceAxisProperties.autoScale: true            (see #749)
mainSeriesProperties.priceAxisProperties.lockScale: false
mainSeriesProperties.priceAxisProperties.percentage: false
mainSeriesProperties.priceAxisProperties.indexedTo100: false
mainSeriesProperties.priceAxisProperties.log: false
mainSeriesProperties.priceAxisProperties.isInverted: false
mainSeriesProperties.priceAxisProperties.alignLabels: true

mainSeriesProperties.statusViewStyle.showExchange: true
mainSeriesProperties.statusViewStyle.showInterval: true
// possible values are: description, ticker, ticker-and-description
mainSeriesProperties.statusViewStyle.symbolTextSource: "description"

symbolWatermarkProperties.color : "rgba(0, 0, 0, 0.00)"
symbolWatermarkProperties.visibility : true

// Different chart types defaults

// Candles styles
mainSeriesProperties.candleStyle.upColor: "#26a69a"
mainSeriesProperties.candleStyle.downColor: "#ef5350"
mainSeriesProperties.candleStyle.drawWick: true
mainSeriesProperties.candleStyle.drawBorder: true
mainSeriesProperties.candleStyle.borderColor: "#378658"
mainSeriesProperties.candleStyle.borderUpColor: "#26a69a"
mainSeriesProperties.candleStyle.borderDownColor: "#ef5350"
mainSeriesProperties.candleStyle.wickColor: "#737375"
mainSeriesProperties.candleStyle.wickUpColor: "#26a69a"
mainSeriesProperties.candleStyle.wickDownColor: "#ef5350"
mainSeriesProperties.candleStyle.barColorsOnPrevClose: false
mainSeriesProperties.candleStyle.drawBody: true

// Hollow Candles styles
mainSeriesProperties.hollowCandleStyle.upColor: "#26a69a"
mainSeriesProperties.hollowCandleStyle.downColor: "#ef5350"
mainSeriesProperties.hollowCandleStyle.drawWick: true
mainSeriesProperties.hollowCandleStyle.drawBorder: true
mainSeriesProperties.hollowCandleStyle.borderColor: "rgba( 55, 134, 88, 1)"
mainSeriesProperties.hollowCandleStyle.borderUpColor: "#26a69a"
mainSeriesProperties.hollowCandleStyle.borderDownColor: "#ef5350"
mainSeriesProperties.hollowCandleStyle.wickColor: "rgba( 115, 115, 117, 1)"
mainSeriesProperties.hollowCandleStyle.wickUpColor: "#26a69a"
mainSeriesProperties.hollowCandleStyle.wickDownColor: "#ef5350"
mainSeriesProperties.hollowCandleStyle.drawBody: true

// Heikin Ashi styles
mainSeriesProperties.haStyle.upColor: "#26a69a"
mainSeriesProperties.haStyle.downColor: "#ef5350"
mainSeriesProperties.haStyle.drawWick: true
mainSeriesProperties.haStyle.drawBorder: true
mainSeriesProperties.haStyle.borderColor: "rgba( 55, 134, 88, 1)"
mainSeriesProperties.haStyle.borderUpColor: "#26a69a"
mainSeriesProperties.haStyle.borderDownColor: "#ef5350"
mainSeriesProperties.haStyle.wickColor: "rgba( 115, 115, 117, 1)"
mainSeriesProperties.haStyle.wickUpColor: "#26a69a"
mainSeriesProperties.haStyle.wickDownColor: "#ef5350"
mainSeriesProperties.haStyle.barColorsOnPrevClose: false
mainSeriesProperties.haStyle.drawBody: true

// Bar styles
mainSeriesProperties.barStyle.upColor: "#26a69a"
mainSeriesProperties.barStyle.downColor: "#ef5350"
mainSeriesProperties.barStyle.barColorsOnPrevClose: false
mainSeriesProperties.barStyle.dontDrawOpen: false
mainSeriesProperties.barStyle.thinBars: true

// Line styles
mainSeriesProperties.lineStyle.color: "#2962FF"
mainSeriesProperties.lineStyle.linestyle: LINESTYLE_SOLID
mainSeriesProperties.lineStyle.linewidth: 2
mainSeriesProperties.lineStyle.priceSource: "close"

// Area styles
mainSeriesProperties.areaStyle.color1: "rgba(33, 150, 243, 0.28)"
mainSeriesProperties.areaStyle.color2: "#2962FF"
mainSeriesProperties.areaStyle.linecolor: "#2962FF"
mainSeriesProperties.areaStyle.linestyle: LINESTYLE_SOLID
mainSeriesProperties.areaStyle.linewidth: 2
mainSeriesProperties.areaStyle.priceSource: "close"
mainSeriesProperties.areaStyle.transparency: 100

// Baseline styles
mainSeriesProperties.baselineStyle.baselineColor: "rgba( 117, 134, 150, 1)"
mainSeriesProperties.baselineStyle.topFillColor1: "rgba( 38, 166, 154, 0.28)"
mainSeriesProperties.baselineStyle.topFillColor2: "rgba( 38, 166, 154, 0.05)"
mainSeriesProperties.baselineStyle.bottomFillColor1: "rgba( 239, 83, 80, 0.05)"
mainSeriesProperties.baselineStyle.bottomFillColor2: "rgba( 239, 83, 80, 0.28)"
mainSeriesProperties.baselineStyle.topLineColor: "rgba( 38, 166, 154, 1)"
mainSeriesProperties.baselineStyle.bottomLineColor: "rgba( 239, 83, 80, 1)"
mainSeriesProperties.baselineStyle.topLineWidth: 2
mainSeriesProperties.baselineStyle.bottomLineWidth: 2
mainSeriesProperties.baselineStyle.priceSource: "close"
mainSeriesProperties.baselineStyle.transparency: 50
mainSeriesProperties.baselineStyle.baseLevelPercentage: 50

// Hi-Lo styles
mainSeriesProperties.hiloStyle.color: "#2962FF"
mainSeriesProperties.hiloStyle.showBorders: true
mainSeriesProperties.hiloStyle.borderColor: "#2962FF"
mainSeriesProperties.hiloStyle.showLabels: true
mainSeriesProperties.hiloStyle.labelColor: "#2962FF"
mainSeriesProperties.hiloStyle.fontSize: 7

// Line Break styles
mainSeriesProperties.pbStyle.upColor: "#26a69a"
mainSeriesProperties.pbStyle.downColor: "#ef5350"
mainSeriesProperties.pbStyle.borderUpColor: "#26a69a"
mainSeriesProperties.pbStyle.borderDownColor: "#ef5350"
mainSeriesProperties.pbStyle.upColorProjection: "rgba( 169, 220, 195, 1)"
mainSeriesProperties.pbStyle.downColorProjection: "rgba( 245, 166, 174, 1)"
mainSeriesProperties.pbStyle.borderUpColorProjection: "rgba( 169, 220, 195, 1)"
mainSeriesProperties.pbStyle.borderDownColorProjection: "rgba( 245, 166, 174, 1")

// Renko styles
mainSeriesProperties.renkoStyle.upColor: "#26a69a"
mainSeriesProperties.renkoStyle.downColor: "#ef5350"
mainSeriesProperties.renkoStyle.borderUpColor: "#26a69a"
mainSeriesProperties.renkoStyle.borderDownColor: "#ef5350"
mainSeriesProperties.renkoStyle.upColorProjection: "rgba( 169, 220, 195, 1)"
mainSeriesProperties.renkoStyle.downColorProjection: "rgba( 245, 166, 174, 1)"
mainSeriesProperties.renkoStyle.borderUpColorProjection: "rgba( 169, 220, 195, 1)"
mainSeriesProperties.renkoStyle.borderDownColorProjection: "rgba( 245, 166, 174, 1)"
mainSeriesProperties.renkoStyle.wickUpColor: "#26a69a"
mainSeriesProperties.renkoStyle.wickDownColor: "#ef5350"

// Kagi styles
mainSeriesProperties.kagiStyle.upColor: "#26a69a"
mainSeriesProperties.kagiStyle.downColor: "#ef5350"
mainSeriesProperties.kagiStyle.upColorProjection: "rgba( 169, 220, 195, 1)"
mainSeriesProperties.kagiStyle.downColorProjection: "rgba( 245, 166, 174, 1)"

// Point&Figure styles
mainSeriesProperties.pnfStyle.upColor: "#26a69a"
mainSeriesProperties.pnfStyle.downColor: "#ef5350"
mainSeriesProperties.pnfStyle.upColorProjection: "rgba( 169, 220, 195, 1)"
mainSeriesProperties.pnfStyle.downColorProjection: "rgba( 245, 166, 174, 1)"

// Range styles
mainSeriesProperties.rangeStyle.upColor: "#26a69a"
mainSeriesProperties.rangeStyle.downColor: "#ef5350"
mainSeriesProperties.rangeStyle.thinBars: "true"
mainSeriesProperties.rangeStyle.upColorProjection: "rgba( 169, 220, 195, 1)"
mainSeriesProperties.rangeStyle.downColorProjection: "rgba( 245, 166, 174, 1)"
```

#### LineStyles

```javascript
LINESTYLE_SOLID = 0
LINESTYLE_DOTTED = 1
LINESTYLE_DASHED = 2
LINESTYLE_LARGE_DASHED = 3
```

#### PriceAxisLastValueMode

```javascript
LastPriceAndPercentageValue = 0
LastValueAccordingToScale = 1
```

### Mintick

Look [here](Symbology#minmov-pricescale-minmove2-fractional) for more information about `minTick` values.

Below is a list of all possible values, represented as an object for better readability:

```text
{ priceScale: 1, minMove: 1, frac: false },
{ priceScale: 10, minMove: 1, frac: false },
{ priceScale: 100, minMove: 1, frac: false },
{ priceScale: 1000, minMove: 1, frac: false },
{ priceScale: 10000, minMove: 1, frac: false },
{ priceScale: 100000, minMove: 1, frac: false },
{ priceScale: 1000000, minMove: 1, frac: false },
{ priceScale: 10000000, minMove: 1, frac: false },
{ priceScale: 100000000, minMove: 1, frac: false },
{ priceScale: 2, minMove: 1, frac: true },
{ priceScale: 4, minMove: 1, frac: true },
{ priceScale: 8, minMove: 1, frac: true },
{ priceScale: 16, minMove: 1, frac: true },
{ priceScale: 32, minMove: 1, frac: true },
{ priceScale: 64, minMove: 1, frac: true },
{ priceScale: 128, minMove: 1, frac: true },
{ priceScale: 320, minMove: 1, frac: true },
```

In additional to values above, there is a special value for the default minTick - `'default'`.

For example:

```javascript
// reset minTick to default
tvWidget.applyOverrides({ 'mainSeriesProperties.minTick': 'default' });

// set series' minTick to { priceScale: 10000, minMove: 1, frac: false }
tvWidget.applyOverrides({ 'mainSeriesProperties.minTick': '10000,1,false' });

// set default minTick for overlay studies to { priceScale: 10000, minMove: 1, frac: false }
tvWidget.applyStudiesOverrides({ 'overlay.minTick': '10000,1,false' });
```
