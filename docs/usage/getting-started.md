<div class="axi-header">
  <h1>Getting Started</h1>
</div>

This guide will introduce you to the concepts behind working with Axiom and give a short introduction to each of the high-level features.

<img class="axi-window-shadow" src="/assets/shots/analytics.png" alt="axiom overview" />

## 1. Get your data into Axiom

Axiom supports ingesting structured data which can be sent to it via a variety of means. Each individual piece of data is called an **Event**.

Events can be emitted from internal or third-party services, cloud functions, containers, VMs, or even scripts. Events follow the [JSON specification](https://www.json.org/json-en.html) for which field types are supported, an event could look like this:

```json
{
  "service": "api-http",
  "severity": "error",
  "duration": 231,
  "customer_id": "ghj34g32poiu4",
  "tags": ["aws-east-1", "zone-b"],
  "metadata": {
    "version": "3.1.2"
  }
}
```

An event must belong to a **Dataset**, which is a collection of similar events. You can have multiple datasets that help to segment your events to make them easier to query and visualize, and also aide in access control.

Axiom stores **every event you send** and makes it available to you for querying either by streaming logs in real-time, or by analyzing events to produce visualizations.

The underlying datastore of Axiom is a timeseries database, which means every event is indexed with an accompanying timestamp (which can be specified at ingress or automatically set).

Axiom **does not sample** your data on ingest or querying, unless you've expressly instructed it to.

<a class="axi-link-button" href="/usage/ingest" title="Learn how to ingest">
  <img src="/assets/ingest.svg" width=24 alt="ingest icon" />
  <span>Learn how to ingest</span>
  <img src="/assets/chevron-right.svg" width=16 alt="go" />
</a>

## 2. Stream your data

Axiom makes it really easy to view your data as it's being ingested live. This is also referred to as "Live Stream" or "Live Tail", and the result is having a terminal-like feel of being able to view all your events in real-time:

<img class="axi-window-shadow" src="/assets/shots/stream.png" alt="Axiom stream page screenshot" />

From the Stream page, you can easily add filters to narrow down the results as well as save popular searches and share them with your organization members. You can also hide/show specific fields

Another useful feature of the stream page is to only show events in a particular time-window (this could be the last N minutes, or a more-specific time range you can input manually). This feature is extremely useful when you need to closely inspect your data, allowing you to get an chronological view of every event in that time window.

<a class="axi-link-button" href="/usage/stream" title="Learn how to stream">
  <img src="/assets/stream.svg" width=24 alt="ingest icon" />
  <span>Learn how to stream</span>
  <img src="/assets/chevron-right.svg" width=16 alt="go" />
</a>

## 3. Analyze your data

While viewing individual events can be very useful, at scale and for general monitoring and observability, it is important to be able to quickly aggregate, filter, and segment your data. The Analytics page lets you do just that, and more:

<img class="axi-window-shadow"  src="/assets/shots/analytics.png" alt="Axiom analytics page screenshot" />

The Analyze page gives you various tools to extract insights from a dataset, including **visualizing aggregations** (count, min, max, average, percentiles, heatmaps, and more), **filtering events** (with and/or grouped filters containing one or more field filters), and segmentation via **group-by**.

You can control the time range of your search, and even compare your results to a previous point-in-time using our **Against** functionality. Queries are rounded off with support for time resolution, ordering, and limits.

Any query you create can be saved as well as easily sharable with your team.

<a class="axi-link-button" href="/usage/analyze" title="Learn how to analyze">
  <img src="/assets/analyze.svg" width=24 alt="analyze icon" />
  <span>Learn how to analyze</span>
  <img src="/assets/chevron-right.svg" width=16 alt="go" />
</a>

## 4. Monitor for problems

Get alerted when there are problems with your data, such as

- A queue size is larger than acceptable limits
- Web containers are taking too long to respond
- A specific customer has started using a new feature
- etc, etc

<img class="axi-window-shadow"  src="/assets/shots/alerts.png" alt="Axiom alerts page screenshot" />

Axiom alerting consists of two key concepts:

1. **Monitors** that run in the background querying your data on a frequency and checking whether a threshold has been reached to _trigger_ the monitor, and
2. **Notifiers** which encapsulate how to alert a person, a team, or a service that a monitor has been triggered.

Monitors are configured with a query, a frequency (how often the monitor should run), interval (what is the time range of data that the monitor should query), a threshold (at what value should the monitor trigger), and one or more _notifiers_ (how to alert that the monitor is triggered).

<a class="axi-link-button" href="/usage/alerts" title="Learn how to monitor">
  <img src="/assets/monitor.svg" width=24 alt="monitor icon" />
  <span>Learn how to monitor</span>
  <img src="/assets/chevron-right.svg" width=16 alt="go" />
</a>

## 5. Integrate with Data shippers

Integrations can be installed and configured using different third-party Data shippers to quickly get insights from your logs and services by setting up a background task that continuously synchronizes events into Axiom. 

<a class="axi-link-button" href="/usage/integrations" title="Learn about integrations">
  <img src="/assets/integrate.svg" width=24 alt="integrations icon" />
  <span>Learn about integrations</span>
  <img src="/assets/chevron-right.svg" width=16 alt="go" />
</a>

## 6. Customize for your organization

As your use of Axiom widens, you can customize it for your organization's needs:

- Add more users
- Setup third-party authentical providers
- Create and manage teams
- Setup Role-Base Access Control
- Setup per-user/service API tokens

<img class="axi-window-shadow"  src="/assets/shots/settings.png" alt="Axiom settings page screenshot" />

<a class="axi-link-button" href="/usage/settings" title="Learn about settings">
  <img src="/assets/settings.svg" width=24 alt="integrations icon" />
  <span>Learn about settings</span>
  <img src="/assets/chevron-right.svg" width=16 alt="go" />
</a>
