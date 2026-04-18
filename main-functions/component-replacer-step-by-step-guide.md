---
description: >-
  How to use the Component Replacer of the Adobe Analytics Bulk Component
  Manager for Google Sheets
---

# Replacer

## Summary

The Component Replacer ("Component Usage" -> Run Component Replacer") **replaces a component by another one.** This is useful for cleaning up duplicates (see the "duplicate" columns in the Component Usage tab) or automatically updating existing workspaces / segments to a new component when an old one is deprecated.

{% hint style="info" %}
Read the "**Important Restrictions" further down before starting** with your first replacement job.
{% endhint %}

![The Component Replacer in the menu](<../.gitbook/assets/image (48).png>)

The Component Replacer scans for the components to be replaced in:

* **all Workspaces** (restrictions below!)
* **Segment Definitions**
* **Calculated Metric Definitions**

If the Replacer finds the component to be replaced, it updates the Workspace/Segment/Calculated Metric.

The Component Replacer supports replacing **all component types, i.e.**:

* Dimensions: e.g. eVars (e.g. eVarX by eVarY), props and Classifications, but also built-in components like "Site Sections" or "Page Name"
* Metrics ("Success Events")
* Segments
* Calculated Metrics
* Date Ranges

The following 2 videos show how the replacer works.

### Video 1: How to auto-replace Components

{% embed url="https://www.youtube.com/watch?v=uEPeSQga4yU" %}
Get through the basics of the replacer in this video
{% endembed %}

### Video 2: How to harmonize duplicate components with the replacer

{% embed url="https://youtu.be/ZAWbdSkntn4" %}
How to use the "Suggest Duplicates to Harmonize" feature, and how to detect and harmonize duplicate components manually. \
Note that the feature has been improved to prioritize components that are shared with all users (includeType "shared") over plain "matches".
{% endembed %}

## Important Restrictions to understand before starting

The Component Replacer has some important restrictions. In the following, "**old component**" refers to the component to be replaced, and **"new component"** to the component that replaces the old component.

{% hint style="info" %}
Check the **Replacement Log** that you get in the **update\_log** tab after the replacements have completed. It is an Excel sheet with all successful and failed replacements.
{% endhint %}

#### Old and new component **have to be of the same type**

E.g., replacing a segment by a dimension will not work and can even cause your workspace to break. You _can_ replace a prop by an eVar or a built-in dimension (e.g. "Page Name") by e.g. eVar78, but make sure you know what you are doing (e.g. do not replace a list prop by an eVar or a Merchandising eVar by a prop).

### To avoid breaking **things**, limit the **replacements to certain Report Suites**

If you use the Replacer for the first time, it asks you to go to the "report\_suites" tab to select the Report Suites where to do the replacements:

![](<../.gitbook/assets/image (2).png>)

#### What does this Report Suite Filter do?

The Report Suite filter is important if you want to replace components that work differently from Report Suite to Report Suite.&#x20;

For **example**, assume you want to replace&#x20;

* eVar10 ("Page Category deprecated")&#x20;
* by eVar20 ("The new Page Category").

But you have multiple Report Suites in your Adobe Analytics account:

* In Report Suite A-C, eVar10 was set up as "Page Category deprecated",&#x20;
* but in Report Suite D, eVar10 was set up as "Product Type".&#x20;

You obviously want to replace only those eVar10's that are used in the context of Report Suite A-C (where they mean "Page Category deprecated").&#x20;

This is where the Report Suite Filter kicks in. It limits the replacements in the following manner:

* **Workspace panels** that are from other Report Suites will not be updated
* **Segments and Calculated Metrics** will only be updated if their **Parent Report Suite** is among the filtered Report Suites. You can see the Parent Report Suite e.g. in the "**all\_comp\_usage**" tab under "**rsid**":&#x20;

![Find the Parent Report Suite of your segment or calculated metric](<../.gitbook/assets/image (115).png>)

### How to apply the Report Suite filter

Go to the **report\_suites tab** and get the latest list of your report suites by running **"Other -> Refresh Report Suites"**:

![](<../.gitbook/assets/image (69).png>)

Now select all the Report Suites for the Replacer in the **column "replace in panels from these RS"**:

![](<../.gitbook/assets/image (6).png>)

Now go back to the replacer tab, and you see the selected Report Suites listed:

![](<../.gitbook/assets/image (12).png>)

### Other Restrictions

* **Workspaces that were last saved before ca. 2020** when Workspaces did not support Report Suite selectors in panels yet **cannot be updated via the Component Replacer.** This is because their data model is older (no Report-Suite-specific panels etc.). To include these Workspaces in the replacement process, open and save them once. In the **Replacement log** that you get after the Replacer has run, you can find a note in the "projects\_replace\_fail" column saying _"no RS panels.Open project->save->try again"_.
*   **Replacing dimensions in Workspaces will not work when the dimension is used as a** "**dimensional value filter**" (where you drag in a dimensional value into a table or under a column). This is because Adobe Analytics, in this case, does not save the actual value ("e.g. "campaignXY"), but a value ID (e.g. "1234". This value ID is tied to the current dimension and makes no sense in another one (or even returns a completely different value). This only affects Workspaces. The replacement log will show you the workspaces where this was the case in the "projects\_replace\_fail" column saying:

    ```
    {proj_id}:panel {panel_id}:dim val filter for {id_old} cant be auto-replaced.
    ```
* Since the Replacer is built on top of the Component Usage Tab, **replacements only happen in Workspaces that are within the Component Usage Tab filters from the "config" tab**. So if you e.g. have a filter set to update the Component Usage Tab only for Workspaces with a modification date newer than 20210101 ("wsp\_mo&#x64;_\__&#x64;ate\_from"), only workspaces within that filter will be taken into account
* Likewise, check the "comp\_max" and "wsp\_max" cells in the config tab for the current **maximum of components and Workspaces to scan** with a single run. Contact your Component Manager Admin for a best practice how to work around limits if your Adobe Analytics account is really huge.
* Replacements only work in classical Workspaces, so e.g. not in **Mobile Scorecard** **Projects**.
* **Template Components** (built-in components like "Conversion Rate") cannot be updated (obviously)
* When replacing built-in dimensions, make sure the replacement makes sense. E.g. replacing a special animal like "Hit Depth" in Segments by e.g. "eVar8" will cause the segment to break.

## How to replace: Step by Step

1. If you have not updated the Component Usage tab in a long time, run "Adobe Component Manager" -> "Component Usage" -> "**Update Component Usage tab**" first. The Component Usage tab ("**all\_comp\_usage**") is also the best place to identify components that should be replaced (e.g. duplicates).
2. Identify the components you want to replace.
3. Go to the **"replacer"** tab
4. Under **"Old IDs" and "Old Names"**, paste the IDs and (optionally) names of the components you want to replace by others. The easiest way is to simply copy and paste them from the "**all\_comp\_usage**" tab. Avoid inserting the same ID in multiple rows!
5. Under **"New IDs" and "New Names"**, paste the IDs and (optionally) names of the components that should replace the old ones. Here you can insert the same ID in multiple rows, e.g. to merge 5 duplicate segments into 1.
6. In the main menu, choose "Adobe Component Manager" -> "Component Usage" -> "**Run Replacer".**

![Start the replacer and relax... :)](<../.gitbook/assets/image (17).png>)

You can now follow the process in the status field.  :)

### The Replacement Log

When done, you will get a link to a **replacement log** file (CSV) where you can see if your replacements worked.

![Check the log file, especially if it says there were issues.](<../.gitbook/assets/image (80).png>)

![The Replacement Log CSV](<../.gitbook/assets/image (18).png>)

The Replacement Log contains the Projects (Workspaces), Segments and Calculated Metrics where the old Component ID was found.  So if a project does not show up there, it means the component simply did not exist in that workspace at the time it was scanned.

For each **Component Type** (Project, Segment, Calc Metric), there is a **"\_success" (replacement worked) and a "\_fail" column.**

In the **Projects columns**, you see comma-separated status messages for each project-panel combination, e.g. **{project id 1:panel id 3 of project 1:message in case of fail}.** The optional message helps you in the "\_fail" column to understand why a replacement may not have worked. In the example above, we see in the first row: _"dim val filter variables/evar130 cant be auto-replaced"._ This refers to the restriction with dimensions when used as dimensional value filters mentioned above (see "_Replacing dimensions in Workspaces will not work when the dimension is used as a "dimensional value filter")._

For Calculated Metrics and Segments, you see comma-separated messages in the format **{component id:message in case of fail}** (one message per component in which a replacement took place or should have taken place).
