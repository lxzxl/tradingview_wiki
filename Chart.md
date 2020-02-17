## Default instrument and resolution

Change the default symbol (instrument) and resolution (time interval).

Minimum supported resolution is 1 second.

[symbol, interval](Widget-Constructor#symbol-interval)

## Default visible range (timeframe)

Change time range of bars for the default resolution

[timeframe](Widget-Constructor#timeframe)

## Default visible range for resolutions

Change time range of bars when the resolution is changed by the user. A sample is available here:

[onIntervalChanged()](Chart-Methods#onintervalchanged)

## Initial timezone

You can set the default timezone. It can be changed by the user in the menu.

[timezone](Widget-Constructor#timezone)

## Chart colors

Customize the colors of the chart so that it matches your site design.

1. [Toolbar color](Toolbars)
1. Chart color at the start - [overrides](Widget-Constructor#overrides), on the fly - [Chart Style properties](Chart-Style-Properties)
1. [CSS Color Themes](CSS-Color-Themes)

## Default properties of a chart

You can change any available properties in the properties dialog.

1. [Initially](Widget-Constructor#overrides)
1. [On the fly](Widget-Methods#applyoverridesoverrides)

## Show/hide chart elements

Certain chart elements (toolbars, buttons, other controls) can be hidden if you don't need them.

1. Most of the chart elements can be shown/hidden by using [Featuresets](Featuresets)
1. You can add [your own CSS](Widget-Constructor#custom_css_url)

## Initial list of favorite intervals / chart styles

You can select the intervals and chart styles that will be shown in the top toolbar by default. A user can change it if `items_favoriting` is enabled in the [Featuresets](Featuresets).

[favorites](Widget-Constructor#favorites)

## Resolutions that are displayed in the menu

1. The complete [list of resolutions](JS-Api#supported_resolutions) is provided in the configuration of the datafeed
1. Resolutions are enabled or disabled in the list being based on the [symbol information](Symbology#supported_resolutions)
1. Initial list of favorite resolutions [can be adjusted](Widget-Constructor#favorites)

## Context menu

You can add new elements to the context menu or hide the existing items.

[onContextMenu(callback)](Widget-Methods#oncontextmenucallback)
