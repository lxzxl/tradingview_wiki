:chart: All content on this page is related to [Trading Terminal](Trading-Terminal) only.

Broker API is a key component that enables live trading. Its main purpose is to connect our charts with your trading logic. In terms of `JS`, it is an `object` which is expected to expose the specific interface. Here is a list of API's **methods** that Terminal is expected to have.

## Required Methods

### constructor(host)

The constructor of the Broker API usually takes [Trading Host](Trading-Host).

### positions : Promise<Position[]>

This method is called by the Trading Terminal to request [positions](Trading-Objects-and-Constants#position).

### orders : Promise<Order[]>

This method is called by the Trading Terminal to request [orders](Trading-Objects-and-Constants#order).

### ordersHistory : Promise<Order[]>

This method is called by the Trading Terminal to request orders history. It is expected that returned [orders](Trading-Objects-and-Constants#order) will have a final status (`rejected`, `filled`, `cancelled`). This method is optional. If you don't support orders history, please set `supportOrdersHistory` flag to `false`.

### executions(symbol) : Promise<Execution[]>

This method is called by the Trading Terminal to request [executions](Trading-Objects-and-Constants#execution).

### trades : Promise<Trade[]>

This method is called by the Trading Terminal to request [trades](Trading-Objects-and-Constants#trade) (individual positions).

### chartContextMenuActions(e)

- `e` is a context object passed by a browser

Chart can have a sub-menu `Trading` in the context menu. This method should return an array of [ActionMetaInfo](Trading-Objects-and-Constants#actionmetainfo) elements, each of them representing one context menu item.

### connectionStatus()

You don't need to return values other than `1` typically since the broker is already connected when you create the widget. You can use it if you want to display a spinner in the bottom panel while the data is being loaded.
Possible return values are:

```javascript
ConnectionStatus.Connected = 1
ConnectionStatus.Connecting = 2
ConnectionStatus.Disconnected = 3
ConnectionStatus.Error = 4
```

### isTradable(symbol): Promise\<boolean | IsTradableResult>

This function is required for the Floating Trading Panel. The ability to trade via the panel depends on the result of this function: `true` or `false`. You don't need to implement this method if all symbols can be traded.

If you want to show a custom message with the reason why the symbol cannot be traded then you can return an object `IsTradableResult`. It has the following keys: tradable (`true` or `false`), solutions(`TradableSolutions`), reason (`string`) and shortReason(`string`). Reason is displayed in the Order dialog while the shortReason is displayed in the legend.

`TradableSolutions` has one of the following keys:

- `changeAccount` - id of a sub-account suitable for trading the symbol

- `changeSymbol` - the symbol suitable for trading with current sub-account

### accountManagerInfo()

This function should return the information that will be used to build an Account manager.
See [Account manager](Account-Manager) for more information.

### placeOrder([order](Trading-Objects-and-Constants#order), confirmId): Promise\<PlaceOrderResult>

Method is called when a user wants to place an order. Order is pre-filled with partial or complete information. This function returns an object with the order id.

`confirmId` is passed if `supportPlaceOrderPreview` configuration flag is on.

### previewOrder([order](Trading-Objects-and-Constants#order))

Returns estimated commission, fees, margin and other information for the order without it actually being placed. The method is called if `supportPlaceOrderPreview` configuration flag is on.
The result will be an object with the following fields:

`OrderPreviewResult` - Describes the result of the order preview.

- `sections` : array of order preview sections, [OrderPreviewSection](Trading-Objects-and-Constants#OrderPreviewSection)[].
- `confirmId` : a unique identifier that should be passed to `placeOrder` method
- `warnings` : optional array of text warnings
- `errors` : optional array of text errors

### modifyOrder([order](Trading-Objects-and-Constants#order))

1. `order` is an order object to modify

Method is called when a user wants to modify an existing order.

`confirmId` is passed if `supportModifyOrderPreview` configuration flag is on.

### cancelOrder(orderId)

This method is called to cancel a single order with a given `id`.

### cancelOrders(symbol, side, ordersIds)

1. `symbol` - symbol string
1. `side`: [Side constant](Trading-Objects-and-Constants#side) or `undefined`
1. `ordersIds` - ids already collected by `symbol` and `side`

This method is called to cancel multiple orders for a `symbol` and `side`.

### leverageInfo([leverageInfoParams](Trading-Objects-and-Constants#leverageInfoParams))

This method is called to receive [leverageInfo](Trading-Objects-and-Constants#leverageInfo) from the broker.

### setLeverage(leverageSetParams)

1. `leverageSetParams` is an object similar to [leverageInfoParams](Trading-Objects-and-Constants#leverageInfoParams), but contains an additional `leverage: number` field, which holds the leverage value set by the user.

This method is called to send user's leverage value to the broker. The value should be verified and corrected on the broker's side if required, and sent back in the response.

### previewLeverage(leverageSetParams)

This method is called to receive [leveragePreviewResult](Trading-Objects-and-Constants#leveragePreviewResult) object which holds messages about the leverage value set by the user.

### editPositionBrackets(positionId, [brackets](Trading-Objects-and-Constants#brackets), customFields)

1. `positionId` is an ID of an existing position to be modified
1. `brackets` - new [brackets](Trading-Objects-and-Constants#brackets).
1. `customFields` - [CustomInputFieldsValues](Trading-Objects-and-Constants#CustomInputFieldsValues) or `undefined`

This method is called if `supportPositionBrackets` configuration flag is on. It shows a dialog that enables `take profit` and `stop loss` editing.

### closePosition(positionId, amount)

This method is called if `supportClosePosition` configuration flag is on. It allows to close the position by id.

The amount is specified if `supportPartialClosePosition` is `true` and the user wants to close only part of the position.

### reversePosition(positionId)

This method is called if `supportNativeReversePosition` configuration flag is on. It allows to reverse the position by id.

### editTradeBrackets(tradeId, [brackets](Trading-Objects-and-Constants#brackets))

1. `tradeId` is ID of existing trade to be modified
1. `brackets` - new [brackets](Trading-Objects-and-Constants#brackets).

This method is called if `supportTradeBrackets` configuration flag is on. It displays a dialog that enables take profit and stop loss editing.

### closeTrade(tradeId, amount)

This method is called if `supportCloseTrade` configuration flag is on. It allows to close the trade by id.

The amount is specified if `supportPartialCloseTrade` is `true` and the user wants to close only part of the trade.

### symbolInfo(symbol) : Deferred (or Promise)

1. `symbol` - symbol string

This method is called by the internal Order dialog, DOM panel and floating trading panel to get symbol information.

The result is an object with the following data:

- `qty` - object [QuantityMetainfo](Trading-Objects-and-Constants#QuantityMetainfo).
- `pipSize` - size of 1 pip (e.g., 0.0001 for EURUSD).
- `pipValue` - value of 1 pip for the instrument in the account currency.
- `minTick` - minimal price change (e.g., 0.00001 for EURUSD). Used for price fields.
- `description` - a description to be displayed in the dialog.
- `type` - instrument type, only `forex` matters - it enables negative pips. You can check that in the Order dialog.
- `domVolumePrecision` - number of decimal places of DOM asks/bids volume (optional, 0 by default).
- `marginRate` - the margin requirement for the instrument. A 3% margin rate should be represented as 0.03.
- `stopPriceStep` - minimal price change for stop price field of the Stop and Stop Limit order. If set it will override the minTick value.
- `limitPriceStep` - minimal price change for limit price field of the Limit and Stop Limit order. If set it will override the minTick value.
- `allowedDurations` - array of strings with valid duration values. You can check that in the Order dialog.
- `currency` - instrument currency that is displayed in the Order dialog
- `baseCurrency` - the first currency quoted in a currency pair. Used for crypto currencies only.
- `quoteCurrency` - the second currency quoted in a currency pair. Used for crypto currencies only.
- `bigPointValue` - The value represented by a full point of price movement in the contract currency. This value is used to calculate the Total Value (symbol currency) of the order.
- `units` - Units of quantity or amount. Displayed instead of the Units label in the Quantity/Amount field.

### accountsMetainfo() : or Promise

This method is called to get the accounts list.
The result contains an array of objects with the following fields:

1. `id`: AccountId - account id
1. `name`: string - account name
1. `currency`?: string - account currency
1. `currencySign`?: string which is a sign of account currency

### currentAccount() : AccountId

This method is called to get the id of current account.

### setCurrentAccount(id)

1. `id` is an ID of an existing sub-account

This method is called to change current account. If the account is changed synchronously `currentAccountUpdate` should be called, otherwise the connection status should be set to Connecting for the period of the account switching.

### subscribeEquity()

The method should be implemented if you use the standard Order dialog and support stop loss. Equity is used to calculate Risk in Percent.

Once this method is called the broker should provide equity (Balance + P/L) updates via [equityUpdate](Trading-Host#equityupdateequity) method.

### unsubscribeEquity()

The method should be implemented if you use the standard Order dialog and support stop loss.

Once this method is called the broker should stop providing equity updates.

### subscribeMarginAvailable()

The method should be implemented if you use the standard Order dialog and want to show the margin meter.

Once this method is called the broker should provide margin available updates via [marginAvailableUpdate](Trading-Host#marginavailableupdatemarginavailable) method.

### unsubscribeMarginAvailable()

The method should be implemented if you use the standard Order dialog want to show the margin meter.

Once this method is called the broker should stop providing margin available updates.

### subscribePipValue()

The method should be implemented if you use a standard Order dialog. `pipValues` is displayed in the Order info and it is used to calculate the Trade Value and risks. If this method is not implemented then `pipValue` from the `symbolInfo` is used in the order panel/dialog.

Once this method is called the broker should provide `pipValue` updates via [pipValueUpdate](Trading-Host#pipvalueupdatesymbol-pipValues) method.

### unsubscribePipValue()

The method should be implemented if you use a standard Order dialog and implement `subscribePipValue`.

Once this method is called the broker should stop providing `pipValue` updates.

## Optional methods

### getOrderDialogOptions(symbol): Promise\<OrderDialogOptions | undefined>

1. `symbol` - symbol string.

The method can be implemented if you use the standard Order dialog and want to customize it.

Use the `symbol` parameter to return customization options for a particular symbol.

The result is an object with options for the Order dialog:

- `showTotal`: boolean

    Using this flag you can change `Trade Value` to `Total` in the Order Info section of the Order dialog.

- `customFields`: (TextWithCheckboxFieldMetaInfo | CustomComboBoxMetaInfo | CheckboxFieldMetaInfo)[];

    Using `customFields` you can add additional input fields to the Order dialog.

Example:

```javascript
customFields: [
    {
        inputType: 'TextWithCheckBox',
        id: '2410',
        title: 'Digital Signature',
        placeHolder: 'Enter your personal digital signature',
        value: {
            text: '',
            checked: false,
        },
        customInfo: {
            asterix: true,
            checkboxTitle: 'Save',
        },
    }
]
```

### getPositionDialogOptions(): PositionDialogOptions

The method can be implemented if you want to customize the position dialog.

The result is an object with options for the position dialog.

- `customFields`: (TextWithCheckboxFieldMetaInfo | CustomComboBoxMetaInfo | CheckboxFieldMetaInfo)[];

    Using `customFields` you can add additional input fields to the position dialog.

## See Also

- [How to connect](Widget-Constructor#broker_factory) your trading controller to the chart
- [Trading Host](Trading-Host)
