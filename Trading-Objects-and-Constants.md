:chart: All content on this page applies to [Trading Terminal](Trading-Terminal) only.

**NOTE:** If you use TypeScript - you can import these constants/interfaces/types from the `broker-api.d.ts` file.

## Broker Configuration

### configFlags: object

This is an object that should be passed in the constructor of the Trading Terminal to [broker_config](Widget-Constructor#broker_config). Each field should have a boolean value (`true`/`false`):

* `supportReversePosition`

    *Default:* `false`

    Broker supports reversing of a position.
    If it is not supported by broker, the reverse position button will be hidden.

* `supportNativeReversePosition`

    *Default:* `false`

    Broker natively supports reversing of a position.
    If it is not natively supported by broker, Chart will place a reversing order.

* `supportClosePosition`

    *Default:* `false`

    Broker supports closing of a position.
    If it is not supported by broker, Chart will have the close button, but it will place a closing order.

* `supportPartialClosePosition`

    *Default:* `false`

    Broker supports partial closing of a position.

* `supportPartialCloseTrade`

    *Default:* `false`

    Broker supports partial closing of a trade.

* `supportPLUpdate`

    *Default:* `true`

    Broker provides PL for a position. If the broker calculates profit/loss by itself it should call [plUpdate](Trading-Host#plupdatepositionid-pl) as soon as PL is changed.
    Otherwise Chart will calculate PL as a difference between the current trade and an average price of the position.

* `supportMargin`

    *Default:* `false`

    Broker supports margin. If the broker supports margin it should call [marginAvailableUpdate](Trading-Host#marginavailableupdatemarginavailable) when the Trading Terminal subscribes using [subscribeMarginAvailable](Broker-API#subscribemarginavailable).

* `supportOrderBrackets`

    *Default:* `false`

    Broker supports brackets (take profit and stop loss) for orders.

* `supportCryptoBrackets`

    *Default:* `false`

    Broker supports brackets (take profit and stop loss) for crypto orders.
    If this flag is set to `true` the Chart will display additional fields in the order ticket.

* `supportPositionBrackets`

    *Default:* `false`

    Broker supports brackets (take profit and stop loss orders) for positions.
    If this flag is set to `true` the Chart will display an Edit button for positions and add `Edit position...` to the context menu of a position.

* `supportTradeBrackets`

    *Default:* `false`

    Broker supports brackets for trades (take profit and stop loss orders).
    If this flag is set to `true` the Chart will display an Edit button for trades (individual positions) and add `Edit position...` to the context menu of a trade.

* `supportTrailingStop`

    *Default:* `false`

    Broker supports trailing stop orders.
    If this flag is set to `true`, then the chart displays trailing stop orders and a user can place a trailing stop order using the Order Dialog.

* `supportPositions`

    *Default:* `true`

    Broker supports positions.
    If it is set to `false`, the Positions tab in the Account Manager will be hidden.

* `supportTrades`

    *Default:* `false`

    Broker supports individual positions (trades).
    If it is set to `true`, there will be two tabs in the Account Manager - Individual Positions and Net Positions.

* `requiresFIFOCloseTrades`

    *Default:* `false`

    Trading account requires closing of trades in FIFO order.

* `supportCloseTrade`

    *Default:* `false`

    Individual positions (trades) can be closed.

* `supportMultiposition`

    *Default:* `false`

    Supporting multiposition prevents creating the default implementation for a reversing position.

* `showQuantityInsteadOfAmount`

    *Default:* `false`

    This flag can be used to change "Amount" to "Quantity" in the Order Dialog

* `supportCryptoExchangeOrderTicket`

    *Default:* `false`

    Whether the account is used to exchange(trade) crypto currencies.
    This flag switches the Order Dialog to the Crypto Exchange mode. It adds second currency quantity control, currency labels etc.

* `supportLevel2Data`

    *Default:* `false`

    Level2 data is used for DOM widget. `subscribeDepth` and `unsubscribeDepth` should be implemented.

* `supportMarketOrders`

    *Default:* `true`

    This flag adds market orders type to the Order Dialog.

* `supportLimitOrders`

    *Default:* `true`

    This flag adds limit orders type to the Order Dialog.

* `supportStopOrders`

    *Default:* `true`

    This flag adds stop orders type to the Order Dialog.

* `supportStopOrdersInBothDirections`

    *Default:* `false`

    Whether stop orders should behave like Market-if-touched in both directions. Enabling this flag removes the direction check from the order dialog.

* `supportStopLimitOrders`

    *Default:* `false`

    This flag adds stop-limit orders type to the Order Dialog.

* `supportMarketBrackets`

    *Default:* `true`

    Using this flag you can disable brackets for market orders.

* `supportModifyOrder`

    *Default:* `true`

    **Deprecated** Using this flag you can disable modification of the existing order.

* `supportModifyOrderPrice`

    *Default:* `true`

    Using this flag you can disable existing order's price modification.

* `supportEditAmount`

    *Default:* `true`

    Using this flag you can disable existing order's quantity modification.

* `supportModifyBrackets`

    *Default:* `true`

    Using this flag you can disable existing order's brackets modification. If you set it to `false`,
    additional fields will be disabled in the Order Dialog on the chart,
    and 'Modify' button will be hidden from the chart and in the Account Manager.

* `supportModifyDuration`

    *Default:* `false`

    Using this flag you can enable modification of the duration of the existing order.

* `supportModifyTrailingStop`

    *Default:* `true`

    Broker supports modifying trailing stop orders.

* `supportAddBracketsToExistingOrder`

    *Default:* `true`

    Using this flag you can disable adding brackets to the existing order.

* `supportBalances`

    *Default:* `false`

    Used for crypto currencies only. Allows to get crypto balances for an account. Balances are displayed as the first table of the Account Summary tab.

* `supportDisplayBrokerNameInSymbolSearch`

    *Default:* `true`

    Display broker symbol name in the symbol search. You may usually want to disable it if broker symbols are the same or you are using internal numbers as broker symbol names.

* `supportCancellingBothBracketsOnly`

    *Default:* `false`

    Cancelling a bracket (take profit or stop loss) cancels it's pair.

* `supportPlaceOrderPreview`

    *Default:* `false`

    Broker provides the estimated commission, fees, margin and other order information before placing the order without actually placing it.

* `supportModifyOrderPreview`

    *Default:* `false`

    Broker provides the estimated commission, fees, margin and other order information before modifying the order without actually modifying it.

* `supportLeverage`

    *Default:* `false`

    Broker supports leverage. If the flag is set to `true`, a leverage input field will appear in the Order Widget. Click on the input field will activate a dedicated Leverage Dialog.

* `supportOrdersHistory`

    *Default:* `false`

    Broker supports orders history. If it is set to `true`, there will be an additional tab in the Account Manager - Orders History.
    The `ordersHistory` method should be implemented. It should return a list of orders with the `filled`, `cancelled` and `rejected` statuses from previous trade sessions.

* `closePositionCancelsOrders`

    *Default:* `false`

    Closing a position cancels it's brackets.

* `supportOnlyPairPositionBrackets`

    *Default:* `false`

    `Stop Loss` and `Take Profit` are added or removed only together.

* `showNotificationsLog`

    *Default:* `true`

    Using this flag you can show/hide the `Notifications log` tab in the account manager.

* `positionPLInInstrumentCurrency`

    *Default:* `false`

    Using this flag you can display PL in instrument currency.

* `supportConfirmations`

    *Default:* `false`

    With this flag you can show a checkbox to disable the confirmation dialog display

* `supportExecutions`

    *Default:* `false`

    Broker supports executions.
    If this flag is set to `true` the Chart will display executions.

### durations: array of objects

List of expiration options of orders. It is optional. Do not set it if you don't want the durations to be displayed in the Order Dialog.
The objects have the following keys: `{ name, value, hasDatePicker?, hasTimePicker?, default?, supportedOrderTypes? }`.

* `name`: String. Localized title of the duration. The title will be displayed in the Durataion control of the Order Dialog.
* `value`: String. Duration identifier.
* `hasDatePicker`: Boolean. If it is set to `true`, then the Display date control in the Order Dialog for this duration type will be dispalyed.
* `hasTimePicker`: Boolean. If it is set to `true`, then the Display time control in the Order Dialog for this duration type will be dispalyed.
* `default`: Boolean. Default duration. Only one duration object in the durations array can have a `true` value for this field. The default duration will be used when the user places orders in the silent mode and it will be the selected one when the user opens the Order Dialog for the first time.
* `supportedOrderTypes`: Array of [OrderType](#ordertype). A list of types of orders for which this duration type will be displayed in the Duration control of the Order Dialog. Default value is `[OrderType.Limit, OrderType.Stop, OrderType.StopLimit]`.

Example:

```javascript
durations: [{ name: 'DAY', value: 'DAY' }, { name: 'WEEK', value: 'WEEK', default: true }, { name: 'GTC', value: 'GTC' }, { name: 'FOK', value: 'FOK', supportedOrderTypes: [OrderType.Market] }]
```

### customNotificationFields: array of strings

Optional field. You can use it if you have custom fields in orders or positions that should be taken into account when showing notifications.

For example, if you have field `additionalType` in orders and you want the chart to show a notification when it is changed, you should set:

```javascript
customNotificationFields: ['additionalType']
```

### customUI

This optional field can be used to replace the standard Order dialogs and the Add Protection dialogs with your own.
Values of the following two fields are functions that are called by the Trading Terminal to show the dialogs. Each function shows a dialog and returns a ```Promise``` object that should be resolved when the operation is finished or cancelled.

**NOTE:** The returned ```Promise``` object should be resolved with either `true` or `false` value.

```ts
customUI: {
    showOrderDialog?: (order: Order, focus?: OrderTicketFocusControl) => Promise<boolean>;
    showPositionDialog?: (position: Position | Trade, brackets: Brackets, focus?: OrderTicketFocusControl) => Promise<boolean>;
    showCancelOrderDialog?: (order: Order) => Promise<boolean>;
    showClosePositionDialog?: (position: Position) => Promise<boolean>;
}
```

## Order

Describes a single order.

* `id` : String
* `symbol` : String
* `type` : [OrderType](#ordertype)
* `side` : [Side](#side)
* `qty` : Double
* `status` : [OrderStatus](#orderstatus)
* `limitPrice` : double
* `stopPrice` : double
* `avgPrice` : double
* `filledQty` : double
* `parentId` : String. If order is a bracket parentOrderId should contain base order/position id.
* `parentType`: [ParentType](#parenttype)
* `stopType`: [StopType](#stoptype) It should be set to 1 (StopType.TrailingStop) for trailing stop orders.
* `duration`: [OrderDuration](#orderduration)
* `customFields`: [CustomInputFieldsValues](#custominputfieldsvalues)
* `isClose`: Boolean. It is set to `true`, if the order closes a position.

## Position

Describes a single position.

* `id`: String. Usually id should be equal to brokerSymbol
* `symbol` : String
* `qty` : positive number
* `side`: [Side](#side)
* `avgPrice` : number

## Trade

Describes a single trade (individual position).

* `id`: String. Usually id should be equal to brokerSymbol
* `symbol` : String
* `date`: number (UNIX timestamp in milliseconds)
* `qty` : Double positive
* `side`: [Side](#side)
* `price` : number

## Execution

Describes a single execution. Execution is a mark on a chart that displays trade information.

* `symbol` : String
* `price` : number
* `time`: Date
* `side` : [Side](#side)
* `qty` : number

## ActionMetaInfo

Describes a single action to put it into a dropdown or a context menu. It is a structure.

* `text` : String
* `checkable` : Boolean. Set it to true if you need a checkbox.
* `checked` : Boolean. Value of the checkbox.
* `checkedStateSource`: function. Getter is executed to get current checkbox value.
* `enabled`: Boolean
* `action`: function. Action is executed when user clicks the item. It has 1 argument - value of the checkbox if exists.

## OrderPreviewSection

Describes a single order preview section. Order preview can have multiple sections that are divided by separators and may have titles.

* `rows` - array of order preview items [OrderPreviewSectionRow](#OrderPreviewSectionRow)[]. Each item is a row of the.section table.
* `header` - optional title of the section.

## OrderPreviewSectionRow

OrderPreviewSectionRow - Describes a single row of a section table of the order preview.

* `title` - Description of the item.
* `value` - Formatted value of the item.

## OrderType

Constants describing an order status.

```javascript
OrderType.Limit = 1
OrderType.Market = 2
OrderType.Stop = 3
OrderType.StopLimit = 4
```

## Side

Constants describing an order/execution side.

```javascript
Side.Buy = 1
Side.Sell = -1
```

## ParentType

Constants describing a bracket order.

```javascript
ParentType.Order = 1
ParentType.Position = 2
```

## StopType

Constants describing a stop order type.

```javascript
StopType.StopLoss = 0
StopType.TrailingStop = 1
```

## OrderStatus

Constants describing an order status.

```javascript
OrderStatus.Canceled = 1 // order is canceled
OrderStatus.Filled = 2 // order is fully executed
OrderStatus.Inactive = 3 // bracket order is created but waiting for a base order to be filled
OrderStatus.Placing = 4 // order is not created on a broker side yet
OrderStatus.Rejected = 5 // order is rejected for some reason
OrderStatus.Working = 6 // order is created but not executed yet
```

## OrderDuration

Duration or expiration of an order.

* `type`: string identifier from the list that you pass to [durations](#orderduration)
* `datetime`: number

## LeverageInfoParams

Object with the values of the current order's settings. Used by the broker to provide [leverageInfo](#leverageInfo).

* `symbol`: string;
* `orderType`: [OrderType](#ordertype);
* `side`: [Side](#side)
* `customFields`?: [CustomInputFieldsValues](#CustomInputFieldsValues);

## LeverageInfo

Object with the leverage information for the current order.

* `title`: string used as a Leverage Dialog's title.
* `leverage`: number;
* `min`: number;
* `max`: number;
* `step`: number;

## LeveragePreviewResult

Object with messages describing the leverage value set by the user.

* `infos`?: string[];
* `warnings`?: string[];
* `errors`?: string [];

## CryptoBalance

Object that describes a single crypto balance.

* `symbol`: string;
* `total`: number;
* `available`: number;
* `longName?`: string;
* `btcValue?`: number;

## DOMEObject

Object that describes a single DOM response.

* `snapshot`: Boolean

    Positive value means that previous data should be cleaned

* `asks`: array of DOMELevel sorted by price in ascending order
* `bids`: array of DOMELevel sorted by price in ascending order

## DOMELevel

Single DOM price level object.

* `price`: double
* `volume`: double

## OrderTicketFocusControl

Constants that are used to set the focus when you open standard Order dialog or Position dialog.

```javascript
OrderTicketFocusControl.LimitPrice = 1 // focus limit price for orders
OrderTicketFocusControl.StopPrice = 2 // focus stop price for orders
OrderTicketFocusControl.TakeProfit = 3 // focus take profit control
OrderTicketFocusControl.StopLoss = 4 // focus stop loss control
OrderTicketFocusControl.Quantity = 5 // focus quantity for orders
```

## Brackets

* `stopLoss`: double
* `takeProfit`: double
* `trailingStopPips`: double

## Formatter

An object with `format` method that can be used to format the number to a string.

## CheckboxFieldMetaInfo

An object that describes a custom checkbox field.

* `inputType`: 'Checkbox'
* `id`: string
* `title`: string
* `value`: boolean
* `supportModify`: boolean
* `help`: string
* `saveToSettings`: boolean

## CustomInputFieldsValues

An object that contains the results of broker specific user inputs (for example a digital signature). There are two possible kinds of custom fields: an input field with a checkbox and a custom combobox.

```javascript
{
    [fieldId: string]: TextWithCheckboxValue | string
}
```

`TextWithCheckboxValue` is an object that is used for the input field with a checkbox and has two properties:

* `text`: string
* `checked`: boolean

The result of a custom combobox is always a `string` that is entered by a user.

## TextWithCheckboxFieldMetaInfo

An object that describes a custom input field with a checkbox.

* `inputType`: 'TextWithCheckBox'
* `id`: string
* `title`: string
* `placeHolder?`: string
* `value`: TextWithCheckboxValue
* `validator?`: (value: string) => PositiveBaseInputFieldValidatorResult | NegativeBaseInputFieldValidatorResult
* `customInfo`: TextWithCheckboxFieldCustomInfo

## TextWithCheckboxValue

An object that contains initial values for the custom input field with a checkbox.

* `text`: string
* `checked`: boolean

## TextWithCheckboxFieldCustomInfo

An object that describes additional settings for the custom input field with a checkbox.
Using `asterix` property you can manage input type. If `asterix` is set to `true` then a password input will be rendered.

* `checkboxTitle`: string
* `asterix`: boolean

## CustomComboBoxMetaInfo

An object that describes a custom combobox.
The value of ComboBox will be saved and will be used as a default value the next time you open the Order Dialog or panel, if `saveToSettings` is set to `true`.

* `inputType`: 'ComboBox'
* `id`: string
* `title`: string
* `items`: CustomComboBoxItem[]
* `saveToSettings?`: boolean

## CustomComboBoxItem

An object that describes an item of the custom combobox.

* `text`: string
* `value`: string

## PositiveBaseInputFieldValidatorResult

An object that describes a positive validation result.

* `valid`: true

## NegativeBaseInputFieldValidatorResult

An object that describes a negative validation result.

* `valid`: false
* `errorMessage`: string

## PlaceOrderResult

An object that describes a place order result.

* `orderId`: string

## QuantityMetainfo

An object that describes the quantity field step and boundaries.

* `min`: number
* `max`: number
* `step`: number
* `uiStep?`: number. Step for scrolling.
* `default?`: number. It is a default quantity value.
