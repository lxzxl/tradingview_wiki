## What is JS API

JS API is a set of JS methods that needs to be implemented in order to connect your data to the chart.

## How to start

You should create a JS object that fetches data from your server when the Charting Library calls its methods.

When you create an object that implements the described interface simply pass it to Library widget constructor through the [datafeed](Widget-Constructor#datafeed) argument.

The Charting Library caches historical data on its own. You don't need to implement a client-side cache by yourself.

## Methods

1. [onReady](#onreadycallback)
1. [searchSymbols](#searchsymbolsuserinput-exchange-symboltype-onresultreadycallback)
1. [resolveSymbol](#resolvesymbolsymbolname-onsymbolresolvedcallback-onresolveerrorcallback-extension)
1. [getBars](#getbarssymbolinfo-resolution-periodparams-onhistorycallback-onerrorcallback)
1. [subscribeBars](#subscribebarssymbolinfo-resolution-onrealtimecallback-subscriberuid-onresetcacheneededcallback)
1. [unsubscribeBars](#unsubscribebarssubscriberuid)
1. [getMarks](#getmarkssymbolinfo-from-to-ondatacallback-resolution)
1. [getTimescaleMarks](#gettimescalemarkssymbolinfo-from-to-ondatacallback-resolution)
1. [getServerTime](#getservertimecallback)
1. [getVolumeProfileResolutionForPeriod](#getvolumeprofileresolutionforperiodcurrentresolution-from-to-symbolinfo)

:chart: [Trading Terminal](Trading-Terminal) specific:

1. [getQuotes](#getquotessymbols-ondatacallback-onerrorcallback)
1. [subscribeQuotes](#subscribequotessymbols-fastsymbols-onrealtimecallback-listenerguid)
1. [unsubscribeQuotes](#unsubscribequoteslistenerguid)
1. [subscribeDepth](#subscribedepthsymbolinfo-callback-string)
1. [unsubscribeDepth](#unsubscribedepthsubscriberuid)

### onReady(callback)

1. `callback`: function(configurationData)
    1. `configurationData`: object (see below)

This call is intended to provide the object filled with the configuration data.
Charting Library assumes that you will call the callback function and pass your datafeed `configurationData` as an argument.
Configuration data is an object; for now, the following properties are supported:

#### exchanges

An array of exchange descriptors. Exchange descriptor is an object `{value, name, desc}`. `value` will be passed as `exchange` argument to [searchSymbols](#searchsymbolsuserinput-exchange-symboltype-onresultreadycallback).

`exchanges = []`  leads to the absence of the exchanges filter in Symbol Search list. Use `value = ""` if you wish to include all exchanges.

#### symbols_types

An array of filter descriptors. Filter descriptor is an object `{name, value}`. `value` will be passed as `symbolType` argument to [searchSymbols](#searchsymbolsuserinput-exchange-symboltype-onresultreadycallback).

`symbols_types = []`  leads to the absence of filter types in Symbol Search list. Use `value = ""` if you wish to include all filter types.

#### supported_resolutions

An array of supported resolutions. Resolution must be a string. Format is described in another [article](Resolution).

`supported_resolutions = undefined` or `supported_resolutions = []` leads to resolution widget including the default content.

Example: `["1", "15", "240", "D", "6M"]` will give you "1 minute, 15 minutes, 4 hours, 1 day, 6 months" in resolution widget.

#### currency_codes

An array of supported currencies for currency conversion. Each item might have one of the following types:

* an object with properties `{ id: string, code: string, logoUrl?: string, description?: string }`.

    Note that `id` and `code` fields are mandatory whereas `logoUrl` and `description` are optional.

    `logoUrl` is a URL to an image of the currency. SVG logos are preferable, but please make sure that a provided image fits fine in the currency select control (for raster images the size of 24x24px is expected).

* a string. The library will automatically convert it to `{ id: value, code: value }` object.

Example: `["USD", "EUR", "GBP"]`.

Example: `[{ id: "USD", code: "USD", description: "$" }, { id: "EUR", code: "EUR", description: "€" }]`.

#### units

An object that lists supported unit groups. Each group can have several unit objects. Each unit object should have the following fields:

* `id`: string. Unique id.
* `name`: string. Short name.
* `description`: string. Description.

Example:

```javascript
{
    weight: [
        { id: 'kg', name: 'kg', description: 'Kilograms' },
        { id: 'lb', name: 'lb', description: 'Pounds'},
    ]
}
```

#### supports_marks

Boolean showing whether your datafeed supports marks on bars or not.

#### supports_timescale_marks

Boolean showing whether your datafeed supports timescale marks or not.

#### supports_time

Set this one to `true` if your datafeed provides server time (unix time). It is used to adjust Countdown on the Price scale.

#### symbols_grouping

Set it if you want to group symbols in the symbol search. Represents an object where keys are symbol types and values ​​are regular expressions (each regular expression should divide an instrument name into 2 parts: a root and an expiration).

Sample:

```javascript
    {
      "futures": `/^(.+)([12]!|[FGHJKMNQUVXZ]\d{1,2})$/`,
      "stock": `/^(.+)([12]!|[FGHJKMNQUVXZ]\d{1,2})$/`,
    }
```

It will be applied to the instruments with `futures` and `stock` as a `type`.

### searchSymbols(userInput, exchange, symbolType, onResultReadyCallback)

1. `userInput`: string. It is text entered by user in the symbol search field.
1. `exchange`: string. The requested exchange (chosen by user). Empty value means no filter was specified.
1. `symbolType`: string. The requested symbol type: `index`, `stock`, `forex`, etc (chosen by user).
    Empty value means no filter was specified.
1. `onResultReadyCallback`: function(result)
    1. `result`: array (see below)

This call is intended to provide the list of symbols that match the user's search query. `result` is expected to look like the following:

```javascript
[
    {
        "symbol": "<short symbol name>",
        "full_name": "<full symbol name>", // e.g. BTCE:BTCUSD
        "description": "<symbol description>",
        "exchange": "<symbol exchange name>",
        "ticker": "<symbol ticker name, optional>",
        "type": "stock" // or "futures" or "crypto" or "forex" or "index"
    },
    {
        //    .....
    }
]
```

If no symbols are found, then callback should be called with an empty array. See more details about `ticker` value [here](Symbology#ticker)

### resolveSymbol(symbolName, onSymbolResolvedCallback, onResolveErrorCallback, extension)

1. `symbolName`: string. Symbol name or `ticker` if provided.
1. `onSymbolResolvedCallback`: function([SymbolInfo](Symbology#symbolinfo-structure))
1. `onResolveErrorCallback`: function(reason)
1. `extension`: optional object with additional parameters. It has the following fields:
    1. `currencyCode`: string. It may be provided to indicate the currency for conversion if `currency_codes` configuration
    field is set and `currency_code` is provided in the original symbol information. Read more about [currency conversion](Price-Scale#currency-conversion).
    1. `unitId`: string. It may be provided to indicate the unit for conversion if `units` configuration
        field is set and `unit_id` is provided in the original symbol information.

Charting Library will call this function when it needs to get [SymbolInfo](Symbology#symbolinfo-structure) by symbol name.

### getBars(symbolInfo, resolution, periodParams, onHistoryCallback, onErrorCallback)

1. `symbolInfo`: [SymbolInfo](Symbology#symbolinfo-structure) object
1. `resolution`: string
1. `periodParams`: object with the following fields:
    1. `from` - unix timestamp, leftmost required bar time (inclusive end)
    1. `countBack` - the exact amount of bars to load, should be considered a higher priority than `from` if your datafeed supports it (see below). It may not be specified if the user requests a specific time period.
    1. `to`: unix timestamp, rightmost required bar time (not inclusive)
    1. `firstDataRequest`: boolean to identify the first call of this method.
        When it is set to `true` you can ignore `to` (which depends on browser's `Date.now()`) and return bars up to the latest bar.
1. `onHistoryCallback`: callback function for historical data. It should be called **just once**. This function has 2 arguments:
    1. Array of `bars`. See below.
    1. `Meta information`: See below.
1. `onErrorCallback`: callback function for errors. The only argument of this function is a text error message.

This function is called when the chart needs a history fragment defined by dates range.

`Bar` is an object with the following fields:

1. `time`: number. Amount of **milliseconds** since Unix epoch start in **UTC** timezone. `time` for daily bars is expected to be a trading day (not session start day) at 00:00 UTC. Charting Library adjusts time according to [Session](Symbology#session) from SymbolInfo.  `time` for monthly bars is the first trading day of the month without the time part.
1. `open`: number. Bar's open value
1. `high`: number. Bar's high value
1. `low`: number. Bar's low value
1. `close`: number. Bar's close value
1. `volume`: number. Bar's volume value

`Meta information` is an object with the following fields:

1. `noData`: boolean. This flag should be set if there is no data in the requested period.
1. `nextTime`: unix timestamp (UTC). Time of the next bar in the history. It should be set if the requested period represents a gap in the data. Hence there is available data prior to the requested period.

#### Note about `periodParams`

Since 18 version the library provides `countBack` parameter, that could be used to improve data load performance.

`from` parameter was and remains inaccurate, since it does not fully take into account the trading session of the symbol. The reason for an inaccurate calculation is speed (an accurate calculation has a linear time complexity, and an inaccurate calculation has a constant complexity).

`countBack` the minimum number of bars that the chart needs (it can be slightly larger) to fill the visible range (except for Japanese charts), and along with the `to` date (which is the date of the last loaded bar), you can easily provide required data in just one request.

It is recommended to consider the priority of `countBack` higher than the priority of `from`, i.e. you must return data in the range `[from, to)`, but the number of bars should not be less than `countBack`. If the number of bars is less than `countBack`, the chart will call `getBars` again.

If your data provider can return the exact amount of bars, it is preferable to use `countBack` over the `from` date for greater efficiency:

* Example 1: let's say the chart requests 300 bars with the range `[2019-06-01T00:00:00..2020-01-01T00:00:00]` in the request.
    If you have only 250 bars in the requested period (`[2019-06-01T00:00:00..2020-01-01T00:00:00]`) and you return these 250 bars, the chart will make another request to load 50 more bars preceding `2019-06-01T00:00:00` date.

* Example 2: let's say the chart requests 300 bars with the range `[2019-06-01T00:00:00..2020-01-01T00:00:00]` in the request.
    If you don't have bars in the requested period, you don't need to return `noData: true` with the `nextTime` parameter equal to the next available data. You can simply return 300 bars prior to `2020-01-01T00:00:00` even if this data is before the `from` date.

### subscribeBars(symbolInfo, resolution, onRealtimeCallback, subscriberUID, onResetCacheNeededCallback)

1. `symbolInfo`: [SymbolInfo](Symbology#symbolinfo-structure) object
1. `resolution`: string
1. `onRealtimeCallback`: function(bar)
    1. `bar`: object `{time, close, open, high, low, volume}`
1. `subscriberUID`: object
1. `onResetCacheNeededCallback` *(since version 1.7)*: function() to be executed when bar data has changed

Charting Library calls this function when it wants to receive real-time updates for a symbol. The Library assumes that you will call `onRealtimeCallback` every time you want to update the most recent bar or to add a new one.

**Remark**: When you call `onRealtimeCallback` with bar having time equal to the most recent bar's time then the entire last bar is replaced with the `bar` object you've passed into the call.

Example:

1. The most recent bar is `{1419411578413, 10, 12, 9, 11}`
1. You call `onRealtimeCallback({1419411578413, 10, 14, 9, 14})`
1. Library finds out that the bar with the time `1419411578413` already exists and is the most recent one
1. Library replaces the entire bar making the most recent bar `{1419411578413, 10, 14, 9, 14}`

**Remark 2**: It is possible either to update the most recent bar or to add a new one with `onRealtimeCallback`.
You'll get an error if you call this function when trying to update a historical bar.

**Remark 3**: There is no way to change historical bars once they've been received by the chart currently.

### unsubscribeBars(subscriberUID)

1. `subscriberUID`: object

Charting Library calls this function when it doesn't want to receive updates for this subscriber any more. `subscriberUID` will be the same object that Library passed to `subscribeBars` before.

### getMarks(symbolInfo, from, to, onDataCallback, resolution)

*Optional.*

1. `symbolInfo`: [SymbolInfo](Symbology#symbolinfo-structure) object
1. `from`: unix timestamp (UTC). Leftmost visible bar's time.
1. `to`: unix timestamp (UTC). Rightmost visible bar's time.
1. `onDataCallback`: function(array of `mark`s)
1. `resolution`: string

The Library calls this function to get [marks](Marks#marks-on-bars) for visible bars range.

The Library assumes that you will call `onDataCallback` only once per `getMarks` call.

`mark` is an object that has the following properties:

* `id`: unique mark ID. It will be passed to a [respective callback](Widget-Methods#subscribeevent-callback) when user clicks on a mark
* `time`: unix time, UTC
* `color`: `red` | `green` | `blue` | `yellow` | `{ border: '#ff0000', background: '#00ff00' }`
* `text`: mark popup text. HTML supported
* `label`: a letter to be printed on a mark. **Note:** the label text is only shown on marks with a diameter of at least 14 pixels. If you require that the label is always shown then use a `minSize` of at least 14 for all marks. Up to two characters can be displayed if the `two_character_bar_marks_labels` feature is enabled.
* `labelFontColor`: color of a letter on a mark
* `minSize`: minimum mark size (diameter, pixels) (default value is `5`)

A few marks per bar are allowed (for now, the maximum is `10`). Marks outside of the bars are not allowed.

**Remark**: This function will be called only if you confirmed that your back-end is [supporting marks](#supports_marks).

### getTimescaleMarks(symbolInfo, from, to, onDataCallback, resolution)

*Optional.*

1. `symbolInfo`: [SymbolInfo](Symbology#symbolinfo-structure) object
1. `from`: unix timestamp (UTC). Leftmost visible bar's time.
1. `to`: unix timestamp (UTC). Rightmost visible bar's time.
1. `onDataCallback`: function(array of `mark`s)
1. `resolution`: string

The Library calls this function to get [timescale marks](Marks#marks-on-the-timescale) for visible bars range.

The Library assumes that you will call `onDataCallback` only once per `getTimescaleMarks` call.

`mark` is an object that has the following properties:

* `id`: unique mark ID. Will be passed to a [respective callback](Widget-Methods#subscribeevent-callback) when user clicks on a mark
* `time`: unix time, UTC
* `color`: `red` | `green` | `blue` | `yellow` | ... | `#000000`
* `label`: a letter to be printed on a mark. Single character
* `tooltip`: array of text strings. Each element of the array is a new text line of a tooltip.

Only one mark per bar is allowed. Marks outside of the bars are not allowed.

**Remark**: This function will be called only if you confirmed that your back-end is [supporting marks](#supports_timescale_marks).

### getServerTime(callback)

1. `callback`: function(unixTime)

This function is called if the configuration flag `supports_time` is set to `true` when the Charting Library needs to know the server time.

The Charting Library assumes that the callback is called once.

The time is provided without milliseconds.

It is used to display Countdown on the price scale.

Example: `1445324591`.

### getVolumeProfileResolutionForPeriod(currentResolution, from, to, symbolInfo)

*Optional.*

1. `currentResolution`: string. Currently selected resolution on the chart
1. `from`: unix timestamp (UTC). Time of the leftmost visible bar
1. `to`: unix timestamp (UTC). Time of the rightmost visible bar
1. `symbolInfo`: [SymbolInfo](Symbology#symbolinfo-structure) object

The library calls this function to get the resolution that will be used to calculate the Volume Profile Visible Range indicator. Usually you might want to implement this method to calculate the indicator more accurately. The implementation really depends on how much data you can transfer to the library and the depth of data in your data feed.

**Remark**: If this function is not provided the library uses `currentResolution`.

## [Trading Terminal](Trading-Terminal) specific

### getQuotes(symbols, onDataCallback, onErrorCallback)

:chart: *[Trading Terminal](Trading-Terminal) specific.*

1. `symbols`: array of symbols names
1. `onDataCallback`: function(array of `data`)
    1. `data`: [symbol quote data](Quotes#symbol-quote-data)
1. `onErrorCallback`: function(reason)

This function is called when the Charting Library needs quote data. The charting library assumes that `onDataCallback` is called once when all the requested data is received.

### subscribeQuotes(symbols, fastSymbols, onRealtimeCallback, listenerGUID)

:chart: *[Trading Terminal](Trading-Terminal) specific.*

1. `symbols`: array of symbols that should be updated rarely (once per minute). These symbols are included in the watchlist but they are not visible at the moment.
1. `fastSymbols`: array of symbols that should be updated frequently (once every 10 seconds or more often)
1. `onRealtimeCallback`: function(array of `data`)
    1. `data`: [symbol quote data](Quotes#symbol-quote-data)
1. `listenerGUID`: unique identifier of the listener

Trading Terminal calls this function when it wants to receive real-time quotes for a symbol.

The Charting Library assumes that you will call `onRealtimeCallback` every time you want to update the quotes.

### unsubscribeQuotes(listenerGUID)

:chart: *[Trading Terminal](Trading-Terminal) specific.*

1. `listenerGUID`: unique identifier of the listener

Trading Terminal calls this function when it doesn't want to receive updates for this listener anymore.

`listenerGUID` will be the same object that the Library passed to `subscribeQuotes` before.

### subscribeDepth(symbolInfo, callback): string

:chart: *[Trading Terminal](Trading-Terminal) specific.*

1. `symbolInfo`: [SymbolInfo](Symbology#symbolinfo-structure) object
1. `callback`: function(depth)
    1. `depth`: object `{snapshot, asks, bids}`
        * `snapshot`: Boolean - if `true` `asks` and `bids` have full set of depth, otherwise they contain only updated levels.
        * `asks`: Array of `{price, volume}` (must be sorted by `price` in asc order)
        * `bids`: Array of `{price, volume}` (must be sorted by `price` in asc order)

Trading Terminal calls this function when it wants to receive real-time level 2 (DOM) for a symbol. The Charting Library assumes that you will call the `callback` every time you want to update DOM data.

This method should return a unique identifier (`subscriberUID`) that will be used to unsubscribe from the data.

### unsubscribeDepth(subscriberUID)

:chart: *[Trading Terminal](Trading-Terminal) specific.*

1. `subscriberUID`: String

Trading Terminal calls this function when it doesn't want to receive updates for this listener anymore.

`subscriberUID` will be the same object that was returned from `subscribeDepth`.
