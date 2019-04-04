## Selection API

### clear()

Clears the selection.

### add(id)

1. `id` is an `entityId`

Adds object specified by `id` to the selection. `id` is an ID of a drawing or a study. If the object does not exist, then an error is thrown.

### add(ids)

1. `ids` is an array of `entityId`

Adds objects specified by `ids` to the selection. `ids` is an array of drawings or studies IDs. If any of the objects does not exist, an error is thrown.

### set(id)

1. `id` is an `entityId`

Clears current selection and selects an object specified by. `set(id)` is the same as `clear();add(id)`. If the object is does not exist, an error is thrown.

### set(ids)

1. `ids` is an array of `entityId`

Clears current selection and selects objects specified by `ids`. `ids` is an array of drawings or studies IDs. `set(ids)`  is the same as `clear();add(ids)`. If any of the objects does not exist, an error is thrown.

### remove(id)

1. `id` is an `entityId`

Removes specified object from selection. `id` is an identifier of a drawing or a study. If the object is not selected, then this method does nothing. If the object does not exist, then an error is thrown.

### remove(ids)

1. `ids` is an array of `entityId`

Removes specified objects from the selection. `ids` is an array of drawings identifiers. If any of the specified objects is not selected, then it is skipped by this method. If any of the objects does not exist, then an error is thrown.

### contains(id)

1. `id` is an `entityId`

Checks if specified object is selected. `id` is an identifier of a drawing or a study. Returns `false` if the object is not selected. If the object does not exist, then an error is thrown.

### allSources()

Returns an array of identifiers of the selected objects.

### isEmpty()

Checks if the selection is empty. It returns `true` if there is no selected objects on the chart.

### onChanged()

Returns a [Subscription](Subscription) object that can be used to subscribe to the selection changes.

**Multiple selection:**

Multiple selection works for shapes only using the following rules:

* If you add a study to the selection, then it clears the selection and selects the study.
* If you add a shape to the selection when the currently selected object is a study, then it clears the selection and selects the shape.
* If you add an array of objects to the selection, it works as if you add these objects one by one.

**Example:**

```javascript
var chart = tvWidget.activeChart();
chart.selection().onChanged().subscribe(null, s => console.log(chart.selection().allSources()));      // it will print all selection changes to the console
var studyId = chart.createStudy("Moving Average", false, false, [10]);  // create a study and save its id
chart.selection().add(studyId);                                         // add the study to the selection ([<id>] is printed to the console)
chart.selection().clear();                                              // clear the selection ([] is printed to the console)
```
