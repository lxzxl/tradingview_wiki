We do our best to make every next version fully compatible with the previous one, but sometimes big changes requires you to make minor changes in your code when upgrading to a new version.

_Note: you can check the Charting Library version by executing `TradingView.version()` in a browser console._

Here is the list of breaking changes:

<!-- markdownlint-disable no-emphasis-as-header -->

## Version 19

_Note: container_id has been marked deprecated. It's now preferable to switch to/use container instead. Container can now be either still be an id or be an HTMLElement you'd like the widget to be attached to._

**Trading Terminal**

- [Trading Host](Trading-Host) `defaultDropdownMenuActions` options have been changed. Options `selectAnotherBroker` and `disconnect` have been removed.

- The return value of the method `buttonDropdownActions` in the [Trading Host](Trading-Host) has been changed from `BindPopupMenuActionDescription[]` to array of [ActionMetaInfo](Trading-Objects-and-Constants#ActionMetaInfo).

- The `orderDialogOptions` object has been removed from the Broker's Configuration. Please use the `getOrderDialogOptions` method to customize the Order dialog.
- The `className` field has been removed from the [Account Manager column description](Account-Manager#Column-description). Use the [alignment](Account-Manager#alignment) field to control the alignment of the cell value.
- `force_session_rebuild` field in the symbol info has been removed

- Count and type of [getBars](JS-Api#getbarssymbolinfo-resolution-periodparams-onhistorycallback-onerrorcallback) arguments has been changed - `from`, `to` and `firstDataRequest` arguments have been combined into the `periodParams` object.
    To quickly switch to the new version, you need to replace the following code

    ```javascript
        // ...

        getBars(symbolInfo, resolution, from, to, onHistoryCallback, onErrorCallback, firstDataRequest) {
            // your code here
        }

        // ...
    ```

     with the following code:

    ```javascript
        // ...

        getBars(symbolInfo, resolution, periodParams, onHistoryCallback, onErrorCallback) {
            let { from, to, firstDataRequest } = periodParams;
            // your code here
        }

        // ...
    ```

- The `to` date in [getBars](JS-Api#getbarssymbolinfo-resolution-periodparams-onhistorycallback-onerrorcallback) is not inclusive from now. The `from` date is still inclusive. It means that you don't need to include bars with `time == to` in the response.

- Arguments of `ctx.new_sym` method in custom indicators have been changed and now you don't need to pass the third argument (it might break the indicator).
    To quickly fix this up, find all use cases for the `new_sym` method and make sure that only 2 arguments are passed to it (instead of three or more).
    For example, if you previously had `ctx.new_sym(newSym, PineJS.Std.period(this._context), PineJS.Std.period(this._context))`, you need to replace it with `ctx.new_sym(newSym, PineJS.Std.period(this._context))`.

## Version 18

- Field `futures_regex` from [configurationData](JS-Api#onreadycallback) has been removed, please use [symbols_grouping](JS-Api#symbols_grouping) instead.

**Trading Terminal**

- `contextMenuEvent` type in `contextMenuActions` in `AccountManagerInfo` interface has been changed from JQueryEventObject to MouseEvent.

- `accountsList` and `account` have been removed from Account Manager Info. They have been replaced with methods `currentAccount`, `setCurrentAccount` and `accountsMetainfo` in broker's API.

- Method `fullUpdate` in the Trading Host has been renamed to `currentAccountUpdate`.

- Method `showClosePositionDialog` has been removed.

- [Trading Host](Trading-Host) method `floatingTradingPanelVisibility` has been renamed to `sellBuyButtonsVisibility`.

- [Trading Host](Trading-Host) `defaultDropdownMenuActions` options have been changed. Option `showFloatingToolbar` has been renamed to `showSellBuyButtons`.

- Flag `supportOrderPreview` has been renamed to `supportPlaceOrderPreview`.

- Method [setPoints](Shape-Api#setpointspoints) now behaves the same way as [createMultipointShape](Chart-Methods#createmultipointshapepoints-options) for all tools. Previously it could change some other properties like width instead on moving points to their new places.

## Version 17

- The orders response has been split into [orders](Broker-API#orders-promiseorder) and [ordersHistory](Broker-API#ordershistory-promiseorder).
- [Widget Method](Widget-Methods) `setLanguage(locale)` has been removed.
- The argument of `onIntervalChanged` event have been modified: type of `timeframe` field has been changed to [TimeFrameValue](Chart-Methods#onIntervalChanged).
- Featureset `same_data_requery` has been removed, please use [resetData() method](Chart-Methods#resetdata) to refresh the data.
- `charting_library/charting_library.min.js` and `charting_library/charting_library.min.d.ts` files have been renamed to `charting_library/charting_library.js` and `charting_library/charting_library.d.ts` accordingly.
- The Chart Method [removeEntity](Chart-Methods#removeentityentityid-options) now can be undone by the user by default. To disable this, please use `disableUndo` field in the new argument `options`.

**Trading Terminal**

- Flag `supportBottomWidget` has been removed from Broker Configuration `configFlags` object. To remove the Account Manager the `trading_account_manager` featureset should be used.

## Version 16 (changed versioning)

- Action `tmzProperties` from [executeActionById](Chart-Methods#executeactionbyidactionid) and [getCheckableActionState](Chart-Methods#getcheckableactionstateactionid) methods is removed.
- Chart method `createStudy` options for `priceScale` have been changed. `left` and `right` have been renamed to `new-left` and `new-right`.
- Series API method `moveToOtherSourceScale` has been renamed to `changePriceScale`. New argument options are added: `new-left`, `new-right`, `no-scale`.
- Study API method `changePriceScale` argument options have been changed. `left` and `right` have been renamed to `new-left` and `new-right`. New argument option `entityId` has been added, it pins the study to the same price axis as a study with a corresponding `entityId`.

- Method `applyOverrides` of ChartWidget is disabled for "mainSeriesProperties.priceAxisProperties.*".

- Creating a study using `createStudy` of ChartWidgetApi can be undone by the user from now. You can disable it using `disableUndo` in `options`.

## Version 1.15

- Featureset `show_logo_on_all_charts` has been removed.
- Featureset `cl_feed_return_all_data` has been removed.
- Action `magnetAction` from [executeActionById](Chart-Methods#executeactionbyidactionid) and [getCheckableActionState](Chart-Methods#getcheckableactionstateactionid) methods is removed. Use [magnetEnabled](Widget-Methods#magnetenabled) instead.
- `callback` argument of [createStudy](Chart-Methods#createstudyname-forceoverlay-lock-inputs-overrides-options) has been removed.
- [createStudy](Chart-Methods#createstudyname-forceoverlay-lock-inputs-overrides-options) returns [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) instead of `entityId`.
- [Pane-Api](Pane-Api) method `getLeftPriceScale` is removed and replaced with `getLeftPriceScales` that returns an array of scales instead a single element.
- [Pane-Api](Pane-Api) method `getRightPriceScale` is removed and replaced with `getRightPriceScales` that returns an array of scales instead a single element.
- [setVisibleRange](Chart-Methods#setvisiblerangerange-options) method now returns a Promise object and don't accept a callback as the last argument.
- Priority of the [symbol](Widget-Constructor#symbol-interval) option has been made higher than the priority of the symbol from the [saved_data](Widget-Constructor#saved_data) option. Do not assign a value to the [symbol](Widget-Constructor#symbol-interval) option, if you don't want to override the symbol from [saved_data](Widget-Constructor#saved_data).
- Override `symbolWatermarkProperties` is not supported anymore. You can use [settings_adapter](Widget-Constructor#settings_adapter) with `symbolWatermark` key.
- `indicators_file_name` constructor option was removed. Use [custom_indicators_getter](Widget-Constructor#custom_indicators_getter) instead.
  We made this change to speed up the loading of the library and get rid of possible vulnerabilities that may occur when loading a file.
  You just need to move the code of your custom indicators from the JS file to the widget constructor, wrapping them in a function and a Promise

**Trading Terminal**

We've changed the broker's interaction flow. Please read the following carefully to understand what changes should be made in your code to switch to the new version.

Till now the Trading Terminal called broker adapter's methods (e.g. `placeOrder`, `modifyOrder`) when user clicked on Buy/Sell/Modify buttons. When calling these methods the Trading Terminal passed a `silently` argument. When `silently` was set to `true`, the broker adapter could send an order without showing the dialog. When it was set to `false`, the broker adapter had to invoke a method from the `host` to show the order ticket (or the Edit Position dialog).

Starting from 1.15 the Trading Terminal shows all dialogs by itself and invokes broker adapter's methods to send an order or a position to the broker's server. The reason for this change is that we've added an order panel that can be used to place an order at any time.
If you use your own Order dialog then you still need to make changes in your broker adapter's methods, but additionally you need to use `metainfo` to pass the dialog constructor to the Trading Terminal.

- Argument `silently` was removed from `placeOrder`, `modifyOrder`, `reversePosition`, `closePosition`, `closeTrade`, `cancelOrder`, `cancelOrders` methods of the [Broker API](Broker-API).

- Arguments `handler` and `options` were removed from `showOrderDailog` method of the [Trading Host](Trading-Host).

- Argument `handler` was removed from `showPositionBracketsDailog` method of the [Trading Host](Trading-Host).

- `supportCustomPlaceOrderTradableCheck` flag is no longer supported.

- We pass the parent order to `modifyOrder` if it exists. If child order’s details are required while modifying the order you can get back this behavior by enabling `always_pass_called_order_to_modify` featureset.

## Version 1.14

- [createButton](Widget-Methods#createButtonoptions) returns `HTMLElement` instead of `JQuery`.
- [createButton](Widget-Methods#createButtonoptions) must be used after [headerReady()](Widget-Methods#headerready) `Promise` is resolved.
- [getVisibleRange](Chart-Methods#getVisibleRange) returns `{from, to}` in the UTC timezone (it was a timezone selected on a chart before).
- Method `onready` was removed. You can use `window.addEventListener('DOMContentLoaded', callback, false)` instead.
- `saveAsSnapshot` parameter was removed from [saveChartToServer](Widget-Methods#savecharttoserveroncompletecallback-onfailcallback-options)

**TypeScript type definitions**

- `StudyInputValueType` type is renamed to `StudyInputValue`.

**Featureset**

- Starting from this version you are no longer able to use the `keep_left_toolbar_visible_on_small_screens` featureset. This featureset is removed and the left toolbar visibility no longer depends on the screen size.

## Version 1.13

- Action `takeScreenshot` from [executeActionById](Chart-Methods#executeactionbyidactionid) method is removed. Use [takeScreenshot](Widget-Methods#takescreenshot) method instead.
- Action `lockDrawingsAction` from [executeActionById](Chart-Methods#executeactionbyidactionid) and [getCheckableActionState](Chart-Methods#getcheckableactionstateactionid) methods is removed. Use [lockAllDrawingTools](Widget-Methods#lockalldrawingtools) instead.
- Action `hideAllDrawingsAction` from [executeActionById](Chart-Methods#executeactionbyidactionid) and [getCheckableActionState](Chart-Methods#getcheckableactionstateactionid) methods is removed. Use [hideAllDrawingTools](Widget-Methods#hidealldrawingtools) instead.
- Featureset `caption_buttons_text_if_possible` is enabled by default.
- Fixed an [issue](https://github.com/tradingview/charting_library/issues/2652) that was causing bars to shift. Time-shifted bars used to appear when daily bars had a negative exchange timezone offset along with a 24x7 session. If you have a workaround for this issue, please remove it before updating to this version.

## Version 1.12

**Charting Library**

- `charting_library/charting_library.min.js` is now [UMD](https://github.com/umdjs/umd) module.

    If you only inline this script into HTML then nothing has changed for you.
    If you import it as a module you should import `widget`, `version` and `onready` functions directly from it.

- `searchSymbolsByName` is removed from `JS-API`, use `searchSymbols` instead.

Study overrides:

- Overrides for `Overlay` should be applied only via `studies_overrides` (and `applyStudiesOverrides` in runtime). In the previous versions you had to use `overrides` and `applyOverrides`). See [Studies-Overrides](Studies-Overrides) page.
- Starting from this version you are no longer able to override `showStudyArguments` and `showLastValue` using `options` keyword.

**Trading Terminal**

- `hasHistory` flag is removed. Use `historyColumns` to display History in the Account Manager.

The following items are still supported in the Trading Terminal, but will be deprecated in future versions:

- `subscribePL` and `unsubscribePL`. The broker should call `plUpdate` method of the Host every time the profit is changed.
- `supportDOM` is removed. DOM widget visibility can be set using `dome_widget` featureset.

**The Trading Controller is replaced with [Broker API](Broker-API)**.

The following changes should be applied to your Trading Controller implementation to move to new Broker API:

- Method `setHost` is removed. Host should be passed to the constructor of Broker API.
- Method `buttonDropdownItems` is removed. Broker API should update [Broker API](Trading-Host) using `setButtonDropdownActions`.
- Methods `configFlags` and `durations` are removed. Use [Widget Constructor](Widget-Constructor) fields instead.
- All methods that returned `$.Deferred` should be modified to return Promise.
- Method `chartContextMenuItems` is renamed to `chartContextMenuActions`.
- Method `isTradable` changed to return a Promise instead of a Boolean value.
- All string constants ("working", "buy" etc.) should be replaced with the appropriate number of constants.
- Position `avg_price` renamed to `avgPrice`.
- `tradingController` field in the [Widget Constructor](Widget-Constructor) is removed. Use `brokerFactory` instead.

## Version 1.11

**Trading Terminal**

The following items are still supported in Trading Terminal, but will be deprecated in future versions:

- `supportDOME` renamed to `supportDOM`.
- The signature of `showClosePositionDialog has been changed.
- `showEditBracketsDialog` was renamed to `showPositionBracketsDialog`.The signature has been changed.

## Version 1.10

- Default behavior of Volume indicator was changed.

    **Previous behavior**: Volume indicator is added/removed when an instrument or a resolution is switched depending on volume support by the instrument. You can get back to this behavior by disabling `create_volume_indicator_by_default_once` featureset.

    **New behavior**: Volume indicator is added when an empty chart is loaded for the first time provided that it is supported by an active instrument.

## Version 1.9

- We don't compile Pine scripts anymore. You can still use scripts that were compiled earlier.

## Version 1.8 of Trading Terminal

- The chart can no longer show active orders only. Appropriate methods have been removed.
- `showOrderDialog` receives an object instead of arguments list
- `showSampleOrderDialog` removed, use [showOrderDialog](Trading-Host#showorderdialogorder-focus-promise) instead
- `showOrderDialog` removed from [Broker API](Broker-API), use `placeOrder` and `modifyOrder` receive `silently` argument instead
- `reversePosition`, `closePosition`, `cancelOrder` have an additional argument `silently`.

## Version 1.7

- Starting from this version calling `setSymbol` with the same symbol is no longer enough. You should call `onResetCacheNeededCallback` from `subscribeBars` first. Then you can use `setSymbol` or new `resetData` method of the chart.
- JSAPI protocol version 1 is not supported anymore. `nextTime` and `noData` must be provided.

## Version 1.5

- Added `source` argument to MACD. You should change MACD creation code to pass `source` also.

    `chartWidget.chart().createStudy('MACD', false, false, [12, 26, "close", 9])`

## Version 1.4

- Override `transparency` is not supported anymore. We added transparency support to every color. Use `rgba` form to define a color with transparency. Example:

    `"symbolWatermarkProperties.color" : "rgba(60, 70, 80, 0.05)"`

## Version 1.3

- Override `paneProperties.gridProperties.*` is not supported anymore.

    Please use `paneProperties.vertGridProperties.*` and `paneProperties.horzGridProperties.*`

- Override `mainSeriesProperties.candleStyle.wickColor` is not supported anymore.

    Use `mainSeriesProperties.candleStyle.wickUpColor` and `mainSeriesProperties.candleStyle.wickDownColor`

<!-- markdownlint-enable no-emphasis-as-header -->
