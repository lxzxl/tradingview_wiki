## Shapes Groups API

Shapes on the chart can be combined into groups. Being grouped, shapes can be managed as a single object via the group id.
When working with groups, the following rules must be considered:

1. Each shape can be but doesn’t necessarily have to be part of a specific group or not be part of any group. Shape can not be part of several groups at the same time.
2. Only shapes of the same pane can be grouped.
3. A group cannot be empty. Empty groups are automatically removed.
4. All shapes in the group have sequential z-indexes. Thus, no other object can be placed between shapes in a group.
5. Groups are bound with symbols.

All operations available through the Shapes Group API go through the undo stack.

## Methods

* [Manipulating groups](#manipulating-groups)
  * [createGroupFromSelection()](#creategroupfromselection)
  * [removeGroup(groupId)](#removegroupgroupid)
  * [groups()](#groups)
  * [shapesInGroup(groupId)](#shapesingroupgroupid)
  * [excludeShapeFromGroup(groupId, shapeId)](#excludeshapefromgroupgroupid-shapeid)
* [Z-Order operations](#z-order-operations)
  * [availableZOrderOperations(groupId)](#availablezorderoperationsgroupid)
  * [bringToFront(groupId)](#bringtofrontgroupId)
  * [sendToBack(groupId)](#sendtobackgroupId)
  * [bringForward(groupId)](#bringforwardgroupid)
  * [sendBackward(groupId)](#sendbackwardgroupid)
  * [insertAfter(groupId, target)](#insertaftergroupid-target)
  * [insertBefore(groupId, target)](#insertbeforegroupid-target)
* [Batch shapes operations](#batch-shapes-operations)
  * [groupVisibility(groupId)](#groupvisibilitygroupId)
  * [setGroupVisibility(groupId, value)](#setgroupvisibilitygroupId-value)
  * [groupLock(groupId)](#grouplockgroupId)
  * [setGroupLock(groupId, value)](#setgrouplockgroupid-value)
* [Groups information methods](#groups-information-methods)
  * [getGroupName(groupId)](#getgroupnamegroupId)
  * [setGroupName(groupId, name)](#setgroupnamegroupid-name)
  * [canBeGroupped(entities)](#canBeGrouppedentities)

## Manipulating groups

### createGroupFromSelection()

Creates a group from selected shapes. Throws an error if one of the following occurs:

* a selection is empty
* a selection contains non-shapes
* a selection contains shapes from more that one pane

This function moves all the shapes to the top one, while keeping their order.
The function returns an ID of a newly created group.

### removeGroup(groupId)

1. `groupId`: string, result of createGroupFromSelection call.

Removes the specified group as well as all the shapes from it.

### groups()

Returns an array with IDs of all existing groups of shapes for the currently selected symbol on the chart.

### shapesInGroup(groupId)

1. `groupId`: string, result of createGroupFromSelection call.

Returns an array of shape identifiers in the specified group.

### excludeShapeFromGroup(groupId, shapeId)

1. `groupId`: string, result of createGroupFromSelection call. A group to exclude the shape from.
2. `shapeId`: EntityID. A shape to be removed from the group.

When the last shape is removed from a group, the group is automatically removed.

## Z-Order operations

### availableZOrderOperations(groupId)

1. `groupId`: string, result of createGroupFromSelection call.

Returns an object with Z-order operations available for the specified group. This structure has the following fields:

* `bringForwardEnabled`: true if one can bring a specified group forward
* `bringToFrontEnabled`: true if one can bring a specified group to front
* `sendBackwardEnabled`: true if one can send a specified group backward
* `sendToBackEnabled`: true if one can send a specified group to back

### bringToFront(groupId)

1. `groupId`: string, result of createGroupFromSelection call.

This function moves all the shapes of the group to the top of the Z-order, while keeping their order.

### sendToBack(groupId)

1. `groupId`: string, result of createGroupFromSelection call.

This function moves all the shapes of the group to the bottom of the Z-order, preserving their order.

### bringForward(groupId)

1. `groupId`: string, result of createGroupFromSelection call.

This function moves all the shapes of the group one step forward in the Z-order.

### sendBackward(groupId)

1. `groupId`: string, result of createGroupFromSelection call.

This function moves all the shapes of the group one step backward in the Z-order.

### insertAfter(groupId, target)

1. `groupId`: string, result of createGroupFromSelection call.
2. `target`: Id of the group or EntityId.

This function moves all the shapes of the group (and the group itself) right below the target.

### insertBefore(groupId, target)

1. `groupId`: string, result of createGroupFromSelection call.
2. `target`: Id of the group or EntityId.

This function moves all the shapes of the group (and the group itself) right above the target.

## Batch shapes operations

### groupVisibility(groupId)

1. `groupId`: string, result of createGroupFromSelection call.

Returns the value for current group visibility. Possible results are:

1. `Visible` - all shapes in the group are visible.
2. `Invisible` - all shapes in the group are invisible.
3. `Partial` - some shapes in the group are visible and some are not.

### setGroupVisibility(groupId, value)

1. `groupId`: string, a result of createGroupFromSelection call.
2. `value`: boolean, true to show and false to hide all the shapes from the group

Shows or hides all the shapes in the group.

### groupLock(groupId)

1. `groupId`: string, result of createGroupFromSelection call.

Returns current group lock value. Possible results are:

1. `Locked` - all shapes in the group are locked.
2. `Unlocked` - all shapes in the group are unlocked.
3. `Partial` - some shapes in the group are locked and some are not.

### setGroupLock(groupId, value)

1. `groupId`: string, result of createGroupFromSelection call.
2. `value`: boolean, true to lock and false to unlock all the shapes from the group

Locks or unlocks all the shapes in the group.

## Groups information methods

### getGroupName(groupId)

1. `groupId`: string, a result of createGroupFromSelection call.

Sets a new name of the group. Uniqueness check is not performed.

### setGroupName(groupId, name)

1. `groupId`: string, result of createGroupFromSelection call.
2. `name`: string, new name for the group

Sets a new name to the group. No uniqueness check is performed.

### canBeGroupped(entities)

1. `entities`: array of EntityId

Checks whether or not the specified set of entities can be grouped.
