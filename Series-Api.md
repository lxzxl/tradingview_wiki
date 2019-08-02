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

### moveToOtherSourceScale(entityId)

1. `entityId`: object. Value that is returned when a study is created via API.

Pins the main series to the same price axis as a study with a corresponding `entityId`.

### isVisible()

Returns `true` if the main series is visible.

### setVisible(value)

1. `value` - `true` or `false`

Shows/hides the main series.

### bringToFront()

Places the main series on top of all other chart objects.

### sendToBack()

Places the main series behind all other chart objects.
