Custom Study [Constructor](Custom-Studies-Constructor) is able to use utility functions from PineJS object (an argument of [custom_indicators_getter](Widget-Constructor#custom_indicators_getter) function).

# Functions ported from Pine

## `na(x)`

Test value if it's a NaN.

### **Returns**

`true` if `x` is not a valid number (`x` is NaN), otherwise `false`.

## `nz(x, y)`

Replaces NaN values with zeros (or given value) in a series.

### **Returns**

`x` if it's a valid (not NaN) number, otherwise y

## `and(expr1, expr2)`

Logical AND. Applicable to boolean expressions.

### **Returns**

Boolean value, or series of boolean values.

## `or(expr1, expr2)`

Logical OR. Applicable to boolean expressions.

### **Returns**

Boolean value, or series of boolean values.

## `not(expr)`

Logical negation (NOT). Applicable to boolean expressions.

### **Returns**

Boolean value, or series of boolean values.

## `max(x1, x2, ..., x10)`

### **Returns**

The greatest of multiple values

## `min(x1, x2, ..., x10)`

### **Returns**

The smallest of multiple given values.

## `pow(base, exponent)`

Mathematical power function.

### **Returns**

`x` raised to the power of `y`. If `x` is a series, it is calculated elementwise.

### **Arguments**

- **`base` (series[float])** Specify the base to use.
- **`exponent` (float)** Specifies the exponent.

## `abs(x)`

Absolute value of `x` is `x` if `x >= 0`, or `-x` otherwise.

### **Returns**

The absolute value of x

## `log(x)`

Natural logarithm of any `x > 0` is the unique `y` such that `e^y = x`

### **Returns**

The natural logarithm of x.

## `log10(x)`

Base 10 logarithm of any `x > 0` is the unique `y` such that `10^y = x`

### **Returns**

The base 10 logarithm of x.

## `sqrt(x)`

Square root of any `x >= 0` is the unique `y >= 0` such that `y^2 = x`

### **Returns**

The square root of x.

## `sign(x)`

Sign (signum) of `x` is zero if the `x` is zero, `1.0` if the `x` is greater than zero, `-1.0` if the `x` is less than zero.

### **Returns**

The sign of the argument.

## `exp(x)`

The exp function of `x` is `e^x`, where `x` is the argument and `e` is Euler's number.

### **Returns**

A number representing e^x.

## `sin(x)`

The `sin` function returns the trigonometric sine of an angle.

### **Returns**

The trigonometric sine of an angle.

### **Arguments**

- **`x` (series[float])** Angle, in radians.

## `cos(x)`

The cos function returns the trigonometric cosine of an angle.

### **Returns**

The trigonometric cosine of an angle.

### **Arguments**

- **`x` (series[float])** Angle, in radians.

## `tan(x)`

The tan function returns the trigonometric tangent of an angle.

### **Returns**

The trigonometric tangent of an angle.

### **Arguments**

- **`x` (series[float])** Angle, in radians.

## `asin(x)`

The asin function returns the arcsine (in radians) of number such that `sin(asin(y)) = y` for `y` in range `[-1, 1]`.

### **Returns**

The arcsine of a value; the returned angle is in the range `[-Pi/2, Pi/2]`, or na if y is outside of range `[-1, 1]`.

## `acos(x)`

The acos function returns the arccosine (in radians) of number such that `cos(acos(y)) = y` for `y` in range `[-1, 1]`.

### **Returns**

The arc cosine of a value; the returned angle is in the range `[0, Pi]`, or `na` if `y` is outside of range `[-1, 1]`.

## `atan(x)`

The atan function returns the arctangent (in radians) of number such that `tan(atan(y)) = y` for any `y`.

### **Returns**

The arc tangent of a value; the returned angle is in the range `[-Pi/2, Pi/2]`.

## `floor(x)`

### **Returns**

The largest integer less than or equal to the given number.

## `ceil(x)`

The ceil function returns the smallest (closest to negative infinity) integer that is greater than or equal to the argument.

### **Returns**

The smallest integer greater than or equal to the given number.

## `round(x)`

### **Returns**

The value of `x` rounded to the nearest integer, with ties rounding up. If the precision parameter is used, returns a float value rounded to that number of decimal places.

## `avg(x1, x2, ..., x10)`

Calculates average of all given series (elementwise).

### **Returns**

Average.

## `open(context)`

Current open price.

### **Arguments**

- **`context`** PineJS execution context.

## `high(context)`

Current high price.

### **Arguments**

- **`context`** PineJS execution context.

## `low(context)`

Current low price.

### **Arguments**

- **`context`** PineJS execution context.

## `close(context)`

Close price of the current bar when it has closed, or last traded price of a yet incomplete, realtime bar.

### **Arguments**

- **`context`** PineJS execution context.

## `hl2(context)`

Is a shortcut for `(high + low)/2`

### **Arguments**

- **`context`** PineJS execution context.

## `hlc3(context)`

Is a shortcut for (high + low + close)/3

### **Arguments**

- **`context`** PineJS execution context.

## `ohlc4(context)`

Is a shortcut for (open + high + low + close)/4

### **Arguments**

- **`context`** PineJS execution context.

## `volume(context)`

Current bar volume.

### **Arguments**

- **`context`** PineJS execution context.

## `period(context)`

Resolution string, e.g. `60` - 60 minutes, `D` - daily, `W` - weekly, `M` - monthly, `5D` - 5 days, `12M` - one year, `3M` - one quarter

### **Arguments**

- **`context`** PineJS execution context.

## `tickerid(context)`

### **Arguments**

- **`context`** PineJS execution context.

## `year(context)`

Current bar year in exchange timezone.

### **Arguments**

- **`context`** PineJS execution context.

## `month(context)`

Current bar month in exchange timezone.

### **Arguments**

- **`context`** PineJS execution context.

## `weekofyear(context)`

Week number of current bar time in exchange timezone.

### **Arguments**

- **`context`** PineJS execution context.

## `dayofmonth(context)`

Date of current bar time in exchange timezone.

### **Arguments**

- **`context`** PineJS execution context.

## `dayofweek(context)`

Day of week for current bar time in exchange timezone.

### **Arguments**

- **`context`** PineJS execution context.

## `hour(context)`

Current bar hour in exchange timezone.

### **Arguments**

- **`context`** PineJS execution context.

## `minute(context)`

Current bar minute in exchange timezone.

### **Arguments**

- **`context`** PineJS execution context.

## `second(context)`

Current bar second in exchange timezone.

### **Arguments**

- **`context`** PineJS execution context.

## `iff(condition, then, _else)`

If ... then ... else ...

### **Remarks**

`iff` does exactly the same thing as ternary conditional operator `?:` but in a functional style. Also iff is slightly less efficient than operator `?:`

## `rising(series, length)`

Test if the `series` is now rising for `length` bars long.

### **Returns**

`true` if current `x` is greater than any previous `x` for `length` bars back, `false` otherwise.

### **Arguments**

- **`series` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).

## `falling(series, length)`

Test if the `series` is now falling for `length` bars long.

### **Returns**

`true` if current `x` is less than any previous `x` for `length` bars back, `false` otherwise.

### **Arguments**

- **`series` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).

## `rsi(upper, lower)`

Relative strength index. It is calculated based on rma's of upward and downward change of x.

### **Returns**

Relative strength index.

### **Arguments**

- **`upper` (float)** Series of values to process.
- **`lower` (float)** Number of bars (length).

## `sum(source, length, context)`

The sum function returns the sliding sum of last y values of x.

### **Returns**

Sum of x for y bars back.

### **Arguments**

- **`source` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).
- **`context`** PineJS execution context.

## `sma(source, length, context)`

The sma function returns the moving average, that is the sum of last `length` values of `source`, divided by `length`.

### **Returns**

Simple moving average of x for y bars back.

### **Arguments**

- **`source` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).
- **`context`** PineJS execution context.

## `rma(source, length, context)`

Moving average used in RSI. It is the exponentially weighted moving average with alpha = 1 / length.

### **Returns**

Exponential moving average of x with alpha = 1 / y.

### **Arguments**

- **`source` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).
- **`context`** PineJS execution context.

## `fixnan(current, context)`

For a given series replaces NaN values with previous nearest non-NaN value.

### **Returns**

Series without `na` gaps.

### **Arguments**

- **`current` (series[float])** Series of values to process.
- **`context`** PineJS execution context.

## `tr(handle_nan, context)`

### **Returns**

True range. It is `max(high - low, abs(high - close[1]), abs(low - close[1]))`

### **Arguments**

- **`handle_nan` (bool)** How NaN values are handled. if `true`, and previous day's close is NaN then `tr` would be calculated as current day high-low. Otherwise (if `false`) `tr` would return NaN in such cases. Also note, that atr uses `tr(true)`.
- **`context`** PineJS execution context.

## `atr(length, context)`

Function atr (average true range) returns the RMA of true range. True range is `max(high - low, abs(high - close[1]), abs(low - close[1]))`

### **Returns**

Average true range.

### **Arguments**

- **`length` (integer)** Length (number of bars back).
- **`context`** PineJS execution context.

## `ema(series, length, context)`

The ema function returns the exponentially weighted moving average. In ema weighting factors decrease exponentially. It calculates by using a formula: `EMA = alpha * x + (1 - alpha) * EMA[1]`, where `alpha = 2 / (y + 1)`

### **Returns**

Exponential moving average of x with alpha = 2 / (y + 1)

### **Arguments**

- **`source` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).
- **`context`** PineJS execution context.

## `wma(source, length, context)`

The wma function returns weighted moving average of `source` for `length` bars back. In wma weighting factors decrease in arithmetical progression.

### **Returns**

Weighted moving average of `series` for `length` bars back.

### **Arguments**

- **`source` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).
- **`context`** PineJS execution context.

## `vwma(source, length, context)`

The `vwma` function returns volume-weighted moving average of `source` for `length` bars back. It is the same as: `sma(x * volume, y) / sma(volume, y)`

### **Returns**

Volume-weighted moving average of `source` for `length` bars back.

### **Arguments**

- **`source` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).
- **`context`** PineJS execution context.

## `swma(source, context)`

Symmetrically weighted moving average with fixed length: 4. Weights: `[1/6, 2/6, 2/6, 1/6]`.

### **Returns**

Symmetrically weighted moving average

### **Arguments**

- **`source` (series[float])** Source series.
- **`context`** PineJS execution context.

## `lowestbars(source, length, context)`

Lowest value offset for a given number of bars back.

### **Returns**

Offset to the lowest bar.

### **Arguments**

- **`source` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).
- **`context`** PineJS execution context.

## `lowest(source, length, context)`

Lowest value for a given number of bars back.

### **Returns**

Lowest value.

### **Arguments**

- **`source` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).
- **`context`** PineJS execution context.

## `highestbars(source, length, context)`

Highest value offset for a given number of bars back.

### **Returns**

Offset to the highest bar.

### **Arguments**

- **`source` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).
- **`context`** PineJS execution context.

## `highest(source, length, context)`

Highest value for a given number of bars back.

### **Returns**

Highest value.

### **Arguments**

- **`source` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).
- **`context`** PineJS execution context.

## `cum(x, context)`

Cumulative (total) sum of `x`. In other words it's a sum of all elements of `x`.

### **Returns**

Total sum series.

### **Arguments**

- **`x` (series[float])** Series of values to process.
- **`context`** PineJS execution context.

## `accdist(context)`

Accumulation/distribution index.

### **Arguments**

- **`context`** PineJS execution context.

## `correlation(source_a, source_b, length, context)`

Correlation coefficient. Describes the degree to which two series tend to deviate from their `sma` values.

### **Returns**

Correlation coefficient.

### **Arguments**

- **`source_a` (series[float])** Source series.
- **`source_b` (series[float])** Target series.
- **`length` (integer)** Length (number of bars back).
- **`context`** PineJS execution context.

## `stoch(source, high, low, length, context)`

Stochastic. It is calculated by a formula: `100 * (close - lowest(low, length)) / (highest(high, length) - lowest(low, length))`

### **Returns**

Stochastic.

### **Arguments**

- **`source` (series[float])** Source series.
- **`high` (series[float])** Series of high.
- **`low` (series[float])** Series of low.
- **`length` (integer)** Length (number of bars back).
- **`context`** PineJS execution context.

## `tsi(source, short_length, long_length, context)`

True strength index. It uses moving averages of the underlying momentum of a financial instrument.

### **Returns**

True strength index. A value in range [-1, 1]

### **Arguments**

- **`source` (series[float])** Source series.
- **`short_length` (integer)** Short length.
- **`long_length` (integer)** Long length.
- **`context`** PineJS execution context.

## `cross(x, y, context)`

### **Returns**

`true` if two series have crossed each other, otherwise `false`.

### **Arguments**

- **`x` (series[float])** First series.
- **`y` (series[float])** Second series.
- **`context`** PineJS execution context.

## `linreg(source, length, offset)`

Linear regression curve. A line that best fits the prices specified over a user-defined time period. It is calculated using the least squares method. The result of this function is calculated using the formula: `linreg = intercept + slope * (length - 1 - offset)`, where intercept and slope are the values calculated with the least squares method on source series (x argument).

### **Returns**

Linear regression curve.

### **Arguments**

- **`source` (series[float])** Source series.
- **`length` (integer)**
- **`offset` (integer)** Offset.

## `sar(start, inc, max, context)`

Parabolic SAR (parabolic stop and reverse) is a method devised by J. Welles Wilder, Jr., to find potential reversals in the market price direction of traded goods.

### **Returns**

Parabolic SAR.

### **Arguments**

- **`start` (series[float])** Start.
- **`inc` (integer)** Increment.
- **`max` (integer)** Maximum.
- **`context`** PineJS execution context.

## `alma(series, length, offset, sigma)`

Arnaud Legoux Moving Average. It uses Gaussian distribution as weights for moving average.

### **Returns**

Arnaud Legoux Moving Average.

### **Arguments**

- **`series` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).
- **`offset` (float)** Controls tradeoff between smoothness (closer to 1) and responsiveness (closer to 0).
- **`sigma` (float)** Changes the smoothness of ALMA. The larger sigma the smoother ALMA.

## `change(source)`

Difference between current value and previous, `x - x[1]`.

### **Returns**

The result of subtraction.

### **Arguments**

- **`source` (series[float])**

## `roc(source, length)`

Function roc (rate of change) showing the difference between current value of `source` and the value of `source` that was `length` days ago.
It is calculated by the formula: `100 * change(src, length) / src[length]`.

### **Returns**

The rate of change of `source` for `length` bars back.

### **Arguments**

- **`source` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).

## `dev(source, length, context)`

Measure of difference between the series and it's `sma`.

### **Returns**

Deviation of `source` for `length` bars back.

### **Arguments**

- **`source` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).
- **`context`** PineJS execution context.

## `stdev(source, length, context)`

### **Returns**

Standard deviation.

### **Arguments**

- **`source` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).
- **`context`** PineJS execution context.

### **Remarks**

This is a biased estimation of standard deviation.

## `variance(source, length, context)`

Variance is the expectation of the squared deviation of a series from its mean `sma`, and it informally measures how far a set of numbers are spread out from their mean.

### **Returns**

Variance of `source` for `length` bars back.

### **Arguments**

- **`source` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).
- **`context`** PineJS execution context.

### **Remarks**

This is a biased estimation of sample variance.

## `percentrank(source, length)`

Percent rank is the percents of how many previous values was less than or equal to the current value of given series.

### **Returns**

Percent rank of `source` for `length` bars back.

### **Arguments**

- **`source` (series[float])** Series of values to process.
- **`length` (integer)** Number of bars (length).

# Functions specific to Charting Library

- `isZero(number)` - boolean, shows whether the `number` equals zero or almost zero
- `toBool(number)` - boolean, `true` if a number is finite and not equals zero
- `eq(arg1, arg2)` - boolean, `true` if argument numbers are equal
- `neq(arg1, arg2)` - boolean, `true` if argument numbers are not equal
- `ge(arg1, arg2)` - boolean, `true` if first argument number is greater or equal to second
- `gt(arg1, arg2)` - boolean, `true` if first argument number is greater than second
- `le(arg1, arg2)` - boolean, `true` if first argument number is lesser or equal to second
- `lt(arg1, arg2)` - boolean, `true` if first argument is lesser than second
- `updatetime(context)` - string, symbol update time
- `ticker(context)` - string, symbol name without exchange prefix, e.g. 'MSFT'
- `interval(context)` - returns symbol interval string
- `isdwm(context)` - boolean, returns `true` if current resolution is a daily or weekly or monthly resolution
- `isintraday(context)` - boolean, returns true if current resolution is an intraday (minutes or seconds) resolution
- `isdaily(context)` - boolean, returns `true` if current resolution is a daily resolution
- `isweekly(context)` - boolean, returns `true` if current resolution is a weekly resolution
- `ismonthly(context)` - boolean, returns `true` if current resolution is a monthly resolution
- `add_days_considering_dst(timezone, utcTime, daysCount)`
- `selectSessionBreaks(context, times)` - select session breaks for intraday resolutions only
- `timepart(symbol, field, time)`
- `wvap(source, context)`
- `createNewSessionCheck(context)`
- `error(message)` - returns study error with `message` specified
- `time(context, period, spec)` - returns UNIX time of current bar
