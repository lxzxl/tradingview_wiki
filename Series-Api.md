## Series API

### isUserEditEnabled()

Returns `true` if a user is able to remove/change/hide the main series.

### setUserEditEnabled(enabled)

1. `enabled` - `true` or `false`

Enables or disables removing/changing/hiding the main series by the user.

### mergeUp()

Merges the main series up (if possible).

### mergeDown()

Merges the main series down (if possible).

### unmergeUp()

Unmerges the main series up (if possible).

### unmergeDown()

Unmerges the main series down (if possible).

### detachToRight()

Pins the main series to a new price axis at right.

### detachToLeft()

Pins the main series to a new price axis at left.

### detachNoScale()

Makes the main series to be an overlay source.

### changePriceScale(priceScale)

1. `priceScale` should be a string with one of the following values:
    * `"new-left"` - attach the main series to the new left price scale
    * `"new-right"` - attach the main series to the new right price scale
    * `"no-scale"` - hide the main series price scale if there are another scales on the main pane
    * `entityId` - pin the main series to the same price axis as a study with a corresponding `entityId`

Changes the price scale of the main series.

### isVisible()

Returns `true` if the main series is visible.

### setVisible(value)

1. `value` - `true` or `false`

Shows/hides the main series.

### bringToFront()

Places main series on top of all other chart objects.

### sendToBack()

Places main series behind all other chart objects.

### chartStyleProperties(chartStyle)

1. `chartStyle` - number

Returns properties for a specific [chart style](Chart-Methods#setChartTypetype). See [this article](Chart-Style-Properties) for a returned object.

### setChartStyleProperties(chartStyle, newPrefs)

Sets properties for a specific chart style.

1. `chartStyle` - number
1. `newPrefs` - object

`newPrefs` should be a subset of properties for a [chart style](Chart-Methods#setChartTypetype).
See [this article](Chart-Style-Properties) for available values of properties for a specific chart style.
