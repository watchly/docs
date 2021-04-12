<div class="axi-header">
  <h1>Visualizations</h1>
</div>

Visualizations are powerful aggregations that are run across your data to produce insights that are easy to understand and monitor.

With Visualizations, teams can  create and obtain data stats, group fields and observe methods in running resources. 

This page will introduce you to the visualizations supported by Axiom and some tips on how best to use them.



## **`count`**

The `count` visualization will count all matching events and produces a timeseries chart.


#### Arguments

`none`

#### Group-By Behaviour

Visualization will produce a separate result for each group plotted on a timeseries chart.

<img class="axi-window" src="/assets/shots/count.png" alt="counts overview" />

!!! example "Examples"
    [`count` query on play.axiom.co](https://play.axiom.co/analytics/api-http?qid=R0uYyZOwc0fHmWAhHO)  
    [`count` + `group-by` query on play.axiom.co](https://play.axiom.co/analytics/api-http?qid=OQlr73NZitahuJnswv)


## **`distinct`**

The `distinct` visualization counts each distinct occurrance of the distinct field inside the dataset and produce a timeseries chart.

#### Arguments

* `field: any` - a field to aggregate

#### Group-By Behaviour

Visualization will produce a seperate result for each group plotted on a timeseries chart.

<img class="axi-window" src="/assets/shots/distinct.png" alt="distinct overview" />


!!! example "Examples"
    [`distinct` query on play.axiom.co](https://play.axiom.co/analytics/github-fork-event?qid=oW64JedBiDCAHDsNeY)  
    [`distinct` + `group-by` query on play.axiom.co](https://play.axiom.co/analytics/github-fork-event?qid=RKvriWzdkUgOmLLyDK)


## **`avg`**

The `avg` visualization averages the values of the field inside the dataset and produces a timeseries chart

#### Arguments

* `field: number` - a number field

#### Group-By Behaviour

Visualization will produce a seperate result for each group plotted on a timeseries chart.

<img class="axi-window" src="/assets/shots/average.png" alt="average overview" />


!!! example "Examples"
    [`avg` query on play.axiom.co](https://play.axiom.co/analytics/api-http?qid=T0VpSvCQoarAfuFMrM)  
    [`avg` + `group-by` query on play.axiom.co](https://play.axiom.co/analytics/api-http?qid=56BbnAYoepyL79QfZy)

## **`max`**

The `max` visualization finds the maximum value of the field inside the dataset and produces a timeseries chart.

#### Arguments

* `field: number` - a number field

#### Group-By Behaviour

Visualization will produce a seperate result for each group plotted on a timeseries chart.

<img class="axi-window" src="/assets/shots/max.png" alt="max overview" />

!!! example "Examples"
    [`max` query on play.axiom.co](https://play.axiom.co/analytics/api-http?qid=olagwqIYy7sGCRXjao)  
    [`max` + `group-by` query on play.axiom.co](https://play.axiom.co/analytics/api-http?qid=lWSfAOtUSZ7POne8g9)

## **`min`**

The `min` visualization finds the minimum value of the field inside the dataset and produces a timeseries chart.

#### Arguments

* `field: number` - a number field

#### Group-By Behaviour

Visualization will produce a seperate result for each group plotted on a timeseries chart.

!!! example "Examples"
    [`min` query on play.axiom.co](https://play.axiom.co/analytics/api-http?qid=Bbzlmy9SYY1CHQsxmh)  
    [`min` + `group-by` query on play.axiom.co](https://play.axiom.co/analytics/api-http?qid=mGGnJwIfeVz0TnGhwB)

## **`sum`**

The `sum` visualization adds all the values of the field inside the dataset and produces a timeseries chart.

#### Arguments

* `field: number` - a number field

#### Group-By Behaviour

Visualization will produce a seperate result for each group plotted on a timeseries chart.

!!! example "Examples"
    [`sum` query on play.axiom.co](https://play.axiom.co/analytics/api-http?qid=LYDKqNwZToZXqtx8Vu)  
    [`sum` + `group-by` query on play.axiom.co](hhttps://play.axiom.co/analytics/api-http?qid=JzRVlkZ8g48BmHHBnQ)

## **`percentiles`**

The `percentiles` visualization calculates the requested percentiles of the field in the dataset and produces a timeseries chart.

#### Arguments

* `field: number` - a number field
* `percentiles: number [, ...]` - one or more percentiles (a float between 0 and 100)
    * e.g. `percentiles(request_size, 95, 99, 99.9)`

#### Group-By Behaviour

Visualization will produce a seperate result for each group plotted on a horizonal bar chart, allowing for visual comparison across the groups.

!!! example "Examples"
    [`percentiles` query on play.axiom.co](https://play.axiom.co/analytics/api-http?qid=auEZhk4D789zDxLbyS)  
    [`percentiles` + `group-by` query on play.axiom.co](https://play.axiom.co/analytics/api-http?qid=xADc7czdxNfgHFBnK0)

## **`histogram`**

The `histogram` visualization buckets the field into a distribution of N buckets, returning a timeseries heatmap chart.

#### Arguments

* `field: number` - a number field
* `nBuckets: number of buckets to return
    * e.g. `histogram(request_size, 15)`

#### Group-By Behaviour

Visualization will produce a seperate result for each group plotted on a timeseries histogram. Hovering over a group in the totals table will show only the results for that group in the histogram.

!!! example "Examples"
    [`histogram` query on play.axiom.co](https://play.axiom.co/analytics/api-http?qid=uHgCGk04C1s8oU1box)  
    [`histogram` + `group-by` query on play.axiom.co](https://play.axiom.co/analytics/api-http?qid=pPskm8Uz43MpBlq1cf)