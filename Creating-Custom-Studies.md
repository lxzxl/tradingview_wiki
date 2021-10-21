## Displaying your data as an indicator

To display your own indicators there is a [custom_indicators_getter](Widget-Constructor#custom_indicators_getter) field in Widget Constructor.
There is a variety of plot types, such as lines, arrows, bar colorers, etc. For full reference please see the [Metainfo](Custom-Studies-Metainfo) section.

The custom indicator is an object with the following fields:

* `name` - your study name, it will be used internally by the Charting Library
* `metainfo` - study metainfo, for details please see [Metainfo](Custom-Studies-Metainfo) article
* `constructor` - the field containing required functions `init()` and `main()`. [Constructor page](Custom-Studies-Constructor)

The instruction below explains how to display chart data as an indicator. Please follow these steps.

1. Come up with a new ticker name to display your data and set up your server to return valid SymbolInfo for this new ticker.
1. Also, set up the server to return valid historical data for this ticker.
1. Add [custom_indicators_getter](Widget-Constructor#custom_indicators_getter) key to the widget constructor. Its value is a function that returns a Promise object with a list of custom indicators.
1. *(Optional)* Update your widget's initialization code to [create](Chart-Methods#createstudyname-forceoverlay-lock-inputs-overrides-options) this indicator when the chart is ready.

Indicator template:

```javascript
custom_indicators_getter: function(PineJS) {
    return Promise.resolve([
        {
            name: '<study name>',
            metainfo: {
                _metainfoVersion: 51,
                id: '<study name>@tv-basicstudies-1',
                description: '<study description>',
                shortDescription: '<short study description>',
                is_hidden_study: true,
                is_price_study: true,
                isCustomIndicator: true,
                format: {
                    type: 'price',
                    precision: 2,
                },

                plots: [{id: 'plot_0', type: 'line'}],
                defaults: {
                    styles: {
                        plot_0: {
                            linestyle: 0,
                            visible: true,
                            linewidth: 2,
                            plottype: 2,

                            // Show price line?
                            trackPrice: false,

                            // Plot color
                            color: '#0000FF'
                        }
                    },
                    precision: 2,
                    inputs: {}
                },
                styles: {
                    plot_0: {
                        title: '-- output name --',
                        histogramBase: 0,
                    }
                },
                'inputs': [],
            },

            constructor: function() {
                this.init = function(context, inputCallback) {
                    this._context = context;
                    this._input = inputCallback;

                    // Define the symbol to be plotted.
                    // Symbol should be a string.
                    // You can use PineJS.Std.ticker(this._context) to get the selected symbol's ticker.
                    // For example,
                    //    var symbol = 'AAPL';
                    //    var symbol = '#EQUITY';
                    //    var symbol = PineJS.Std.ticker(this._context) + '#TEST';
                    var symbol = '<TICKER>';
                    this._context.new_sym(symbol, PineJS.Std.period(this._context));
                };

                this.main = function(context, inputCallback) {
                    this._context = context;
                    this._input = inputCallback;

                    this._context.select_sym(1);

                    // You can use following built-in functions in PineJS.Std object:
                    //    open, high, low, close
                    //    hl2, hlc3, ohlc4
                    var v = PineJS.Std.close(this._context);
                    return [v];
                }
            }
        }
    ]);
},
```

## Examples

* [Requesting data for another ticker](Custom-Studies-Examples#requesting-data-for-another-ticker)
* [Coloring bars](Custom-Studies-Examples#coloring-bars)
* [Custom styles for every point](Custom-Studies-Examples#custom-styles-for-every-point)
* [Complex filled areas](Custom-Studies-Examples#complex-filled-areas)
* [OHLC plots](Custom-Studies-OHLC-Plots)
* [Advanced OHLC style](Custom-Studies-Examples#advanced-OHLC-style)
* [Advanced Shapes use](Custom-Studies-Examples#advanced-shapes-use)
