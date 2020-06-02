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

* `supportReducePosition`

    *Default:* `false`

    Broker supports changing of a position without orders.

* `supportPLUpdate`

    *Default:* `false`

    Broker provides PL for a position. If the broker calculates profit/loss by itself it should call [plUpdate](Trading-Host#plupdatepositionid-pl) as soon as PL is changed.
    Otherwise Chart will calculate PL as a difference between the current trade and an average price of the position.

* `supportMargin`

    *Default:* `false`

    Broker supports margin. If the broker supports margin it should call [marginAvailableUpdate](Trading-Host#marginavailableupdatemarginavailable) when the Trading Terminal subscribes using [subscribeMarginAvailable](Broker-API#subscribemarginavailable).

* `supportOrderBrackets`

    *Default:* `false`

    Broker supports brackets (take profit and stop loss) for orders.
    If this flag is set to `true` the Chart will display additional fields in the order ticket and Modify button on a chart and in the Account Manager.

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
    If this flag is set to `true`, then the chart displays trailing stop orders and a user can place a trailing stop order using the Order Ticket.

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

    This flag can be used to change "Amount" to "Quantity" in the order dialog

* `supportLevel2Data`

    *Default:* `false`

    Level2 data is used for DOM widget. `subscribeDepth` and `unsubscribeDepth` should be implemented.

* `supportMarketOrders`

    *Default:* `true`

    This flag adds market orders type to the order dialog.

* `supportLimitOrders`

    *Default:* `true`

    This flag adds limit orders type to the order dialog.

* `supportStopOrders`

    *Default:* `true`

    This flag adds stop orders type to the order dialog.

* `supportStopLimitOrders`

    *Default:* `false`

    This flag adds stop-limit orders type to the order dialog.

* `supportMarketBrackets`

    *Default:* `true`

    Using this flag you can disable brackets for market orders. It is enabled by default.

* `supportModifyDuration`

    *Default:* `false`

    Using this flag you can enable modification of the duration of the existing order. It is disabled by default.

* `supportModifyOrder`

    *Default:* `true`

    Using this flag you can disable modification of the existing order. It is enabled by default.

* `supportAddBracketsToExistingOrder`

    *Default:* `true`

    Using this flag you can disable adding brackets to the existing order. It is enabled by default.

* `supportBalances`

    *Default:* `false`

    Using this flag you can disable adding brackets to the existing order. It is enabled by default.

* `cancellingBracketCancelsParentOrder`

    Broker cancels the base order if a stop loss or a take profit is cancelled.

* `cancellingOnePositionBracketsCancelsOther`

    Broker cancels the second protection order (stop loss or take profit) as well if the first one is cancelled by a user.

* `supportOrderPreview`

    *Default:* `false`

    Broker provides the estimated commission, fees, margin and other information for the order without it actually being placed.

* `closePositionCancelsOrders`

    *Default:* `false`

    Closing a position cancels it's brackets.

* `supportOnlyPairPositionBrackets`

    *Default:* `false`

    `Stop Loss` and `Take Profit` are added or removed only together.

### durations: array of objects

List of expiration options of orders. It is optional. Do not set it if you don't want the durations to be displayed in the order ticket.
The objects have the following keys: `{ name, value, hasDatePicker?, hasTimePicker?, default? }`.

Example:

```javascript
durations: [{ name: 'DAY', value: 'DAY' }, { name: 'WEEK', value: 'WEEK', default: true }, { name: 'GTC', value: 'GTC' }]
```

### customNotificationFields: array of strings

Optional field. You can use it if you have custom fields in orders or positions that should be taken into account when showing notifications.

For example, if you have field `additionalType` in orders and you want the chart to show a notification when it is changed, you should set:

```javascript
customNotificationFields: ['additionalType']
```

### orderDialogOptions

Optional field. An object with options for the order ticket. Using these options you can customize the order ticket.

* `showTotal`: boolean

    Using this flag you can change `Trade Value` to `Total` in the Order Info section of the order ticket.

* `customFields`: (TextWithCheckboxFieldMetaInfo | CustomComboBoxMetaInfo)[];

    Using `customFields` you can add additional input fields to the order ticket.

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

### positionDialogOptions

Optional field. An object with options for the position ticket. Using these options you can customize the position ticket.

* `customFields`: (TextWithCheckboxFieldMetaInfo | CustomComboBoxMetaInfo)[];

    Using `customFields` you can add additional input fields to the position ticket.

### customUI

This optional field can be used to replace the standard Order Ticket and the Add Protection dialogs with your own.
Values of the following two fields are functions that are called by the Trading Terminal to show the dialogs. Each function shows a dialog and returns a ```Promise``` object that should be resolved when the operation is finished or cancelled.

**NOTE:** The returned ```Promise``` object should be resolved with either `true` or `false` value.

```ts
customUI: {
    showOrderDialog?: (order: Order, focus?: OrderTicketFocusControl) => Promise<boolean>;
    showPositionDialog?: (position: Position | Trade, brackets: Brackets, focus?: OrderTicketFocusControl) => Promise<boolean>;
}
```

## Order

Describes a single order.

* `id` : String
* `symbol` : String
* `brokerSymbol` : String. Can be empty if broker symbol is the same as TV symbol.
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

## Position

Describes a single position.

* `id`: String. Usually id should be equal to brokerSymbol
* `symbol` : String
* `brokerSymbol` : String. Can be empty if broker symbol is the same as TV symbol.
* `qty` : positive number
* `side`: [Side](#side)
* `avgPrice` : number

## Trade

Describes a single trade (individual position).

* `id`: String. Usually id should be equal to brokerSymbol
* `symbol` : String
* `date`: number (UNIX timestamp in milliseconds)
* `brokerSymbol` : String. Can be empty if broker symbol is the same as TV symbol.
* `qty` : Double positive
* `side`: [Side](#side)
* `price` : number

## Execution

Describes a single execution. Execution is a mark on a chart that displays trade information.

* `symbol` : String
* `brokerSymbol` : String. Can be empty if broker symbol is the same as TV symbol.
* `price` : number
* `time`: Date
* `side` : [Side](#side)
* `qty` : number

## ActionMetainfo

Describes a single action to put it into a dropdown or a context menu. It is a structure.

* `text` : String
* `checkable` : Boolean. Set it to true if you need a checkbox.
* `checked` : Boolean. Value of the checkbox.
* `enabled`: Boolean
* `action`: function. Action is executed when user clicks the item. It has 1 argument - value of the checkbox if exists.

## OrderPreviewInfoItem

Describes information for the order.

* `title` : String
* `value` : String

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
```

## Brackets

* `stopLoss`: double
* `takeProfit`: double
* `trailingStopPips`: double

## Formatter

An object with `format` method that can be used to format the number to a string.

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

An object that decribes a custom input field with a checkbox.

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
The value of ComboBox will be saved and will be used as a default value the next time you open the order dialog or panel, if `saveToSettings` is set to `true`.

* `inputType`: 'ComboBox'
* `id`: string
* `title`: string
* `items`: CustomComboBoxItem[]
* `saveToSettings?`: boolean;

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
