## Pane API

### hasMainSeries()

Returns `true` if the pane contains the main series.

### getLeftPriceScales()

Returns an array of the [PriceScaleApi](Price-Scale-Api) instances that allows interaction with left price scales. The array may be empty if there is not any price scale on the left side of the pane.

### getRightPriceScales()

Returns an array of the [PriceScaleApi](Price-Scale-Api) instances that allows interaction with right price scales. The array may be empty if there is not any price scale on the right side of the pane.

### getMainSourcePriceScale()

Returns:

* an instance of the [PriceScaleApi](Price-Scale-Api) that allows you to interact with the price scale of the main source
* `null` if the main source is not attached to any price scale (it is in 'No Scale' mode)

### getHeight()

*Starting from version 1.15.*

Returns the pane's height.

### setHeight()

*Starting from version 1.15.*

Sets the pane's height.

### paneIndex()

*Starting from version 1.15.*

Returns the pane's index, it's a number between 0 and all panes count - 1.

### moveTo(paneIndex)

*Starting from version 1.15.*

Moves the pane to a new position, `paneIndex` should be a number between 0 and all panes count - 1.
