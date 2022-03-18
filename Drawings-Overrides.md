The complete list of drawings overrides with default values is presented here. You can change the default values using the `overrides` argument of the [widget constructor](Widget-Constructor#overrides). At the bottom of this list you will find a list of constants and abbreviations used in the values.

```javascript
// Icon
linetoolicon: {
    color: 'rgba( 61, 133, 198, 1)',
    size: 40,
    icon: 0x263A,
    angle: Math.PI * 0.5,
    scale: 1.0
},

// Curve
linetoolbezierquadro: {
    linecolor: 'rgba( 21, 153, 128, 1)',
    linewidth: 1.0,
    fillBackground: false,
    backgroundColor: 'rgba( 21, 56, 153, 0.5)',
    transparency: 50,
    linestyle: LINESTYLE_SOLID,
    extendLeft: false,
    extendRight: false,
    leftEnd: LINEEND_NORMAL,
    rightEnd: LINEEND_NORMAL
},

// Double Curve
linetoolbeziercubic: {
    linecolor: 'rgba( 21, 153, 128, 1)',
    linewidth: 1.0,
    fillBackground: false,
    backgroundColor: 'rgba( 21, 56, 153, 0.5)',
    transparency: 50,
    linestyle: LINESTYLE_SOLID,
    extendLeft: false,
    extendRight: false,
    leftEnd: LINEEND_NORMAL,
    rightEnd: LINEEND_NORMAL
},

// Trend Line
linetooltrendline: {
    linecolor: 'rgba( 21, 153, 128, 1)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    extendLeft: false,
    extendRight: false,
    leftEnd: LINEEND_NORMAL,
    rightEnd: LINEEND_NORMAL,
    showLabel: false,
    horzLabelsAlign: 'center',
    vertLabelsAlign: 'bottom',
    textcolor: 'rgba( 21, 119, 96, 1)',
    fontsize: 14,
    bold:false,
    italic:false,
    alwaysShowStats: false,
    showMiddlePoint: false,
    showPriceLabels: false,
    showPriceRange: false,
    showBarsRange: false,
    showDateTimeRange: false,
    showDistance:false,
    showAngle: false,
    statsPosition: STATS_POSITION_RIGHT,
},

// Info Line
linetoolinfoline: {
    linecolor: 'rgba( 21, 153, 128, 1)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    extendLeft: false,
    extendRight: false,
    leftEnd: LINEEND_NORMAL,
    rightEnd: LINEEND_NORMAL,
    showLabel: false,
    horzLabelsAlign: 'center',
    vertLabelsAlign: 'bottom',
    textcolor: 'rgba( 21, 119, 96, 1)',
    fontsize: 14,
    bold: false,
    italic: false,
    alwaysShowStats: true,
    showMiddlePoint: false,
    showPriceLabels: false,
    showPriceRange: true,
    showBarsRange: true,
    showDateTimeRange: true,
    showDistance: true,
    showAngle: true,
    statsPosition: STATS_POSITION_CENTER,
},

// Time Cycles
linetooltimecycles: {
    linecolor: 'rgba(21, 153, 128, 1)',
    linewidth: 1.0,
    fillBackground: true,
    backgroundColor: 'rgba(106, 168, 79, 0.5)',
    transparency: 50,
    linestyle: LINESTYLE_SOLID
},

// Sine Line
linetoolsineline: {
    linecolor: 'rgba( 21, 153, 128, 1)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID
},

// Trend Angle
linetooltrendangle: {
    linecolor: 'rgba( 21, 153, 128, 1)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    textcolor: 'rgba( 21, 119, 96, 1)',
    fontsize: 12,
    bold: false,
    italic: false,
    alwaysShowStats: false,
    showMiddlePoint: false,
    showPriceLabels: false,
    showPriceRange: false,
    showBarsRange: false,
    extendRight: false,
    extendLeft: false,
    statsPosition: STATS_POSITION_RIGHT,
},

// Disjoint Channel
linetooldisjointangle: {
    linecolor: 'rgba( 18, 159, 92, 1)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    fillBackground: true,
    backgroundColor: 'rgba( 106, 168, 79, 0.5)',
    transparency: 20,
    extendLeft: false,
    extendRight: false,
    leftEnd: LINEEND_NORMAL,
    rightEnd: LINEEND_NORMAL,
    textcolor: 'rgba( 18, 159, 92, 1)',
    fontsize: 12,
    bold: false,
    italic: false,
    showPrices: false,
    showPriceRange: false,
    showDateTimeRange: false,
    showBarsRange: false
},

// Flat Top/Bottom
linetoolflatbottom: {
    linecolor: 'rgba(171, 71, 188, 1)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    fillBackground: true,
    backgroundColor: 'rgba(171, 71, 188, 0.2)',
    transparency: 20,
    extendLeft: false,
    extendRight: false,
    leftEnd: LINEEND_NORMAL,
    rightEnd: LINEEND_NORMAL,
    textcolor: 'rgba(171, 71, 188, 1)',
    fontsize: 12,
    bold: false,
    italic: false,
    showPrices: false,
    showPriceRange: false,
    showDateTimeRange: false,
    showBarsRange: false
},

// Fib Spiral
linetoolfibspiral: {
    counterclockwise: false,
    linecolor: '#089981',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID
},

// Date Range
linetooldaterange: {
    linecolor: 'rgba( 21, 119, 96, 1)',
    linewidth: 1,
    textcolor: 'rgba( 255, 255, 255, 1)',
    fontsize: 12,
    fillLabelBackground: true,
    labelBackgroundColor: 'rgba(41, 98, 255, 0.9)',
    fillBackground: true,
    backgroundColor: 'rgba(41, 98, 255, 0.2)',
    backgroundTransparency: 60,
    drawBorder: false,
    borderColor: 'rgba(41, 98, 255, 0.9)',
    extendTop: false,
    extendBottom: false,
    showLabel: true,
},

// Price Range
linetoolpricerange: {
    linecolor: 'rgba( 21, 119, 96, 1)',
    linewidth: 1,
    textcolor: 'rgba( 255, 255, 255, 1)',
    fontsize: 12,
    fillLabelBackground: true,
    labelBackgroundColor: 'rgba(41, 98, 255, 0.9)',
    fillBackground: true,
    backgroundColor: 'rgba(41, 98, 255, 0.2)',
    backgroundTransparency: 60,
    drawBorder: false,
    borderColor: 'rgba(41, 98, 255, 0.9)',
    extendLeft: false,
    extendRight: false,
    showLabel: true,
},

// Date and Price Range
linetooldateandpricerange: {
    linecolor: 'rgba( 21, 119, 96, 1)',
    linewidth: 1,
    textcolor: 'rgba( 255, 255, 255, 1)',
    fontsize: 12,
    fillLabelBackground: true,
    labelBackgroundColor: 'rgba(41, 98, 255, 0.9)',
    fillBackground: true,
    backgroundColor: 'rgba(41, 98, 255, 0.2)',
    backgroundTransparency: 60,
    borderWidth: 1,
    drawBorder: false,
    borderColor: 'rgba( 21, 119, 96, 1)',
    showLabel: true,
},

// Short Position
linetoolriskrewardshort: {
    linecolor: 'rgba(120, 123, 134, 1)',
    linewidth: 1.0,
    textcolor: 'rgba(255, 255, 255, 1)',
    fontsize: 12,
    fillLabelBackground: true,
    labelBackgroundColor: 'rgba( 88, 88, 88, 1)',
    fillBackground: true,
    stopBackground: 'rgba(242, 54, 69, 0.2)',
    profitBackground: 'rgba(8, 153, 129, 0.2)',
    stopBackgroundTransparency: 80,
    profitBackgroundTransparency: 80,
    drawBorder: false,
    borderColor: 'rgba( 102, 123, 139, 1)',
    compact: false,
    riskDisplayMode: RISK_DISPLAY_MODE_PERCENTAGE,
    accountSize: 1000,
    lotSize: 1,
    risk: 25,
    alwaysShowStats: false,
    showPriceLabels: true,
},

// Long Position
linetoolriskrewardlong: {
    linecolor: 'rgba(120, 123, 134, 1)',
    linewidth: 1.0,
    textcolor: 'rgba(255, 255, 255, 1)',
    fontsize: 12,
    fillLabelBackground: true,
    labelBackgroundColor: 'rgba( 88, 88, 88, 1)',
    fillBackground: true,
    stopBackground: 'rgba(242, 54, 69, 0.2)',
    profitBackground: 'rgba(8, 153, 129, 0.2)',
    stopBackgroundTransparency: 80,
    profitBackgroundTransparency: 80,
    drawBorder: false,
    borderColor: 'rgba( 102, 123, 139, 1)',
    compact: false,
    riskDisplayMode: RISK_DISPLAY_MODE_PERCENTAGE,
    accountSize: 1000,
    lotSize: 1,
    risk: 25,
    alwaysShowStats: false,
    showPriceLabels: true,
},

// Arrow
linetoolarrow: {
    linecolor: 'rgba( 21, 119, 96, 1)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    extendLeft: false,
    extendRight: false,
    leftEnd: LINEEND_NORMAL,
    rightEnd: LINEEND_ARROW,
    showLabel: false,
    horzLabelsAlign: 'center',
    vertLabelsAlign: 'bottom',
    textcolor: 'rgba( 21, 119, 96, 1)',
    fontsize: 14,
    bold: false,
    italic: false,
    alwaysShowStats: false,
    showMiddlePoint: false,
    showPriceLabels: false,
    showPriceRange: false,
    showBarsRange: false,
    showDateTimeRange: false,
    showDistance: false,
    showAngle: false,
    statsPosition: STATS_POSITION_RIGHT,
},

// Ray
linetoolray: {
    linecolor: 'rgba( 21, 119, 96, 1)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    extendLeft: false,
    extendRight: true,
    leftEnd: LINEEND_NORMAL,
    rightEnd: LINEEND_NORMAL,
    showLabel: false,
    horzLabelsAlign: 'center',
    vertLabelsAlign: 'bottom',
    textcolor: 'rgba( 21, 119, 96, 1)',
    fontsize: 14,
    bold: false,
    italic: false,
    alwaysShowStats: false,
    showMiddlePoint: false,
    showPriceLabels: false,
    showPriceRange: false,
    showBarsRange: false,
    showDateTimeRange: false,
    showDistance: false,
    showAngle: false,
    statsPosition: STATS_POSITION_RIGHT,
},

// Extended Line
linetoolextended: {
    linecolor: 'rgba( 21, 119, 96, 1)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    extendLeft: true,
    extendRight: true,
    leftEnd: LINEEND_NORMAL,
    rightEnd: LINEEND_NORMAL,
    showLabel: false,
    horzLabelsAlign: 'center',
    vertLabelsAlign: 'bottom',
    textcolor: 'rgba( 21, 119, 96, 1)',
    fontsize: 14,
    bold: false,
    italic: false,
    alwaysShowStats: false,
    showMiddlePoint: false,
    showPriceLabels: false,
    showPriceRange: false,
    showBarsRange: false,
    showDateTimeRange: false,
    showDistance: false,
    showAngle: false,
    statsPosition: STATS_POSITION_RIGHT,
},

// Horizontal Line
linetoolhorzline: {
    linecolor: 'rgba( 21, 119, 96, 1)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    showPrice: true,
    showLabel: false,
    textcolor: 'rgba( 21, 119, 96, 1)',
    fontsize: 12,
    bold: false,
    italic: false,
    horzLabelsAlign: 'center',
    vertLabelsAlign: 'top'
},

// Horizontal Ray
linetoolhorzray: {
    linecolor: 'rgba( 21, 119, 96, 1)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    showPrice: true,
    showLabel: false,
    textcolor: 'rgba( 21, 119, 96, 1)',
    fontsize: 12,
    bold: false,
    italic: false,
    horzLabelsAlign: 'center',
    vertLabelsAlign: 'top'
},

// Vertical Line
linetoolvertline: {
    linecolor: 'rgba( 21, 119, 96, 1)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    extendLine: true,
    showTime: true,
    showLabel: false,
    horzLabelsAlign: 'right',
    vertLabelsAlign: 'top',
    textcolor: 'rgba( 21, 119, 96, 1)',
    textOrientation: 'vertical',
    fontsize: 14,
    bold: false,
    italic: false,
},

// Cross Line
linetoolcrossline: {
    linecolor: 'rgba( 21, 119, 96, 1)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    showPrice: true,
    showTime: true
},

// Cyclic Lines
linetoolcirclelines: {
    trendline: {
        visible: true,
        color: 'rgba( 128, 128, 128, 1)',
        linewidth: 1.0,
        linestyle: LINESTYLE_DASHED
    },
    linecolor: 'rgba( 128, 204, 219, 1)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID
},

// Fib Time Zone
linetoolfibtimezone: {
    horzLabelsAlign: 'right',
    vertLabelsAlign: 'bottom',
    baselinecolor: 'rgba( 128, 128, 128, 1)',
    linecolor: 'rgba( 0, 85, 219, 1)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    showLabels: true,
    fillBackground: false,
    transparency: 80,
    trendline: {
        visible: true,
        color: 'rgba( 128, 128, 128, 1)',
        linewidth: 1.0,
        linestyle: LINESTYLE_DASHED
    },
    level1-11: LEVELS_TYPE_C
},

// Text
linetooltext: {
    color: 'rgba( 21, 119, 96, 1)',
    fontsize: 14,
    fillBackground: false,
    backgroundColor: 'rgba( 91, 133, 191, 0.3)',
    backgroundTransparency: 70,
    drawBorder: false,
    borderColor: 'rgba( 102, 123, 139, 1)',
    bold: false,
    italic: false,
    fixedSize: true,
    wordWrap: false,
    wordWrapWidth: 200
},

// Anchored Text
linetooltextabsolute: {
    color: 'rgba( 21, 119, 96, 1)',
    fontsize: 14,
    fillBackground: false,
    backgroundColor: 'rgba( 155, 190, 213, 0.3)',
    backgroundTransparency: 70,
    drawBorder: false,
    borderColor: 'rgba( 102, 123, 139, 1)',
    bold: false,
    italic: false,
    wordWrap: false,
    wordWrapWidth: 200
},

// Balloon
linetoolballoon: {
    color: '#ffffff',
    backgroundColor: 'rgba(156, 39, 176, 0.7)',
    borderColor: 'rgba(156, 39, 176, 0.0)',
    fontsize: 14,
    transparency: 30
},

// Brush
linetoolbrush: {
    linecolor: '#00bcd4',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    smooth: 5,
    fillBackground: false,
    backgroundColor: 'rgba(0, 188, 212, 0.5)',
    transparency: 50,
    leftEnd: LINEEND_NORMAL,
    rightEnd: LINEEND_NORMAL
},

// Highlighter
linetoolhighlighter: {
    linecolor: 'rgba(236, 64, 122, 0.15)',
    smooth: 5,
    transparency: 85
},

// Polyline
linetoolpolyline: {
    linecolor: '#7e57c2',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    fillBackground: true,
    backgroundColor: 'rgba(126, 87, 194, 0.2)',
    transparency: 50,
    filled: false,
},

// Path
linetoolpath: {
    lineColor: 'rgba( 21, 119, 96, 1)',
    lineWidth: 2,
    lineStyle: LINESTYLE_SOLID,
    leftEnd: LINEEND_NORMAL,
    rightEnd: LINEEND_ARROW,
},

// Arrow Mark Left
linetoolarrowmarkleft: {
    color: 'rgba( 21, 119, 96, 1)',
    arrowColor: 'rgba( 21, 119, 96, 1)',
    fontsize: 14,
    bold: false,
    italic: false,
    showLabel: true,
},

// Arrow Mark Up
linetoolarrowmarkup: {
    color: '#089981',
    arrowColor: '#089981',
    fontsize: 14,
    bold: false,
    italic: false,
    showLabel: true,
},

// Arrow Mark Right
linetoolarrowmarkright: {
    color: 'rgba( 21, 119, 96, 1)',
    arrowColor: 'rgba( 21, 119, 96, 1)',
    fontsize: 14,
    bold: false,
    italic: false,
    showLabel: true,
},

// Arrow Mark Down
linetoolarrowmarkdown: {
    color: '#CC2F3C',
    arrowColor: '#CC2F3C',
    fontsize: 14,
    bold: false,
    italic: false,
    showLabel: true,
},

// Flag Mark
linetoolflagmark: {
    flagColor: 'rgba( 21, 119, 96, 1)'
},

// Note
linetoolnote: {
    markerColor: 'rgba( 21, 119, 96, 1)',
    textColor: '#ffffff',
    backgroundColor: 'rgba(41, 98, 255, 0.7)',
    backgroundTransparency: 0,
    borderColor: 'rgba( 21, 119, 96, 1)',
    fontSize: 14,
    bold: false,
    italic: false,
    fixedSize: true
},

// Anchored Note
linetoolnoteabsolute: {
    markerColor: 'rgba( 21, 119, 96, 1)',
    textColor: '#ffffff',
    backgroundColor: 'rgba(41, 98, 255, 0.7)',
    backgroundTransparency: 0,
    borderColor: 'rgba( 21, 119, 96, 1)',
    fontSize: 14,
    bold: false,
    italic: false,
    fixedSize: true
},

// Price Label
linetoolpricelabel: {
    color: '#ffffff',
    backgroundColor: 'rgba( 21, 119, 96, 1)',
    borderColor: 'rgba( 21, 119, 96, 1)',
    fontWeight: 'bold',
    fontsize: 14,
    transparency: 0,
},

// Price Note
linetoolpricenote: {
    showLabel: false,
    horzLabelsAlign: 'center',
    vertLabelsAlign: 'bottom',
    textColor: 'rgba( 21, 119, 96, 1)',
    fontSize: 14,
    bold: false,
    italic: false,
    lineColor: 'rgba( 21, 119, 96, 1)',
    priceLabelBackgroundColor: 'rgba( 21, 119, 96, 1)',
    priceLabelBorderColor: 'rgba( 21, 119, 96, 1)',
    priceLabelTextColor: '#ffffff',
    priceLabelFontSize: 12,
    priceLabelBold: false,
    priceLabelItalic: false,
},

// Arrow Marker
linetoolarrowmarker: {
    backgroundColor: '#1E53E5',
    textColor: '#1E53E5',
    bold: true,
    italic: false,
    fontsize: 16,
    showLabel: true,
},

// Rectangle
linetoolrectangle: {
    color: '#9c27b0',
    fillBackground: true,
    backgroundColor: 'rgba(156, 39, 176, 0.2)',
    linewidth: 1.0,
    transparency: 50,
    showLabel: false,
    horzLabelsAlign: 'left',
    vertLabelsAlign: 'bottom',
    textColor: '#9c27b0',
    fontSize: 14,
    bold: false,
    italic: false,
    extendLeft: false,
    extendRight: false,
},

// Rotated Rectangle
linetoolrotatedrectangle: {
    color: '#4caf50',
    fillBackground: true,
    backgroundColor: 'rgba(76, 175, 80, 0.2)',
    transparency: 50,
    linewidth: 1.0,
},

// Ellipse
linetoolellipse: {
    color: '#e91e63',
    fillBackground: true,
    backgroundColor: 'rgba(233, 30, 99, 0.2)',
    transparency: 50,
    linewidth: 1.0
},

// Arc
linetoolarc: {
    color: '#ab47bc',
    fillBackground: true,
    backgroundColor: 'rgba(171, 71, 188, 0.2)',
    transparency: 50,
    linewidth: 1.0
},

// Forecast
linetoolprediction: {
    linecolor: 'rgba( 21, 119, 96, 1)',
    linewidth: 1.0,

    sourceBackColor: 'rgba( 21, 119, 96, 1)',
    sourceTextColor: 'rgba(255, 255, 255, 1)',
    sourceStrokeColor: 'rgba( 21, 119, 96, 1)',

    targetStrokeColor: 'rgba( 21, 119, 96, 1)',
    targetBackColor: 'rgba( 21, 119, 96, 1)',
    targetTextColor: 'rgba( 255, 255, 255, 1)',

    successBackground: 'rgba(76, 175, 80, 1)',
    successTextColor: 'rgba( 255, 255, 255, 1)',

    failureBackground: 'rgba( 231, 69, 69, 0.5)',
    failureTextColor: 'rgba( 255, 255, 255, 1)',

    intermediateBackColor: 'rgba( 234, 210, 137, 1)',
    intermediateTextColor: 'rgba( 109, 77, 34, 1)',

    transparency: 10,
    centersColor: 'rgba( 32, 32, 32, 1)'
},

// Triangle
linetooltriangle: {
    color: '#f57c00',
    fillBackground: true,
    backgroundColor: 'rgba(245, 124, 0, 0.2)',
    transparency: 50,
    linewidth: 1.0
},

// Callout
linetoolcallout: {
    color: '#ffffff',
    backgroundColor: 'rgba(0, 151, 167, 0.7)',
    transparency: 50,
    linewidth: 1.0,
    fontsize: 14,
    bordercolor: 'rgba(0, 151, 167, 1)',
    bold: false,
    italic: false,
    wordWrap: false,
    wordWrapWidth: 200
},

// Parallel Channel
linetoolparallelchannel: {
    linecolor: 'rgba( 21, 119, 96, 1)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    extendLeft: false,
    extendRight: false,
    fillBackground: true,
    backgroundColor: 'rgba(41, 98, 255, 0.2)',
    transparency: 20,
    showMidline: true,
    midlinecolor: 'rgba( 21, 119, 96, 1)',
    midlinewidth: 1.0,
    midlinestyle: LINESTYLE_DASHED
},

// Elliott Impulse Wave (12345)
linetoolelliottimpulse: {
    degree: 7,
    showWave: true,
    color: 'rgba( 61, 133, 198, 1)',
    linewidth: 1
},

// Elliott Triangle Wave (ABCDE)
linetoolelliotttriangle: {
    degree: 7,
    showWave: true,
    color: 'rgba( 255, 152, 0, 1)',
    linewidth: 1
},

// Elliott Triple Combo Wave (WXYXZ)
linetoolelliotttriplecombo: {
    degree: 7,
    showWave: true,
    color: 'rgba( 106, 168, 79, 1)',
    linewidth: 1
},

// Elliott Correction Wave (ABC)
linetoolelliottcorrection: {
    degree: 7,
    showWave: true,
    color: 'rgba( 61, 133, 198, 1)',
    linewidth: 1
},

// Elliott Double Combo Wave (WXY)
linetoolelliottdoublecombo: {
    degree: 7,
    showWave: true,
    color: 'rgba( 106, 168, 79, 1)',
    linewidth: 1
},

// Bars Pattern
linetoolbarspattern: {
    color: 'rgba( 21, 119, 96, 1)',
    mode:BARS_MODE,
    mirrored: false,
    flipped: false
},

// Ghost Feed
linetoolghostfeed: {
    averageHL: 20,
    variance: 50,
    candleStyle: {
        upColor: '#6ba583',
        downColor: '#d75442',
        drawWick: true,
        drawBorder: true,
        borderColor: '#378658',
        borderUpColor: '#225437',
        borderDownColor: '#5b1a13',
        wickColor: 'rgba(120, 123, 134, 1)'
    },
    transparency: 50
},

// Pitchfork
linetoolpitchfork: {
    fillBackground: true,
    transparency: 80,
    style:PITCHFORK_STYLE_ORIGINAL,
    median: {
        visible: true,
        color: 'rgba( 165, 0, 0, 1)',
        linewidth: 1.0,
        linestyle: LINESTYLE_SOLID
    },
    extendLines: false,
    level0-8: LEVELS_TYPE_C
},

// Pitchfan
linetoolpitchfan: {
    fillBackground: true,
    transparency: 80,
    median: {
        visible: true,
        color: 'rgba( 165, 0, 0, 1)',
        linewidth: 1.0,
        linestyle: LINESTYLE_SOLID
    },
    level0-8: LEVELS_TYPE_C
},

// Gann Fan
linetoolgannfan: {
    showLabels: true,
    fillBackground: true,
    transparency: 80,
    level1-9: LEVELS_TYPE_F
},

// Gann Square
linetoolganncomplex: {
    fillBackground: false,
    arcsBackground: {
        fillBackground: true,
        transparency: 80
    },
    reverse: false,
    scaleRatio: '',
    showLabels: true,
    labelsStyle: {
        fontSize: 12,
        bold: false,
        italic: false,
    },
    levels: [/* 6 LEVELS_TYPE_D */],
    fanlines: [/* 11 LEVELS_TYPE_E */],
    arcs: [/* 11 LEVELS_TYPE_E */]
},

// Gann Square Fixed
linetoolgannfixed: {
    fillBackground: false,
    arcsBackground: {
        fillBackground: true,
        transparency: 80
    },
    reverse: false,
    levels: [/* 6 LEVELS_TYPE_D */],
    fanlines: [/* 11 LEVELS_TYPE_E */],
    arcs: [/* 11 LEVELS_TYPE_E */],
},

// Gann Box
linetoolgannsquare: {
    color: 'rgba( 21, 56, 153, 0.8)',
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    showTopLabels: true,
    showBottomLabels: true,
    showLeftLabels: true,
    showRightLabels: true,
    fillHorzBackground: true,
    horzTransparency: 80,
    fillVertBackground: true,
    vertTransparency: 80,
    reverse: false,
    fans: LEVELS_TYPE_A,
    hlevel1-7: LEVELS_TYPE_B,
    vlevel1-7: LEVELS_TYPE_B
},

// Fib Speed Resistance Fan
linetoolfibspeedresistancefan: {
    fillBackground: true,
    transparency: 80,
    grid: {
        color: 'rgba( 21, 56, 153, 0.8)',
        linewidth: 1.0,
        linestyle: LINESTYLE_SOLID,
        visible: true
    },
    linewidth: 1.0,
    linestyle: LINESTYLE_SOLID,
    showTopLabels: true,
    showBottomLabels: true,
    showLeftLabels: true,
    showRightLabels: true,
    reverse: false,
    hlevel1-7: LEVELS_TYPE_B,
    vlevel1-7: LEVELS_TYPE_B
},

// Fib Retracement
linetoolfibretracement: {
    showCoeffs: true,
    showPrices: true,
    fillBackground: true,
    transparency: 80,
    extendLines: false,
    extendLinesLeft: false,
    horzLabelsAlign: 'left',
    vertLabelsAlign: 'bottom',
    reverse: false,
    coeffsAsPercents: false,
    fibLevelsBasedOnLogScale: false,
    trendline: {
        visible: true,
        color: 'rgba(120, 123, 134, 1)',
        linewidth: 1.0,
        linestyle: LINESTYLE_DASHED
    },
    levelsStyle: {
        linewidth: 1.0,
        linestyle: LINESTYLE_SOLID
    },
    level1-24: LEVELS_TYPE_B
},

// Fib Channel
linetoolfibchannel: {
    showCoeffs: true,
    showPrices: true,
    fillBackground: true,
    transparency: 80,
    extendLeft: false,
    extendRight: false,
    horzLabelsAlign: 'left',
    vertLabelsAlign: 'middle',
    coeffsAsPercents: false,
    levelsStyle: {
        linewidth: 1.0,
        linestyle: LINESTYLE_SOLID
    },
    level1-24:  LEVELS_TYPE_B
},

// Projection
linetoolprojection: {
    showCoeffs: true,
    fillBackground: true,
    transparency: 80,
    color1: 'rgba(41, 98, 255, 0.2)',
    color2: 'rgba(156, 39, 176, 0.2)',
    linewidth: 1.0,
    trendline: {
        visible: true,
        color: 'rgba(149, 152, 161, 1)',
        linestyle: LINESTYLE_SOLID
    },
    level1: LEVELS_TYPE_C
},

// XABCD Pattern
linetool5pointspattern: {
    color: 'rgba( 21, 119, 96, 1)',
    textcolor: 'rgba( 255, 255, 255, 1)',
    fillBackground: true,
    backgroundColor: 'rgba( 21, 119, 96, 1)',
    fontsize: 12,
    bold: false,
    italic: false,
    transparency: 85,
    linewidth: 1.0
},

// Cypher Pattern
linetoolcypherpattern: {
    color: 'rgba( 21, 119, 96, 1)',
    textcolor: '#FFFFFF',
    fillBackground: true,
    backgroundColor: 'rgba( 21, 119, 96, 1)',
    fontsize: 12,
    bold: false,
    italic: false,
    transparency: 85,
    linewidth: 1.0
},

// Triangle Pattern
linetooltrianglepattern: {
    color: '#673AB7',
    textcolor: '#FFFFFF',
    fillBackground: true,
    backgroundColor: '#673AB7',
    fontsize: 12,
    bold: false,
    italic: false,
    transparency: 85,
    linewidth: 1.0
},

// ABCD Pattern
linetoolabcd: {
    color: 'rgba( 0, 155, 0, 1)',
    textcolor: 'rgba( 255, 255, 255, 1)',
    fontsize: 12,
    bold: false,
    italic: false,
    linewidth: 1.0
},

// Three Drives Pattern
linetoolthreedrivers: {
    color: '#673AB7',
    textcolor: 'rgba( 255, 255, 255, 1)',
    fillBackground: true,
    backgroundColor: 'rgba( 149, 40, 204, 0.5)',
    fontsize: 12,
    bold: false,
    italic: false,
    transparency: 50,
    linewidth: 1.0
},

// Head and Shoulders
linetoolheadandshoulders: {
    color: 'rgba( 69, 104, 47, 1)',
    textcolor: 'rgba( 255, 255, 255, 1)',
    fillBackground: true,
    backgroundColor: 'rgba( 69, 168, 47, 0.5)',
    fontsize: 12,
    bold: false,
    italic: false,
    transparency: 85,
    linewidth: 1.0
},

// Fib Wedge
linetoolfibwedge: {
    showCoeffs: true,
    fillBackground: true,
    transparency: 80,
    trendline: {
        visible: true,
        color: 'rgba( 128, 128, 128, 1)',
        linewidth: 1.0,
        linestyle: LINESTYLE_SOLID
    },
    level1-11: LEVELS_TYPE_C
},

// Fib Circles
linetoolfibcircles: {
    showCoeffs: true,
    fillBackground: true,
    transparency: 80,
    coeffsAsPercents: false,
    trendline: {
        visible: true,
        color: 'rgba(120, 123, 134, 1)',
        linewidth: 1.0,
        linestyle: LINESTYLE_DASHED
    },
    level1-11: LEVELS_TYPE_C
},

// Fib Speed Resistance Arcs
linetoolfibspeedresistancearcs: {
    showCoeffs: true,
    fillBackground: true,
    transparency: 80,
    fullCircles: false,
    trendline: {
        visible: true,
        color: 'rgba(120, 123, 134, 1)',
        linewidth: 1.0,
        linestyle: LINESTYLE_DASHED
    },
    level1-11: LEVELS_TYPE_C
},

// Trend-Based Fib Extension
linetooltrendbasedfibextension: {
    showCoeffs: true,
    showPrices: true,
    fillBackground: true,
    transparency: 80,
    extendLines: false,
    extendLinesLeft: false,
    horzLabelsAlign: 'left',
    vertLabelsAlign: 'bottom',
    reverse: false,
    coeffsAsPercents: false,
    fibLevelsBasedOnLogScale: false,
    trendline: {
        visible: true,
        color: 'rgba(120, 123, 134, 1)',
        linewidth: 1.0,
        linestyle: LINESTYLE_DASHED
    },
    levelsStyle: {
        linewidth: 1.0,
        linestyle: LINESTYLE_SOLID
    },
    level1-24: LEVELS_TYPE_B
},

// Trend-Based Fib Time
linetooltrendbasedfibtime: {
    showCoeffs: true,
    fillBackground: true,
    transparency: 80,
    horzLabelsAlign: 'right',
    vertLabelsAlign: 'bottom',
    trendline: {
        visible: true,
        color: 'rgba(120, 123, 134, 1)',
        linewidth: 1.0,
        linestyle: LINESTYLE_DASHED
    },
    level1-11: LEVELS_TYPE_C
},

// Modified Schiff Pitchfork
linetoolschiffpitchfork: {
    fillBackground: true,
    transparency: 80,
    style:PITCHFORK_STYLE_SCHIFF,
    median: {
        visible: true,
        color: 'rgba( 165, 0, 0, 1)',
        linewidth: 1.0,
        linestyle: LINESTYLE_SOLID
    },
    extendLines: false,
    level0-8: LEVELS_TYPE_C
},

// Schiff Pitchfork
linetoolschiffpitchfork2: {
    fillBackground: true,
    transparency: 80,
    style:PITCHFORK_STYLE_SCHIFF2,
    median: {
        visible: true,
        color: 'rgba( 165, 0, 0, 1)',
        linewidth: 1.0,
        linestyle: LINESTYLE_SOLID
    },
    extendLines: false,
    level0-8: LEVELS_TYPE_C
},

// Inside Pitchfork
linetoolinsidepitchfork: {
    fillBackground: true,
    transparency: 80,
    style:PITCHFORK_STYLE_INSIDE,
    median: {
        visible: true,
        color: 'rgba( 165, 0, 0, 1)',
        linewidth: 1.0,
        linestyle: LINESTYLE_SOLID
    },
    extendLines: false,
    level0-8: LEVELS_TYPE_C
},

// Regression Trend
linetoolregressiontrend: {
    styles: {
        upLine: {
            visible: true,
            color: 'rgba(41, 98, 255, 0.3)',
            linestyle: LINESTYLE_SOLID
        },
        downLine: {
            visible: true,
            color: 'rgba(41, 98, 255, 0.3)',
            linestyle: LINESTYLE_SOLID
        },
        baseLine: {
            visible: true,
            color: 'rgba(244, 67, 54, 0.3)',
            linestyle: LINESTYLE_SOLID
        },
        extendLines: false,
        showPearsons: true
    }
}
```

### Constants

These constants are used in the default properties of drawings. You cannot use their names directly. Use their values instead.

```javascript
LINESTYLE_SOLID = 0;
LINESTYLE_DOTTED = 1;
LINESTYLE_DASHED = 2;
LINESTYLE_LARGE_DASHED = 3;

LINEEND_NORMAL = 0;
LINEEND_ARROW  = 1;
LINEEND_CIRCLE = 2;

BARS_MODE = 0;
LINE_MODE = 1;
OPENCLOSE_MODE = 2;
LINEOPEN_MODE = 3;
LINEHIGH_MODE = 4;
LINELOW_MODE = 5;
LINEHL2_MODE = 6;

PITCHFORK_STYLE_ORIGINAL = 0;
PITCHFORK_STYLE_SCHIFF = 1;
PITCHFORK_STYLE_SCHIFF2 = 2;
PITCHFORK_STYLE_INSIDE = 3;

STATS_POSITION_LEFT = 0;
STATS_POSITION_CENTER = 1;
STATS_POSITION_RIGHT = 2;

RISK_DISPLAY_MODE_PERCENTAGE = 'percents';
RISK_DISPLAY_MODE_MONEY = 'money';

LEVELS_TYPE_A = {
    color: color,
    visible: visible
};

LEVELS_TYPE_B = {
    coeff: coeff,
    color: color,
    visible: visible
};

LEVELS_TYPE_C = {
    coeff: coeff,
    color: color,
    visible: visible,
    linestyle: linestyle,
    linewidth: linewidth
};

LEVELS_TYPE_D = {
    color: color,
    width: width,
    visible: visible
};

LEVELS_TYPE_E = {
    color: color,
    visible: visible,
    width: width,
    x: x,
    y: y
};

LEVELS_TYPE_F = {
    coeff1: coeff1,
    coeff2: coeff2,
    color: color,
    visible: visible,
    linestyle: linestyle,
    linewidth: linewidth
};
```
