The Custom Study Constructor is a Function Constructor in terms of ES5. The library creates an instance of a custom study by applying operator `new` to the constructor. The constructor function is a mandatory field of [custom study object](Creating-Custom-Studies). The library expects the constructor to create an instance of the study with one mandatory method - `main()` and one optional method - `init()`.
Once the study is created the library calls `init` (if exists) and `main` sequentially with empty context to collect information about all `vars` (see below).

All functions in Constructor accept [PineJS utility functions](PineJS-Utility-Functions).

Arguments for both functions are `context` and `inputCallback`.

The `context` is an object, containing symbol info along with some useful methods to load/store symbol:

`* - required`

* `new_sym(ticker*, period*, currencyCode, unitId)` - is used to load new ticker
* `select_sym(i*)` - switch context to the other symbol received trough `new_sym`, where `i` is an index of the symbol (`0` for the main series)
* `new_var(value*)` - creates an in-memory temporary storage with depth defined by first call `new_var(value).get(n)`
* `new_unlimited_var(value*)` - creates an in-memory temporary storage with unlimited depth

The `inputCallback` is an array of input values, placed in order of `inputs` in [Metainfo](Custom-Studies-Metainfo).

## init(context, inputCallback)

The `init` method is called only once during the lifetime of the study and designed to get additional info for the study.

```javascript
this.init = function(context, inputCallback) {
    var symbol = '#EQUITY';
    var period = PineJS.Std.period(this._context);
    context.new_sym(symbol, period);
};
```

## main(context, inputCallback)

The `main` is called every time the library wants to calculate the study. Also it's called for every bar of every symbol. Thus, if you request several additional symbols inside your indicator it will increase the count of runs.

`main` should return one of the following types:

* a single value; this is a shorthand of an array form with the only single item; example - 10 (the same as [10])
* an array of:
  * numbers - N-th number in this array is treated as value of [n-th plot](Custom-Studies-Metainfo). Example: [10, 20].
  * objects with the structure `{ offset: number, value: number, }`. The same as the numbers, but allows you to override the offset of every plot (note that offset of a certain plot should always be the same). Example: `[{ value: 10, offset: 5, }, { value: 20, offset: 10, }]`.

```javascript
this.main = function(ctx, inputCallback) {
    this._context = ctx;
    this._input = inputCallback;
    var inputValue1 = this._input(0);
    var inputValue2 = this._input(1);
    var zigzag1 = PineJS.Std.zigzag(inputValue1 / 100, inputValue2 / 2, this._context);
    var zigzag2 = PineJS.Std.zigzagbars(inputValue1 / 100, inputValue2 / 2, this._context);
    return [zigzag1, zigzag2];
};
```
