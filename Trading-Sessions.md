# Trading Sessions

A trading session defines the hours in a week when a symbol is actively traded on an exchange. The trading session of a symbol is passed to the Charting Library in the [`session` field of the symbol information.](Symbology#session)

Session time is expected to be in the **exchange time zone**.

**Use this parser to check your session string**: <http://tradingview.github.io/checksession.html>

## Session formats

The trading session is defined by a string. The format allows many different kinds of sessions to be described.

### 24/7 sessions

A session that runs 24 hours a day, 7 days a week _including_ Saturday and Sunday.

* `24x7`

### Sessions within a day

A session within a day. For example:

* `0930-1600` starts at 9:30am and ends at 16:00pm from Monday to Friday.

* `0000-0000` starts at 0:00am to 0:00am from Monday to Friday.

### Overnight sessions

A session may go over multiple days. For example:

* `1600-0930` starts at 4:00pm the previous day, and ends at 9:30am on the current day.

* `1700-1700` starts at 5:00pm the previous day, and ends at 5:00pm on the current day.

The 'F' symbol can be used for sessions that start a relative number of days ago. The number of days cannot be more than 6:

* `1600F-0930` starts at 4:00pm on the previous day, ends at 9:30am. For example Wednesday's session starts at 7:00pm and ends at 9:30am on Thursday.

* `1900F-2350F` starts at 7:00pm on the previous day, ends at 11:50pm on the previous day. For example Monday's session starts at 7:00pm on Sunday and ends at 11:50pm on Sunday.

* `1900F3-1900` starts at 19:00 three days ago. For example Friday's session starts at 7:00pm on Tuesday and ends at 7:00pm on Friday.

* `1900F3-2350F3` starts at 19:00 three days ago and end at 23:50 three days ago. For example Friday's session starts at 7:00pm on Tuesday and ends at 7:00pm on Tuesday.

### Multiple sessions

There may be more than one session in one trading day. If that's the case you should pass all of them as sessions separated with comma:

* `0930-1400,1430-1700` The first session starts at 9:30am and ends at 2:00pm, and the second session starts at 2:30pm and ends at 5:00pm.

### Different sessions for different days

By default sessions are assumed to be for Monday to Friday with no sessions on Saturday or Sunday.

Day numbers are `1` for **Sunday** and `7` for **Saturday** (`2` - Monday, `3` - Tuesday, etc.).

You can use the `:` specifier to assign the day the session should be applied to, which allows you to include Saturday and Sunday:

* `0900-1400:2|0900-1630` on Mondays the session starts at 9:00am and ends at 2:00pm. On all other days the session starts at 9:00am and ends at 4:30pm.
* `2200-2200:3456|1700F-2200:2` the Monday session starts at 5:00pm on Sunday and ends at 10:00pm on Monday. On all other days the session starts at 10:00pm the previous day and ends at 10:00pm.
* `0930-1630:34567` starts at 9:30am and ends at 4:30pm on Tuesday, Wednesday, Thursday, Friday, and Saturday.

You can specify more than 1 day for a single session. For example in `0900-1630|0900-1400:23` the `0900-1400` session will be assigned to days `2` and `3` (Monday and Tuesday).

## Examples

Let's look at some examples in detail.

### `0900-1400:2|0900-1630`

Monday has one session starting at 9:00am and ending at 2:00pm.

All other week days have one session starting at 9:00am and ending at 4:30pm.

Fragment | Meaning
---------|--------
0900-1630|A session 0900-1630. This session will be assigned by default to all non-weekend days because it's not followed by the `:` specifier.
&#124;|Sessions separator. This character divides different sessions.
0900-1400|A session 0900-1400. It's the session for a day #2 (see below).
:|Day specifier. This character follows the session hours and is followed by the day numbers.
2|The day number for the session above (Monday).

### `1715F-0300,0915-1200,1300-1630:3456|1715F3-0300F2,0915-1200,1300-1630:2`

Monday has three sessions. The first starts at 5:15pm on Friday and ends at 3:00am on Saturday, the second starts at 9:15am on Monday and ends at 12:00 midday, and the third starts at 1:00pm and ends sat 4:30pm.

Tuesday, Wednesday, Thursday, and Friday also have three sessions. The first starts at 5:15pm on the previous day and ends at 3:00am on the current day, the second starts at 9:15am on current day and ends at 12:00 midday, and the third starts at 1:00pm and ends sat 4:30pm.

Fragment | Meaning
---------|--------
1715F-0300|A session starting at 5:15pm one day ago, and ending at 3:00am.
0915-1200|A session starting at 9:00am, and ending at 12:00 midday.
1300-1630|A session starting at 1:00pm, and ending at 4:30pm.
:|Day specifier. This character follows the session hours and is followed by the day numbers.
3456|The day numbers for the sessions above (Tuesday, Wednesday, Thursday, and Friday).
&#124;|Sessions separator. This character divides different sessions.
1715F3-0300F2|A session starting at 5:15 three days ago, and ending at 3:00am two days ago.
0915-1200|A session starting at 9:15am, and ending at 12:00 midday.
1300-1630|A session starting at 1:00pm, and ending at 4:30pm.
:|Day specifier.
2|The day number for the session above (Monday).

**version: 1.1**:

You can specify the first trading day of the week using semicolon. Examples:

* `1;0900-1630|0900-1400:2` - first day of the week is Sunday
* `0900-1630|0900-1400:2;6` - first day of the week is Saturday
* `0900-1630|0900-1400:2` - first day of the week is Monday (default value)
