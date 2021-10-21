The `inputs` in Custom Study [Metainfo](Custom-Studies-Metainfo) is an array of study inputs.
Study input contains following fields:

`* - required`

* `id`* - string
* `name`* - string, the title of the input
* `type`* - string, input type. Possible values are:
  * `'bool'`
  * `'text'`
  * `'symbol'`
  * `'resolution'`
  * `'session'`
  * `'source'`
  * `'integer'`
  * `'float'`
  * `'time'`
* `confirm` - boolean, if true, then user will be asked to confirm input value before indicator is added to chart. Default value is false.
* `isHidden` - boolean
* `visible` - string
* `defval` - default value of the input variable. It has the specific type for a given input and can be optional.

Also, study input object can have additional fields depending on the input `type`.

## Bool

* `type`* - `'bool'`
* `defval`* - boolean

## Text

* `type`* - `'text'`
* `defval`* - string
* `options` - an array of strings, a list of options to choose from
* `optionsTitles` - an object `{ [option]: value }`, where `option` and `value` are strings

## Symbol

* `type`* - `'symbol'`
* `defval` - string
* `optional` - boolean

## Resolution

* `type`* - `'resolution'`
* `defval`* - a resolution string, please see the [Resolution](Resolution) page
* `options` - an array of strings, a list of options to choose from
* `optionsTitles` - an object `{ [option]: value }`, where `option` and `value` are strings

## Source

* `type`* - `'source'`
* `defval`* - may be a custom string or one of the following: `open`, `high`, `low`, `close`, `hl2`, `hlc3`, `ohlc4`
* `options` - an array of custom strings or the following: `open`, `high`, `low`, `close`, `hl2`, `hlc3`, `ohlc4`
* `optionsTitles` - an object `{ [option]: value }`, where `option` and `value` are strings

## Integer, Float, Time

* `type`* - `'integer'`, `'float'`, or `'time'`
* `defval`* - number
* `max` - number, maximum possible value of the input variable
* `min` - number, minimal possible value of the input variable
* `step` - number, the step value to use for incrementing/decrementing input from format dialog. Default value is 1.
