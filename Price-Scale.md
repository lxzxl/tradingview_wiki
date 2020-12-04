The Charting Library allows users to have up to 8 price scales (or price axis).

## Formatting

Prices are formatted according to the symbol information - [minmov, pricescale, minmove2, fractional](Symbology#minmov-pricescale-minmove2-fractional).

You can also apply custom formatting using [numeric_formatting](Widget-Constructor#numeric_formatting).

## Style and default settings

You can change the color of the price scale, its font and default options using the [overrides](Widget-Constructor#overrides). Look for `scalesProperties` in the [list of overrides](Overrides).

## Instrument currency

### Displaying instrument currency

You can display symbol currency on the price scale. It is quite straightforward. You just need to assign a currency code to the [currency_code](Symbology#currency_code) field in the symbol information.

### Currency conversion

The library provides a user interface for selecting the currency in which the instrument is displayed. Here are the steps to implement the currency conversion:

1. Add two additional fields to the symbol information: [currency_code](Symbology#currency_code) and [original_currency_code](Symbology#original_currency_code)
1. Provide a list of [available currencies](JS-Api#currency_codes).
1. Consider the [currencyCode](JS-Api#resolvesymbolsymbolname-onsymbolresolvedcallback-onresolveerrorcallback-extension) that is passed to the `resolveSymbol` method.

The price scale displays instrument currency and users can click it and select another currency from the drop-down. When another currency is selected, the `resolveSymbol` method is called with the same `symbolInfo`, but the `extension` argument has `currency_code` of the selected currency.

The actual conversion algorithms can vary and you need to implement it by yourself. Typically, you can choose from 2 algorithms:

1. Constant currency rate. You get the current currency rate and multiply each bar to this value. It is quite simple, but gives wrong results for historical bars when the exchange rate could be absolutely different.
1. Corresponding currency rate. You request historical currency rates from the server and multiply each bar to its corresponding currency rate.

**Remark**: Both algorithms can be implemented relatively easily if all instruments and FX rates have the same time zone. If the time zone varies for instruments or FX rates, you need to find an appropriate way to match the correct corresponding rate to the bar.
