## Overview

The Charting Library is meant to be used on your own site, with your own source of market data. It does NOT include any market data. If you want to display TradingView market data, please check our [widgets](https://www.tradingview.com/widget/).

Unlike simple charts, the primary aim of which is just displaying data, the Technical Analysis Charting Library gives users control over the chart.
Thus, market data connection API is designed in such a way, that all interactions (data requests, symbol information requests and symbol search) are initiated by the user.

## JS API

Market data connection API ([JS API](JS-Api)) is a set of methods that must be implemented in JavaScript.

All these methods are called by the library as needed.

The Charting Library expects to get an implementation of the JS API in the [datafeed](Widget-Constructor#datafeed) field of the constructor.

## UDF

If you don’t have sufficient JavaScript knowledge, or if you don’t yet have a Web-based server API that you can fetch data from, then you can use a ready-made [UDF adapter](UDF) that implements the [JS API](JS-Api) and makes simple HTTP(S) requests at the specified URL in a specific format. This adapter does not support data streaming out of the box (but it still can be added there).

Also, the UDF adapter can be used as an **example** implementation of the JS API. You can copy [its code](https://github.com/tradingview/charting_library/tree/master/datafeeds/udf) and start editing it.

## Go ahead

[Start implementing JS API if you have an existing Web API](JS-Api)

[Start with a predefined UDF adapter and implement a server-side API](UDF)
