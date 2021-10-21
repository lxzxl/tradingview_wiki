OHLC plots can be used to create custom OHLC study with candle or bars type.

Firstly, we should add new OHLC plot to the [metainfo](Custom-Studies-Metainfo), using `ohlcPlots` field:

```javascript
ohlcPlots: {
    plotcandle_0: {
        title: 'Plot candle title',
    },
},
```

`ohlcPlots` is an object, where keys are `plot id` and values are `plots info`.
`Plot info` is an object with following fields:

`* - Required`

* `title`* - string, title of plot that will be used in settings dialog
* `isHidden`* - boolean
* `drawBorder` - boolean
* `showLast` - number

Now we need to declare `default` values for this plot (styles etc) in `metainfo`. Depending on the plot type you want to use there might be different schemas of the `default` object.

Example:

```javascript
// ...
defaults: {
    ohlcPlots: {
        plotcandle_0: {
            plottype: 'ohlc_candles',
            borderColor: '#000000',
            color: '#2196F3',
            drawBorder: true,
            drawWick: true,
            visible: true,
            wickColor: '#737375',
        },
    },
},
// ...
```

OHLC plots are 'meta' plots, this means that under the hood there should be a set of simple plots in metainfo `plots` field.

Example:

```javascript
plots: [
    {
        id: 'plot_0',
        type: 'ohlc_open',
        target: 'plotcandle_0',
    },
    {
        id: 'plot_1',
        type: 'ohlc_high',
        target: 'plotcandle_0',
    },
    {
        id: 'plot_2',
        type: 'ohlc_low',
        target: 'plotcandle_0',
    },
    {
        id: 'plot_3',
        type: 'ohlc_close',
        target: 'plotcandle_0',
    },
],
```

The main things here are `type` and `target` fields.

* `type` field must be one of the following: `ohlc_open`, `ohlc_high`, `ohlc_low` or `ohlc_close`, all four plots for every OHLC plot must be declared here.
* `target` - allows you to declare for which OHLC plot this 'simple' plot is. Here you should set an id of the OHLC plot (`plotcandle_0`).

Last but not least you have to return data for plots from your study's `main` function in [constructor](Custom-Studies-Constructor):

```javascript
this.main = function(context, inputCallback) {
    this._context = context;
    this._input = inputCallback;

    var direction = Math.sign(Math.random() - 0.5);
    var value = Math.random() * 200;

    var open  = value + 8 * direction;
    var high = value + 15;
    var low = value - 15;
    var close = value - 8 * direction;

    return [open, high, low, close];
}
```

Full example:

```javascript
{
    name: 'OHLC_sample',
    metainfo: {
        _metainfoVersion: 51,
        id: 'OHLC_sample@tv-basicstudies-1',
        scriptIdPart: '',
        description: 'OHLC_sample',
        shortDescription: 'OHLC_sample',
        is_hidden_study: false,
        is_price_study: false,
        isCustomIndicator: true,
        plots: [
            {
                id: 'plot_0',
                type: 'ohlc_open',
                target: 'plotcandle_0',
            },
            {
                id: 'plot_1',
                type: 'ohlc_high',
                target: 'plotcandle_0',
            },
            {
                id: 'plot_2',
                type: 'ohlc_low',
                target: 'plotcandle_0',
            },
            {
                id: 'plot_3',
                type: 'ohlc_close',
                target: 'plotcandle_0',
            },
        ],

        ohlcPlots: {
            plotcandle_0: {
                title: 'Plot candle title',
            },
        },

        defaults: {
            ohlcPlots: {
                plotcandle_0: {
                borderColor: '#000000',
                    color: '#2196F3',
                    drawBorder: true,
                    drawWick: true,
                    plottype: 'ohlc_candles', // might be 'ohlc_bars' for bars
                    visible: true,
                    wickColor: '#737375',
                },
            },
            precision: 4,
            inputs: {},
        },
        styles: {},
        inputs: [],
    },
    constructor: function() {
        this.main = function(context, inputCallback) {
            this._context = context;
            this._input = inputCallback;

            var direction = Math.sign(Math.random() - 0.5);
            var value = Math.random() * 200;

            var open  = value + 8 * direction;
            var high = value + 15;
            var low = value - 15;
            var close = value - 8 * direction;

            return [open, high, low, close];
        }
    }
}
```
