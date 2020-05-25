## Panes and scales behavior

Here is the detailed description of how panes and scales work when creating a study.

First of all, all studies are divided into 2 groups: "price" studies and "non-price" studies. Examples of price studies are "moving average" and "bollinger bands". The result of such studies has the same dimension as their input source. Price studies are placed by default on the same pane as their source and pinned to the same price scale. By contrast, the result of non-price studies has a different dimension. For example, Stochastic always returns values from 0 to 100. Non-price studies are placed by default to a separate pane.

* You can change the default pane of the study using `forceOverlay`. If it's set to true, the study is placed on the main pane (pane with the main series). This option doesn't affect the default price scale. This flag is applied to non-price studies only. There is no way to place a price study on a separate pane by default at this time.
* You can change the default price scale using `priceScale`. If it is not set, then the chart behaves as described above. `no-scale` sets "No scale" (full-screen) mode for the study. `new-left` and `new-right` always places the study on a new price scale, even while placing a price study. `as-series` option always places the study on the same price scale that the main series are attached to.

The following table illustrates this

| Value | Price Study or Non-Price Study with force_overlay=true | Non-Price Study with force_overlay=false |
|---|---|---|
|new-left|place on a new left scale of the main pane|place on a new left scale of a new pane
|new-right|place on a new right scale of the main pane|place on a new right scale of a new pane
|no-scale|place as "no scale" on the main pane|place as "no scale" on a new pane
|as-series|place on the same price scale as the main series|place on a separate pane on the right price scale
