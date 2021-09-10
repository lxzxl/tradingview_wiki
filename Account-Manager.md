:chart: All content on this page is relevant to [Trading Terminal](Trading-Terminal) only.

Account Manager is an interactive table that displays trading information.
It includes 3 pages: orders/positions and account information.

To create an account manager you will need to describe columns of each page and provide data.

Remark 1. [Broker API](Broker-API) should implement [accountManagerInfo](Broker-API#accountmanagerinfo)

<!--
Be sure that you have the following structure:
## Fields group name
### Field name
### Field name
#### Field subitem description
-->

# Account Manager Meta Information

The following information should be returned by [accountManagerInfo](Broker-API#accountManagerInfo).

## Account Manager header

Account Manager's header includes the name of the broker.

### accountTitle: String

## Orders Page

### orderColumns: array of [Column](#column-description)

Columns description that you want to be displayed on the Orders page.
You can display any field of an [order](Trading-Objects-and-Constants#order) or add your own fields to an order object and display them.

### orderColumnsSorting: [SortingParameters](#sortingparameters)

Optional sorting of the table.

### possibleOrderStatuses: array of [OrderStatus](Trading-Objects-and-Constants#orderstatus)

Optional list of statuses to be used in the orders filter. Default list is used if it hasn't been set.

### historyColumns: array of [Column](#column-description)

History page will be displayed if it exists. All orders from previous sessions will be shown in the History.

### historyColumnsSorting: [SortingParameters](#sortingparameters)

Optional sorting of the table.

## Positions Page

### positionColumns: array of [Column](#column-description)

You can display any field of a [position](Trading-Objects-and-Constants#position) or add your own fields to a position object and display them.

## Additional Pages (e.g. Account Summary)

### pages: array of [Page](#page)

You can add new tabs in the Account Manager by using `pages`. Each tab is a set of tables.

#### Page

`Page` is a description of an additional Account Manager tab. It is an object with the following fields:

1. `id`: String

    Unique identifier of a page

1. `title`: String

    Page title. It is the tab name.

1. `tables`: Array of [Table](#table).

    It is possible to display one or more tables in this tab.

#### Table

You can add one or more tables to a [Page](#page).
Account Summary table metainfo is an object with the following fields:

1. `id`: String

    Unique identifier of a table.

1. `title`: String

    Optional title of a table.

1. `columns`: array of [Column](#column-description)

1. `getData`: Promise

    This function is used to request table data. It should return Promise (or Deferred) and resolve it with an array of data rows.

    Each row is an object. Keys of this object are column names with the corresponding values.

    There is a predefined field `isTotalRow` which can be used to mark a row that should be at the bottom of the table.

1. `changeDelegate` : [Delegate](Delegate)

    This delegate is used to watch the data changes and update the table. Pass new account manager data row by row to the `fire` method of the delegate.

1. `initialSorting`: [SortingParameters](#sortingparameters)

    Optional sorting of the table.

**NOTE**: make sure that you have a unique string `id` field in each row to identify it.

#### SortingParameters

Object with the following properties:

    - `columnId` - `property` of the column that will be used for sorting.
    - `asc` - (optional, default `true`) - If it is `false`, then initial sorting will be in descending order.

## Column description

The most valuable part of Account Manager description is a description of its columns.

### label

Column title. It will be displayed in the table's header row.

### alignment

Horizontal alignment of the cell value. The default value is `left`.

| alignment    |   description  |
|--------------|----------------|
| left         | It aligns the cell value to the left |
| right        | It aligns the cell value to the right |

### formatter

Name of the formatter to be used for data formatting. If `formatter` is not set the value is displayed as is.
Formatter can be a default or a custom one.

Here is the list of default formatters:

| name | description |
| ---- | ----------- |
| `date` | Displays the date or time. |
| `dateOrDateTime` | Displays the date or date and time. This formatter accepts an object `{value: number, hasTime: boolean}`. If `hasTime` is set to `true` then the date and time are displayed. Otherwise only the date is displayed.|
| `fixed` | Displays a number with 2 decimal places. |
| `formatPrice` | Displays symbol's price. |
| `formatQuantity` | Displays an integer or floating point quantity, separates thousands groups with a space. |
| `formatPriceForexSup` | The same as `formatPrice`, but it makes the last character of the price superscripted. It works only if instrument type is set to `forex`.|
| `localDate` | Displays the local date or time. |
| `localDateOrDateTime` | The same as `dateOrDateTime`, but it displays time in the local timezone. |
| `pips` | Displays a number with 1 decimal place. |
| `profit` | Displays profit in account currency. It also adds the `+` sign, separates thousands and changes the cell text color to red or green. |
| `profitInInstrumentCurrency` | Displays profit in instrument currency. It also adds the `+` sign, separates thousands and changes the cell text color to red or green. |
| `side` | It is used to display the side: Sell or Buy. |
| `positionSide` | It is used to display the position side: Short or Long. |
| `status` | It is used to format the `status`. |
| `symbol` | It is used for a symbol field. It displays `brokerSymbol`, but when you click on a symbol the chart changes according to the `symbol` field. `property` key is ignored.|
| `text` | Displays a text value. |
| `textNoWrap` | Displays a text value without word wrapping. |
| `type` | It is used to display the type of order: Limit/Stop/StopLimit/Market. |
| `variablePrecision` | Displays a number with variable precision. |

There are some special formatters that are used to add buttons to the table:

`orderSettings` adds Modify/Cancel buttons to the orders tab.

`posSettings` adds Edit/Close buttons to the Positions/Net Positions tab.

`tradeSettings` adds Edit/Close buttons to the Individual Positions tab.

### property

`property` is a data object key that is used to get the data to display in a table.

### sortProp

Optional `sortProp` is a data object key that is used for data sorting.

### notSortable

Optional `notSortable` can be set to prevent column sorting.

### help

`help` is a tooltip string for the column.

### highlightDiff

`highlightDiff` can be set with `formatPrice` and `formatPriceForexSup` formatters only to highlight the changes of the field.

### tooltipProperty

`tooltipProperty` is a key of the row object that is used to get the tooltip to display when hovering over a cell. The tooltip property refers to an object whose keys are property names and values are the corresponding tooltips.

### supportedStatusFilters

An optional numeric array of order statuses that is applied to order columns only. If it is available then the column will be displayed in the specified tabs of the status filter only.

Here is the list of possible order statuses:

1. 0 - All
1. 1 - Canceled
1. 2 - Filled
1. 3 - Inactive
1. 5 - Rejected,
1. 6 - Working

### isCapitalize

If it is `true`, the first character of every word in the sentence in the column will be capitalized. The default value is `true`.

### showZeroValues

If it is `false`, the zero values will be hidden. The default value is `true`.

## Context Menu

### contextMenuActions(contextMenuEvent, activePageActions)

`contextMenuEvent`: MouseEvent or TouchEvent object passed by a browser

`activePageActions`: array of `ActionMetaInfo` items for the current page

Optional function to create a custom context menu.
It should return `Promise` that is resolved with an array of `ActionMetaInfo`.
