---
description: >-
  One Adobe Analytics account, so many eVars, props, & Success Events to keep an
  eye on. The Health Report looks at all of them regularly and summarizes the
  biggest changes - even in a Slack channel!
---

# Variable Health Report

The Health Report is a must-have for Admins trying to stay on top of Data Quality issues. Implementations change, bugs happen, and many trends in the data are hard to spot without looking at a lot of reports regularly. While you can and should set up customized Alerts with smart Calculated Metrics in them, you can rarely cover everything.&#x20;

The closest to everything is the "Variable Health Report". It checks all your Metrics (Success Events and Instances of eVars) and Dimensions (eVars, props, Classifications), calculates the trends, and finally summarizes the biggest observations.&#x20;

<div data-full-width="true"><figure><img src="../.gitbook/assets/image (153).png" alt=""><figcaption></figcaption></figure></div>

You can **filter the Variable Health report by segments** of your choice. You can **schedule** it to run daily or weekly.

You can create **as many Variable Health reports as you like,** e.g., one for dimensions in Report Suite 1 with Segments S and T applied, and another one for metrics,plus another one for data from another Report Suite.&#x20;

In addition to the summary being shown in the Google Sheet, it can also be sent to a **Slack Channel** of your choice.

<figure><img src="../.gitbook/assets/image (144).png" alt="" width="507"><figcaption></figcaption></figure>

## Step-by-Step Guide

The following video explains the most important parts of the Variable Health Report:

{% embed url="https://www.youtube.com/watch?v=aaFv1pXOrGo" %}

For more details, see the following chapters:

{% hint style="info" %}
Please [install the AA Component Manager Google Sheets Add-on](../getting-started-with-the-component-manager/) if you haven't yet.
{% endhint %}

### Create a Variable Health Report

From the menu, select Variable Health Report -> Create new Health Report.

<figure><img src="../.gitbook/assets/image (145).png" alt="" width="563"><figcaption></figcaption></figure>

In the popup, give the health report a name, e.g. "metrics\_reportsuiteX". The tab name will be "**health\_**&#x6D;etrics\_reportsuiteX" (with a "health\_" prefix).

{% hint style="info" %}
You can change the name of the tab as long as you don't have a schedule running for the it. Removing the "health\_" prefix will break the health report however.
{% endhint %}

The Health Report has the following main areas:

<div data-full-width="true"><figure><img src="../.gitbook/assets/image (152).png" alt=""><figcaption></figcaption></figure></div>

We will start with the **Report Configuration:**

<div align="center"><figure><img src="../.gitbook/assets/image (148).png" alt=""><figcaption></figcaption></figure></div>

* **Report Suite:** Select the (Virtual or regular) Report Suite from where to pull the data. If the drop-down menu shows nothing to select from, run "Report Suites" -> "Refresh Report Suites" once
* **Variable Type:** Dimensions or Metrics. The "Dimensions" report checks all dimensions for trends, the "Metrics" report does the same for all Metrics. More details below.
* **Period Length:** which time frame (in days) should be looked at? "7" means: Compare the last 7 full days to 8-14 days ago. Enter any value between 1 and 28.
* **Filter by Segment ID(s):** Enter the segment IDs separated by comma that you would like the report to filter the data for. Multiple segments will be stacked (combined with an AND condition), just like in AA. You can find Segment IDs e.g. in the ["full\_comp\_import" tab](the-full_comp_import-tab.md) (refresh it via "Component Editor -> Reload Components").
* **Vars to exclude entirely:** Some variables like User IDs are rarely useful. Others are not useful because you already have the same info in another variable. To speed up the report and avoid useless entries in your report summary, enter any number of variables to exclude from the analysis, separated by comma. You can find the IDs e.g. in the ["full\_comp\_import" tab](the-full_comp_import-tab.md). You can enter the IDs like this:
  * full ID: `variables/evar2, variables/prop37.classificationx, metrics/event89, metrics/evar82instances`
  * ID without prefix: `evar2, prop37.classificationx, event89, evar82instances`
* **Vars to exclude from summary:** Some variables may be of interest in the report details, but you may not want them in the report summary text. Enter them exactly like explained under "Vars to exclude entirely".

### **Run and interpret the Health Report**

Click "Variable Health -> Run Health Report" and confirm the ensuing popup. Now follow the status bar for the progress. In the end, you will see a **summary** in the summary area as well as a **detailed trend report for each metric/dimension** below.&#x20;

The following chapter describes in detail how the reports work:

#### Metrics

If you choose Variable Type "Metrics", the Component Manager will get the Occurrences for all Success Events and eVar Instances for the time periods chosen and compare the values with a "change pct" metric in the column to the right. Thanks to the colored highlights, you quickly see the biggest changes in dark red.

<figure><img src="../.gitbook/assets/image (149).png" alt=""><figcaption></figcaption></figure>

#### **Dimensions**

In the "Dimensions" variant of the Health Report, the Component Manager will get the top 25 top 25 values of both the current and previous period **per dimension** and compare them. The darker the red, the bigger the change. You can of change the conditional formatting via the regular Google Sheets function if you prefer another color scheme.

<figure><img src="../.gitbook/assets/image (150).png" alt=""><figcaption></figcaption></figure>

### **Report Summary**

While scanning through all these rows is still a big time saver, the Component Manager summarize the most important trends for you in the "Report Summary" area as the **"Top 10 Risers**" and **"Top 10 Fallers"**:

{% hint style="info" %}
You can also send the report summary to a **Slack channel.** See below.
{% endhint %}

<figure><img src="../.gitbook/assets/image (155).png" alt=""><figcaption></figcaption></figure>

To show as many useful results as possible, the Report Summary contains the values (metrics or dimensional values) with the biggest changes, sorted by change percentage) with the following restrictions:

* minimum 100 Occurrences in the previous period (e.g. for a 7-day report, the value must have had at least 100 Occurrences 8-14 days ago)
* the change must be at least by 10%

These thresholds can be configured for your account by Datacroft support. Just contact us.

#### Send the Health Report Summary to a Slack Channel

While you can wait and consume the Variable Health Report summary in the Google Sheet itself, it is more convenient to [have it sent to a Slack channel](slack-channel-integration.md) when it is ready, especially when you run the health report automatically from a schedule.&#x20;

The Slack version of the summary is also more readable.&#x20;

Example **"Dimensions" Variable Health Report:**

<figure><img src="../.gitbook/assets/image (143).png" alt=""><figcaption></figcaption></figure>

Example "**Metrics" Variable Health Report**:&#x20;

<figure><img src="../.gitbook/assets/image (156).png" alt=""><figcaption></figcaption></figure>

**Setting up a Slack integration is super-easy**. 😊 Just follow [these instructions](slack-channel-integration.md).

### Scheduling Health Reports

The best way to use the Health Reports is by scheduling them regularly and then consuming them in Slack.&#x20;

Simply select the schedule frequency and time of your choice:

<div data-full-width="true"><figure><img src="../.gitbook/assets/image (230).png" alt=""><figcaption></figcaption></figure></div>

To **activate a schedule**, run "Variable Health Report" -> "Activate Schedule". You will then see the schedule confirmed in the Status Bar as well as next to "**Active Schedule**" on the right.

To **deactivate a schedule**, run "Variable Health Report" -> Deactivate Schedule". Again, you will see the status bar confirmation. Next to "Active Schedule", you will now see "none".

### Further Notes

#### Don't schedule too many reports at the same time

The AA Component Manager uses one and the same API user for all its queries. Adobe has a limit of API requests per minute. When that limit is reached, the Component Manager takes a forced break until it tries again.&#x20;

Thus, if you schedule multiple reports at the same time, it is more likely that your reports take longer than they should have because they will overload the API. This can even lead to your reports going over the 9-minute timeout. See the next chapter on this:

#### Dealing with Report Timeouts

The Health Report can run for a maximum of 9 minutes.

The Metrics report should not take more than a minute or two.&#x20;

The Dimensions report can take longer, depending on the amount of data in your AA account and the number of dimensions chosen.  The status bar should tell you that it was not possible to fetch data for all dimensions in a message like this:

```
Could only get 83 of 130 dimensions. You can try with a shorter time range or by 
reducing the number of dimensions to be checked via 'Vars to exclude entirely'.
```

In this case, try running the report again (some data gets cached by Adobe and thus faster to retrieve the second time). If it still fails to complete, try without Classifications and/or reduce the number of dimensions via the "Vars to exclude entirely" configuration field. Of course, you can also try with a shorter time range.

Additionally, you can ask for an individual longer run by contacting Datacroft support.&#x20;
