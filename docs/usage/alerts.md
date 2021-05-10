<div class="axi-header">
  <h1>Monitoring and Notifiers</h1>
</div>

**Setup Monitors and Notifiers to be alerted when errors or other conditions are met by events.**

This guide will introduce Monitors and Notifiers, and how they work together to enable alerting to you, your team members, and external services.

## Monitors

Monitors are background tasks that can be configured to run queries on intervals and check whether the values produced from the results exceed a threshold. If they do, then a the monitor would switch to a it's *triggered* state and alert external parties via it's Notifier configuration.

<img class="axi-window" src="/assets/shots/monitors-monitors-page.png" alt="monitors page" />

Monitors are very simple to setup and use the same Query Builder as in the [Analytics Page](/usage/analyze). Clicking on the "New Monitor" button or selecting an existing monitor will display the editing slide-out:

<img class="axi-crop" src="/assets/shots/monitors-monitors-slideout.png" alt="monitors slide out" />

With reference to the above monitor slide-out, below is a description of the available options:

### Monitor Options

* **Name** - Used when notifying to indicate which monitor has been triggered
* **Description** - Helpful for team members to understand why this monitor was created
* **Trigger Options** 
    * **Comparison Types**: `above`, `above-or-equal`, `below`, `below-or-equal` are the options on how to compare the values produced by the query to the threshold.
    * **Value** - the value to compare the results of this query to
* **Check Options**
    * **Frequency** - how often the monitor should be run
    * **Time Range** - what should the time range be for the check query (now - $time)
* **Notifers** - connect configured Notifiers to receive alerts when the monitor is triggered ([See below](#notifiers)).

### Query Builder

The monitors query builder mimics that of the Analytics [Query Builder](/usage/analyze#building-a-query) with some restrictions:

* Only one visualization is allowed

The goal of the query is to produce one or more rows of results (> 1 in the case of a group-by being used) that can each be compared to the Trigger Options above to determine whether the monitor is triggered.

---

**Group By**

If a group by clause is used, then a monitor can trigger once for every group that is produced by a query. A monitor will stay triggered until all groups are back within threshold. Groups are a great way of getting more specific alerts where necessary.

### Snooze

A monitor can be snoozed by clicking the 'alarm clock' icon in the slide-out's toolbar. By snoozing a monitor, no checks will be carried out by the monitor until the snooze time is elapsed. As no checks are run, there will be no triggering or notifications either.


## Notifiers

Notifiers are how monitors alert external parties when they are triggered.

Axiom currently supports four notifiers, each of which can be configured multiple times to allow for different options (e.g. separate slack channel notifiers for web and backend). 

---

### Email

Create email notifers with team members to have everyone emailed when a monitor is triggered/resolved.

<img class="axi-crop" src="/assets/shots/monitors-notifiers-email.png" alt="email notifier" />

---


### Slack

Create Slack notifiers to notify specific channels in your Slack organization. Currenly this notifier requires setting up an [Incoming Webhook](https://api.slack.com/incoming-webhooks) for it to work.

<img class="axi-crop" src="/assets/shots/monitors-notifiers-slack.png" alt="slack notifier" />

---

### PagerDuty

Create a PagerDuty notifer to use all the incident management features of PagerDuty with Axiom. Triggered/resolve states will be managed by Axiom, and you can configure schedules/alerting rules/etc inside PagerDuty.

<img class="axi-crop" src="/assets/shots/monitors-notifiers-pagerduty.png" alt="pagerduty notifier" />

---

### Webhook

Create Webhook notifiers to connect to internal or external services using your own handlers. They are simple to setup and contain all the details you'll need.

<img class="axi-crop" src="/assets/shots/monitors-notifiers-webhook.png" alt="webhook notifier" />

