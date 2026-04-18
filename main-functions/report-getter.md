---
description: >-
  Exports reports from Adobe Analytics to Google Sheets and allows scheduling
  them regularly.
---

# Report Getter

{% hint style="info" %}
Please [install the AA Component Manager Google Sheets Add-on](../getting-started-with-the-component-manager/) before continuing.
{% endhint %}

## Video Guide

The following video guide shows the main functionalities. Note that the menu has now moved to **Extensions -> AA Component Manager** (the video shows an older version).

{% embed url="https://www.youtube.com/watch?v=wHGPFsc3uOA" %}

## Step-by-Step Guide

First, Select **Reports -> Create New Report** (You can create as many reports as you like)

<figure><img src="../.gitbook/assets/image (169).png" alt=""><figcaption></figcaption></figure>

Now, enter a name for the new report tab.&#x20;

{% hint style="info" %}
You can change the tab name later, but if you have a report schedule tied to this tab, the schedule will fail if it cannot find a tab with this name anymore. If you want to change the name, first deactivate the running schedule, then change the name of the tab, then reactivate the schedule.
{% endhint %}

A new tab is created. Now go to the Analysis Workspace. Enable the debugger via **Help -> Enable debugger:**

&#x20;

<figure><img src="../.gitbook/assets/image (191).png" alt=""><figcaption></figcaption></figure>

Now go to the freeform table report that you want to export to GoogleSheets and click on the Debug icon on the top right of the table, then on "Freeform Table":

<figure><img src="../.gitbook/assets/image (166).png" alt=""><figcaption></figcaption></figure>

If you see multiple timestamps, click on the last one:

<figure><img src="../.gitbook/assets/image (196).png" alt=""><figcaption></figcaption></figure>

Copy the **JSON Request** to your clipboard:

<figure><img src="../.gitbook/assets/image (167).png" alt=""><figcaption></figcaption></figure>

Go to your Google Sheet Report tab and paste the JSON into the "**Query Payload**" field:

<figure><img src="../.gitbook/assets/image (194).png" alt=""><figcaption></figcaption></figure>

Choose **daily or no granularity.** Daily granularity will get you the data for each day in the date range as a 2-dimensional report (first dimension: day, second dimension: the dimension from your AA report).

<figure><img src="../.gitbook/assets/image (175).png" alt=""><figcaption></figcaption></figure>

Select a **start and end date**. Double-click into the field to get a date picker overlay. You can also type in the date manually (date format "2022-11-22") or **use formulas,** e.g. `=TODAY()-1` (=>yesterday) to refer to rolling date ranges. This is especially useful for scheduled reports.

<figure><img src="../.gitbook/assets/image (168).png" alt=""><figcaption></figcaption></figure>

**Results:** Type in the number of desired results (=rows)**.** The maximum is 50'000 (limited by the Adobe Reporting API). See more under [Limitations](report-getter.md#limitations). To make your report fast and avoid stretching the infrastructure unnecessarily (also think of the greenhouse gas emissions that this creates), use a sensible limit, e.g. don't use 50'000 rows if the first 5'000 rows give you enough information.

<figure><img src="../.gitbook/assets/image (192).png" alt=""><figcaption></figcaption></figure>

**Headers:** Choose technical Component **IDs** (don't change, but hard to read or even cryptic (Calculated Metrics) or Component **Names** (human-readable like in the interface, but can change).

<figure><img src="../.gitbook/assets/image (206).png" alt=""><figcaption></figcaption></figure>

**Export Destination (New!):** Choose **"Sheet"** or **"CSV":**

<figure><img src="../.gitbook/assets/image (231).png" alt=""><figcaption></figcaption></figure>

* **Sheet:** The report data is written to the same tab below
* **CSV** (Premium only): After each run, an CSV download link is provided to the right. Since Google Sheets can handle only a limited number of cells and large sheets get very slow, exporting daily-granular data with tens of thousands of rows each day can make your sheet unusable. With the CSV option, you don't need to worry about these limits:

<figure><img src="../.gitbook/assets/image (232).png" alt=""><figcaption><p>When choosing "CSV" as the export format, a "Last Export Location" link will be written to the sheet once the report completes.</p></figcaption></figure>

**Run the Report:** Select **AA Component Manager -> Reports -> Run Report**.&#x20;

<figure><img src="../.gitbook/assets/image (209).png" alt=""><figcaption></figcaption></figure>

Follow the status updates on the top of the sheet. It tells you when the report has finished.

<figure><img src="../.gitbook/assets/image (187).png" alt=""><figcaption></figcaption></figure>

That's it: Enjoy digesting your report data!

<figure><img src="../.gitbook/assets/image (161).png" alt=""><figcaption></figcaption></figure>

### Schedule a regular Adobe Analytics-to-Google-Sheets report

To activate a regular schedule for a report, go to the tab on which the report is that you want to schedule.

Next to "**Schedule**", choose your schedule, e.g. "**daily at 13:00**". Times are in UTC.

<figure><img src="../.gitbook/assets/image (164).png" alt=""><figcaption></figcaption></figure>

Now select **AA Component Manager -> Report -> Activate Schedule.**

<figure><img src="../.gitbook/assets/image (204).png" alt=""><figcaption></figcaption></figure>

After some seconds, you see the scheduled report confirmation in these 2 places.

<figure><img src="../.gitbook/assets/image (179).png" alt=""><figcaption></figcaption></figure>

Your report will get scheduled every day now (around 4 AM UTC).&#x20;

{% hint style="info" %}
Note that the scheduled report is generated based on the settings of the report tab **at the moment of delivery**!&#x20;

Assume that you e.g. have a daily scheduled report with daily granularity and your settings report tab today says "1000 results". You receive the report on 2 consecutive days. Both these 2 days will export a maximum of 1000 rows.&#x20;

Now you change the setting to 5000 results. The next run will get 5000 results, but only for that incremental day. The already imported days are left untouched.&#x20;

If you want to re-run the report for all of the days, simply delete the existing report data, and then run a manual granular report with 5000 results once.
{% endhint %}

### Deactivate a schedule

To **deactivate a schedule,** simply choose **AA Component Manager -> Reports -> Deactivate schedule.**  You will get a confirmation in the status bar, and "Active Schedule" now says "none" again:

<figure><img src="../.gitbook/assets/image (184).png" alt=""><figcaption></figcaption></figure>

## Limitations

#### **Row Limit**&#x20;

The Adobe Analytics Reporting API allows for a maximum of 50'000 rows to be exported. When using date-granular reports, the row limit is 50'000 **per day**. So a report for 10 days with a limit of 50'000 rows will require a maximum of 500'000 rows in total.

#### **One-dimensional reports only**&#x20;

Similar to Analysis Workspace's "export to CSV" feature, you cannot export multi-dimensional reports, since the Adobe Analytics Reporting API is incapable of doing this for larger amounts of data. \
\
The **exception are date-granular reports** which are 2-dimensional where the first column is the date and the second column the actual dimension.

#### **8:30 minutes maximum per report query**&#x20;

A report will fail it takes longer than 8:30 minutes to generate. For date-granular reports, this limit applies only to each individual day, not the time for all days together. So if you have a daily-granularity report across 30 days and each individual day takes less than 8:30 minutes, that is fine.&#x20;

#### **24 metrics (columns) maximum**&#x20;

To not sacrifice on performance, the Report Getter can process a maximum of 24 metrics (columns). If you use segments or date ranges to **split a metric into multiple columns**, those count as their own columns and will display the metric name only. \
\
Example: A table like this ...&#x20;

<figure><img src="../.gitbook/assets/image (181).png" alt=""><figcaption></figcaption></figure>

... will end up in the Google Sheet like this:

<figure><img src="../.gitbook/assets/image (185).png" alt=""><figcaption></figcaption></figure>

So instead of splitting columns, create individual calculated metrics that contain the segment you use for splitting. Ideally, all your your columns are just one green component (= 1 (calculated) metric).
