## Timezone API

### availableTimezones()

Returns an array of supported [TimezoneInfo](Timezone-Api#TimezoneInfo).

### getTimezone()

Returns the current [TimezoneInfo](Timezone-Api#TimezoneInfo).

### setTimezone(timezoneId, options)

1. `timezoneId` - string, timezone identificator.
2. `options` is an *optional* object with one field:
    * `disableUndo` - boolean, flag that shows the undo action availability.

Sets the current timezone.

### onTimezoneChanged

You can subscribe using the [Subscription](Subscription) object returned by this function to be notified when the timezone is changed. You can also use the same object to unsubscribe from the event.

Example:

```javascript
timezoneApi.onTimezoneChanged().subscribe(
    null,
    timezone => console.log(`New timezone: ${timezone}`),
    true
);
```

## TimezoneInfo

TimezoneInfo is an object with the following fields:

* `id` - string, timezone identificator.
* `title` - string, timezone title.
* `offset` - number, optional field that contains information about timezone offset.

Supported timezone identificators are [timezones](Symbology#timezone) and `exchange`. `exchange` is a special "timezone" that means the timezone of a currently active symbol. Thus the actual timezone will be calculated every time a symbol changes.
