<div class="axi-header">
  <h1>Analyzing Data</h1>
</div>

**The Analytics page allows you to gain insights from your data visually.**

Rather than inspect individual events, you can run aggregations across all or a subset of events in a dataset and visualize the output. Queries can be crafted to get any level of detail from results, and are easily saved for future use as well as being easy to share with team members.

This guide will introduce the Analytics page and it's components to allow you to unlock powerful insights from your data.


## Select a Dataset

As all events in Axiom reside in a *dataset*, we have to first choose a dataset to analyze. When no dataset is chosen, you will be presented with a list of your datasets and quick-access panels for recent [Starred Queries](#starred-queries) and [Query History](#query-history):

<img class="axi-window" src="/assets/shots/analyze-datasets.png" alt="datasets overview" />

Select a dataset from the **Datasets** list to continue:

<img class="axi-crop" src="/assets/shots/analyze-datasets-list.png" alt="datasets list" />


## Dataset Overview

Upon selecting a dataset, the next page will provide an overview of the dataset, it's fields, starred queries, query history and, most importantly, the Query Builder:

<img class="axi-window" src="/assets/shots/analyze-dataset.png" alt="datasets overview" />

Below we explore the different components of this page:

### Fields List

The fields list gives an overview of all fields from all events that are in this dataset. Fields are presented with the following information:

#### Field Type

* Supported types are:
    * `string`
    * `number`
    * `boolean`
    * `array`
* Field names are flattened with dot-notation so an event like ` { "foo": { "bar": "baz" } }` as a field called `foo.bar`

#### Field Name

Field names match the JSON specification, however field names containing periods (`.`) will be folded.


#### Quick Charts

Quick charts allow fast charting of fields depending on there field type. For example, `number` fields will have quick charts for easily visualizing percentiles, averages, and histograms.

<img class="axi-crop" src="/assets/shots/analyze-fields-list.png" alt="fields list" />


### Virtual Fields

Virtual Fields are powerful expressions that run on every event during a query to emit new data from existing. They are similar in behaviour to derived columns/fields from other datastores, but super-charged with an expressive interpretor and with the flexiblity to add/edit/remove them at any time.

Available on the toolbar, the Virtual Fields slide-out will allow viewing and management of a dataset's virtual fields:

<img class="axi-crop" src="/assets/shots/analyze-toolbar-vfields.png" alt="virtual fields tool button" />

<img class="axi-crop" src="/assets/shots/analyze-slideout-vfields.png" alt="virtual fields slideout" />

From this slide-out, you can managing existing virtual fields or create new ones. Just click on "Add Virtual Field" or an existing virtual field to open the editing dialog.

### Starred Queries

Starred Queries are queries that you or your team have saved for future use. They are great for keeping a list of useful queries against a dataset, and there is no implicit need to share as all starred queries for a dataset are shared between the team.

Get started by selecting the Starred Queries button on the toolbar to open the slid-out:

<img class="axi-crop" src="/assets/shots/analyze-toolbar-starred.png" alt="starred tool button" />

### Query History

Every query you and your team members run is given a unique id and saved inside Axiom so it's very easy to share results with other members, as well as easily find a query that you might have lost and want to star for future use.

Get started by clicking on the Query History button on the toolbar:

<img class="axi-crop" src="/assets/shots/analyze-toolbar-query-history.png" alt="query history tool button" />

Once the slide-out is open, historical queries are presented in reverse-chronological order, and you can choose between your own queries or those of your team:

<img class="axi-crop" src="/assets/shots/analyze-slideout-query-history.png" alt="query history slideout" />


### Query Builder

While the other sections help you run pre-determined or historical queries, the Query Builder component lets you begin crafting a new query. Find out more [below]("#building-a-query").


## Building a Query

The Query Builder is a mainstay in the Analytics page, it is always available to create or edit queries against the seleced dataset:

<img class="axi-crop" src="/assets/shots/analyze-query-builder.png" alt="query builder" />

This component is a visual query builder that eases the process of building visualizations and segments of your data. With built-in autocomplete, suggested values, and much more, the Query Builder is the quickest and easiest way to deep-dive into your data.

This guide walks you through the individual sections of the Query Builder, showing you how to get the most out of your data:


### Time Range

Every query has a start and end time and the Time Range component allows quick selection of common time ranges as well as the ability to input specific start and end timestamps:

<img class="axi-crop" src="/assets/shots/analyze-timerange.png" alt="time range" />

<img class="axi-crop" src="/assets/shots/analyze-timerange-menu.png" alt="time range menu" />

* Use the **Quick Range** items to quickly select popular ranges
* Use the **Custom Start/End Date** inputs to select specific times
* Use the **Resolution** items to choose between various time bucket resolutions


#### Against

When a timeseries visualization is selected, such as `count`, the **Against** menu is enabled and it is possible to select a historical time to compare the results of your time range too.

For example, if you wanted to compare the the last hour's average response time to the same time yesterday, you'd select `1 hr` in the time range menu, and then select `-1D` from the Against menu:

<img class="axi-crop" src="/assets/shots/analyze-timerange-against-menu.png" alt="time range against menu" />

The results would look like this:

<img class="axi-crop" src="/assets/shots/analyze-timerange-against-chart.png" alt="time range against chart" />

The dotted line represents results from the 'against' date, and the totals table includes the comparative totals.


### Visualizations

Axiom provides powerful visualizations that display the output of running aggregate functions across your dataset. The Visualization menu allows you to add these visualizations and, where required, input their arguments:

<img class="axi-crop" src="/assets/shots/analyze-visualizations-menu.png" alt="visualizations menu" />

You can select a visualization to add it to the query. If a visualization requires an argument (such as the field and/or other parameters), then the menu will allow you to select eligible fields and then allow you to input those arguments. Pressing <enter> when you are done will complete the addition:

<img class="axi-crop" src="/assets/shots/analyze-visualizations-demo.gif" alt="visualizations demo" />

You can click on a visualization in the Query Builder to edit it at any time.

<a class="axi-link-button" href="/reference/visualizations" title="Find out about visualizations">
  <img src="/assets/analyze.svg" width=24 alt="analyze icon" />
  <span>Learn about supported visualizations</span>
  <img src="/assets/chevron-right.svg" width=16 alt="go" />
</a>

### Filters

Use the Filter menu to attach simple or complex filter clauses to your search. 

Axiom supports AND/OR operators at the top-level as well as one level deep. This means you can create filters that would read as `status == 200 AND (method == get OR method == head) AND (user-agent contains Mozilla or user-agent contains Webkit)`.

Filters are divided up by the field type they are operating on, though some may apply to more than one field type.

<img class="axi-crop" src="/assets/shots/analyze-filters-demo.gif" alt="filters demo" />

#### List of Filters

*String Fields*

* `==`
* `!=`
* `exists`
* `not-exists`
* `starts-with`
* `not-starts-with`
* `ends-with`
* `not-ends-with`
* `contains`
* `not-contains`
* `regexp`
* `not-regexp`

*Number Fields*

* `==`
* `!=`
* `exists`
* `not-exists`
* `>`
* `>=`
* `<`
* `<=`

*Boolean Fields*

* `==`
* `!=`
* `exists`
* `not-exists`

*Array Fields*

* `contains`
* `not-contains`
* `exists`
* `not-exists`


#### Special Fields

* `_time` - the timestamp of the event. This is automatically set to system time if it is missing from the event.
* `_sysTime` - the system time related to when the event was ingested.

`_time` and `_sysTime` can be used interchangably for the majority of cases however, if your events do set a `_time` explicitly, the `_sysTime` can be very useful to know if events are being ingested in case of clock skews etc on your event-producing systems.


### Group By (Segmentation)

When visualizing data, it can be incredibly useful to segment data into specific groups to more clearly understand how the data is behaving.

The Group By component makes it very easy to add one or more fields to group events by:

<img class="axi-crop" src="/assets/shots/analyze-groupby.png" alt="group by" />


### Misc Options

#### Order

By default, Axiom will automatically choose the best ordering for results. However you can manually set the desired order through this menu.

#### Limit

by default, Axiom will choose a reasonable limit for the query that has been passed in. However you can control that limit manually through this component.


## The Results View

Query results are presented beside the Query Builder in the Results View:

<img class="axi-window" src="/assets/shots/analyze-results.png" alt="results view" />

The results view adapts to the query that has been run and so it will add and remove components as necessary to give you the best experience.

---

The components that it can present are explained below:

### Status Bar

The status bar is always visible and gives details on the currently running or last-run query.

### Charts

The charts component will display all the visualizations that you have added to the query. Hovering over charts will give extra detail on each result set.

On timeseries charts, hovering over a specific time will show the same marker on similar charts for easy comparisons.

### Totals Table

The totals table is the totals from each of the aggregate functions that have run for the visualizations you have requested.

If the query included group-by clauses, then there will be a row for each group that is part of the results. Hovering over a group row will highlight the group's data on timeseries charts.

### Matches

If no visualizations are added to the query, then the matches table will list the raw query results (events).