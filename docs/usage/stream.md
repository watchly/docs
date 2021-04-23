<div class="axi-header">
  <h1>Streaming Data</h1>
</div>

Axiom stream feature lets you Process, analyze high volumes of high-velocity data from a variety of sources in real time. 

**The Streaming page allows you to inspect individual events and watch as they are ingested live.**

It can be incredibly useful to be able to live-stream events as they are ingested to know what is going on in the context of the entire system. Like a supercharged-terminal, the Stream page in Axiom allows you to view streams of events, filter them to only see important information, and finally inspect each individual event.

This guide will introduce the Stream page and it's components to allow you to unlock powerful insights from your data.

## Choose a Dataset

Similar to the [Analytics page](/usage/analyze), the Stream page requires a selected dataset. And so the default view is one where you can easily see which datasets are available and also see some recent Starred Queries in case you want to jump directly into a stream:

<img class="axi-window" src="/assets/shots/stream-datasets.png" alt="datasets overview" />

Select a dataset from the **Datasets** list to continue.

## Event Stream

Upon selecting a dataset, you are immediately taken to the live event stream for that dataset:

<img class="axi-window" src="/assets/shots/stream-event-stream.png" alt="event stream" />

You can  click on an event to be taken to the event details slideout:

<img class="axi-crop" src="/assets/shots/stream-event-details.png" alt="event details" />

On this slide-out, you can copy individual field values, or copy the entire event as JSON.

## Filtering

As with the [Analytics page](/usage/analyze#filters), the Steam page provides access to a powerful filter builder right in the toolbar:

<img class="axi-crop" src="/assets/shots/stream-filter-bar.png" alt="filter bar" />

It provides all the features of the filter bar on the Analytics page, and so please [review that documentation](/usage/analyze#filters) for more information.


## Time Range Selection

The stream has two time modes:

* Live stream (default)
* Time Range

Live stream continuously checks for new events and presents them in the stream.

Time range will only show events that fall between a specific start and end date, this can be very valuable when investigating an issue. THe time range menu has some options to quickly choose some time ranges, or you can input a specific range for your search:

<img class="axi-crop" src="/assets/shots/stream-time-range-menu.png" alt="time range menu" />

When you are ready to return to live streaming, simply click this button:

<img class="axi-crop" src="/assets/shots/stream-live-button.gif" alt="return to live button" />

Clicking on the button again would pause the stream.


## View Settings

The stream view is customizable via the view settings menu:

<img class="axi-crop" src="/assets/shots/stream-view-menu.png" alt="view menu" />

Options include:

* Text size used in the stream
* Whether to wrap lines
* Whether to highlight severity (this is automatically extracted from the event)
* Whether to show the raw event details
* Which fields should be added to the stream view in their own column

## Starred Queries

Similar to the Analytics page, the starred queries slide-out is activated via the toolbar:

<img class="axi-crop" src="/assets/shots/stream-toolbar-starred.png" alt="starred queries" />

---


**[Find out more about starred queries here](/usage/analyze#starred-queries).**