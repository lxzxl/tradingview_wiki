## Requesting data for another ticker

```javascript
custom_indicators_getter: function(PineJS) {
    return Promise.resolve([
        {
            name: 'Equity',
            metainfo: {
                _metainfoVersion: 51,
                id: 'Equity@tv-basicstudies-1',
                description: 'Equity',
                shortDescription: 'Equity',
                is_hidden_study: true,
                is_price_study: true,
                isCustomIndicator: true,
                format: {
                    type: 'price',
                    // Precision is set to one digit, e.g. 777.7
                    precision: 1,
        },

                plots: [{id: 'plot_0', type: 'line'}],
                defaults: {
                    styles: {
                        plot_0: {
                            linestyle: 0,
                            visible: true,

                            // Make the line thinner
                            linewidth: 1,

                            // Plot type is Line
                            plottype: 2,

                            // Show price line
                            trackPrice: true,

                            // Set the plotted line color to dark red
                            color: '#880000'
                        }
                    },

                    inputs: {}
                },
                styles: {
                    plot_0: {
                        // Output name will be displayed in the Style window
                        title: 'Equity value',
                        histogramBase: 0,
                    }
                },
                inputs: [],
            },

            constructor: function() {
                this.init = function(context, inputCallback) {
                    this._context = context;
                    this._input = inputCallback;

                    var symbol = '#EQUITY';
                    this._context.new_sym(symbol, PineJS.Std.period(this._context), PineJS.Std.period(this._context));
                };

                this.main = function(context, inputCallback) {
                    this._context = context;
                    this._input = inputCallback;

                    this._context.select_sym(1);

                    var v = PineJS.Std.close(this._context);
                    return [v];
                }
            }
        }
    ]);
},
```

## Coloring bars

![images/bar_colorer.png](images/bar_colorer.png)

```javascript
{
    name: 'Bar Colorer Demo',
    metainfo: {
        _metainfoVersion: 51,

        id: "BarColoring@tv-basicstudies-1",
        name: "BarColoring",
        description: "Bar Colorer Demo",
        shortDescription: "BarColoring",

        isCustomIndicator: true,
        isTVScript: false,
        isTVScriptStub: false,

        format: {
            type: 'price',
            precision: 4,
        },

        defaults: {
            palettes: {
                palette_0: {
                    // palette colors
                    // change it to the default colors that you prefer,
                    // but note that the user can change them in the Style tab
                    // of indicator properties
                    colors: [
                        { color: '#FFFF00' },
                        { color: '#0000FF' }
                    ]
                }
            }
        },
        inputs: [],
        plots: [{
            id: 'plot_0',

            // plot type should be set to 'bar_colorer'
            type: 'bar_colorer',

            // this is the name of the palette that is defined
            // in 'palettes' and 'defaults.palettes' sections
            palette: 'palette_0'
        }],
        palettes: {
            palette_0: {
                colors: [
                    { name: 'Color 0' },
                    { name: 'Color 1' }
                ],

                // the mapping between the values that
                // are returned by the script and palette colors
                valToIndex: {
                    100: 0,
                    200: 1
                }
            }
        }
    },
    constructor: function() {
        this.main = function(context, input) {
            this._context = context;
            this._input = input;

            var valueForColor0 = 100;
            var valueForColor1 = 200;

            // perform your calculations here and return one of the constants
            // that is specified as a key in 'valToIndex' mapping
            var result =
                Math.random() * 100 % 2 > 1 ? // we randomly select one of the color values
                    valueForColor0 : valueForColor1;

            return [result];
        }
    }
}
```

## Custom styles for every point

![images/custom_styles_for_every_point.png](images/custom_styles_for_every_point.png)

```javascript
{
    name: 'Equity',
    metainfo: {
        _metainfoVersion: 51,
        id: 'Equity@tv-basicstudies-1',
        scriptIdPart: '',
        description: 'Equity',
        shortDescription: 'Equity',
        is_hidden_study: false,
        is_price_study: false,
        isCustomIndicator: true,
        plots: [
            {
                'id': 'plot_0',
                'type': 'line',
            },
            {
                'id': 'plot_1',
                'type': 'colorer',
                'target': 'plot_0',
                'palette': 'paletteId1',
            },
        ],
        palettes: {
            paletteId1: {
                colors: {
                    0: {
                            name: 'First color',
                    },
                    1: {
                            name: 'Second color',
                    },
                },
            },
        },
        defaults: {
            palettes: {
                paletteId1: {
                    colors: {
                        0: {
                            color: 'red',
                            width: 1,
                            style: 0,
                        },
                        1: {
                            color: 'blue',
                            width: 3,
                            style: 1,
                        },
                    },
                },
            },
            styles: {},
            precision: 4,
            inputs: {},
        },
        styles: {
            plot_0: {
                title: 'Equity value',
                histogramBase: 0,
            },
        },
        inputs: [],
    },
    constructor: function() {
        this.main = function(context, inputCallback) {
            this._context = context;
            this._input = inputCallback;

            var value = Math.random() * 200;

            return [value, value > 100 ? 0 : 1];
        }
    }
}
```

## Complex filled areas

![images/complex_filled_areas.png](images/complex_filled_areas.png)

```javascript
{
    name: 'Equity',
    metainfo: {
        _metainfoVersion: 51,
        id: 'Equity@tv-basicstudies-1',
        scriptIdPart: '',
        description: 'Equity',
        shortDescription: 'Equity',
        is_hidden_study: false,
        is_price_study: false,
        isCustomIndicator: true,
        plots: [
            {
                id: 'plot_0',
                type: 'line',
            },
            {
                id: 'plot_1',
                type: 'line',
            },
            {
                id: 'plot_2',
                type: 'colorer',
                target: 'filledAreaId1',
                palette: 'paletteId1',
            },
        ],

        filledAreas: [
            {
                id: 'filledAreaId1',
                objAId: 'plot_0',
                objBId: 'plot_1',
                title: 'Filled area between first and second plot',
                type: 'plot_plot',
                palette: 'paletteId1',
            },
        ],

        palettes: {
            paletteId1: {
                valToIndex: {
                    0: 0,
                    1: 1,
                },
                colors: {
                    0: {
                        name: 'First color',
                    },
                    1: {
                        name: 'Second color',
                    },
                },
            },
        },
        defaults: {
            filledAreasStyle: {
                filledAreaId1: {
                    color: 'yellow',
                    visible: true,
                },
            },

            palettes: {
                paletteId1: {
                    colors: {
                        0: {
                            color: 'red',
                            width: 1,
                            style: 0,
                        },
                        1: {
                            color: 'blue',
                            width: 3,
                            style: 1,
                        },
                    },
                },
            },

            styles:
            {
                plot_0: {
                    linestyle: 0,
                    visible: true,
                    linewidth: 1,
                    plottype: 2,
                    trackPrice: true,
                    color: 'blue'
                },
                plot_1: {
                    linestyle: 1,
                    visible: true,
                    linewidth: 2,
                    plottype: 2,
                    trackPrice: true,
                    color: 'red'
                },
            },
            precision: 4,
            inputs: {}
        },
        styles:
        {
            plot_0:
            {
                title: 'First plot',
                histogramBase: 0,
            },
            plot_1:
            {
                title: 'Second plot',
                histogramBase: 0,
            },
        },
        inputs: [],
    },
    constructor: function() {
        this.main = function(context, inputCallback) {
            this._context = context;
            this._input = inputCallback;

            var value = Math.random() * 200 - 100;
            var colorIndex = value > 0 ? 0 : 1;

            return [0, value, colorIndex];
        }
    }
}
```

## Advanced Shapes use

![images/advanced_shapes_use.png](images/advanced_shapes_use.png)

```javascript
{
    name: 'fxn',
    metainfo: {
        _metainfoVersion: 51,
        isTVScript: false,
        isTVScriptStub: false,
        is_hidden_study: false,
        defaults: {
            styles: {
                plot_0: {
                  color: '#FF5252',
                  textColor: '#2196F3',
                  visible: true
                }
            },
            inputs: {}
        },
        plots: [
            {
                id: 'plot_0',
                type: 'shapes'
            }
        ],
        styles: {
            plot_0: {
              isHidden: false,
              location: 'Bottom',
              plottype: 'shape_circle',
              size: 'tiny',
              text: 'Monday',
              title: 'Shapes'
            }
        },
        description: 'fxn',
        shortDescription: 'fxn',
        is_price_study: false,
        inputs: [],
        id: 'fxn@tv-basicstudies-1',
        scriptIdPart: '',
    },
    constructor: function() {
        this.main = function(context, inputCallback) {
            var studyValue = Math.random() * 100 - 50;
            var shouldBeShapeVisible = studyValue > 0;

            // 1 is plot value, it'll be displayed in legend of the indicator
            // NaN means that there is no value for that plot and shape should be hidden for that bar
            var plotValue = shouldBeShapeVisible ? 1 : NaN;
            return [plotValue];
        }
    }
},
```

## Advanced OHLC style

![images/OHLC_plots.png](images/OHLC_plots.png)

```javascript
{
    name: 'Equity',
    metainfo: {
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
            {
                id: 'plot_4',
                type: 'ohlc_colorer',
                palette: 'palette_0',
                target: 'plotcandle_0',
            }
        ],

        palettes: {
            palette_0: {
                colors: [
                    { name: 'Up Color' },
                    { name: 'Down Color' }
                ],

                valToIndex: {
                    '1': 0,
                    '-1': 1
                }
            }
        },

        ohlcPlots: {
            plotcandle_0: {
                title: 'Candles',
            },
        },

        defaults: {
            ohlcPlots: {
                plotcandle_0: {
                    borderColor: '#000000',
                    color: '#000000',
                    drawBorder: false,
                    drawWick: true,
                    plottype: 'ohlc_candles',
                    visible: true,
                    wickColor: '#737375'
                },
            },

            palettes: {
                palette_0: {
                    colors: [
                        { color: '#6ba583' },
                        { color: '#d75442' }
                    ]
                }
            },

            precision: 4,
            inputs: {},
        },
        styles: {},
        inputs: [],
    }
}
```
