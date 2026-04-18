---
description: How to use the Component Editor (component_editor) tab
---

# Component Editor

## Summary

The Component Editor (`component_editor`) tab allows you to:

* edit or delete components globally&#x20;
* or for Curated Components of multiple Virtual Report Suites (VRS) at once: You can&#x20;
  * add or remove them from VRS or
  * edit their VRS-specific "Curated Name"

![The Component Editor tab and its menu functions](<../.gitbook/assets/image (77).png>)

## Step-by-Step Guide

### 1. Reload all Components from Adobe Analytics

First you want to make sure to work with the most recent state in your Adobe Analytics account. For that, quickly reload the components from Adobe Analytics by clicking on "Component Editor" -> "Reload Components from AA":

![Refresh the Component Manager by reloading all components from AA](<../.gitbook/assets/image (66).png>)

### 2. Select the Components for editing via the "Component Viewer"

In the background, this actually refreshes the `full_comp_import` tab, which is where the "**Component Viewer**" reads from. In the Viewer (on the blue-green left side), you can view a list of all components, or only the curated components of a specific VRS by selecting a VRS in the drop-down menu on top:&#x20;

![Filter the components you want to see on the left side.](<../.gitbook/assets/image (106).png>)

{% hint style="info" %}
You can [**configure the VRS's**](configuring-virtual-report-suites.md) for your Component Manager in the "**config**" tab in cells A4:B4 and below (column C "Import Sheet Prefix" is no longer needed).
{% endhint %}

Then simply copy the IDs of the components you want to edit to the "ID" column of the Component Editor (the orange part on the right). Wait a couple of seconds, the Component Editor will automatically populate the other columns with the current values:

{% embed url="https://www.youtube.com/watch?v=GbhDr34aGeM" %}
How to copy from the Component Viewer to the Component Editor
{% endembed %}

Of course, you can copy the IDs from any of the other tabs as well. It does not have to be from the "Component Viewer".

### Supported Edit or Delete Operations

The Component Manager supports the following operations:

1. **change:** change name/description globally or VRS-specific curatedName
2. **add:** add to VRS
3. **remove:** remove from VRS
4. **delete:** delete globally (component will be gone)

See the following screenshot for a visual explanation:

![Supported Editing and Deletion options](<../.gitbook/assets/image (36).png>)

### Which Component Types can be edited/deleted?

* VRS operations (**add/remove/change curated name**) are supported for **any component type**
* **change or delete** operations are supported for **segments, calculated metrics and date ranges**
* to **edit eVars, props or Success Events,** **go to the "**[**Report Suite Editor**](report-suite-editor-evars-props-success-events.md)**"**.

### 3. How to edit or delete, step by step:

1. **Copy the Component IDs into the "ID" column** (as many IDs as you'd like), as shown in the previous chapter.
2. Wait for the other columns to populate all columns with the current values.
3. For each component (each row), **choose the** "**method**" (or simply copy-paste), i.e. change/remove/add/delete (explanation in previous chapter).
4. **Edit the "Curated Name", "Name" or "Description" fields** for those components where you want to change something (e.g. add the new name in the "name" column if you want to change the name)
5. If you have any VRS-specific operations (add/remove/change Curated name), **add an "x" to the Virtual Report Suite columns** where these operations should apply.
6. Run **"Component Editor -> Validate Data to Send"**.

![](<../.gitbook/assets/image (8).png>)

{% hint style="info" %}
* Leaving a field **empty** will be interpreted as "no change". As of now, there is no method to entirely "clear" a value. Adding a space " " however does the job.
* You can **combine VRS add/remove operations with changes to the (curated) name or description.** E.g. If your method is "add" or "remove" and you also submit a change to the global or Curated name or the description in the same row, these changes will be executed as well, so you don't need an extra row for them.
{% endhint %}

You are now taken to the **"update\_export"** sheet where you can see a preview of all the planned updates. The **validation** checks if the updates you want to send are "valid". In the example below, the validation failed because no "method" was specified:

![](<../.gitbook/assets/image (90).png>)

Note that this validation is not exhaustive, it covers most of the typical errors.

After successful validation, click **Component Editor -> Send Updates to AA** and confirm the message. You can now follow the updates in the "Status" of the "component\_editor" tab.

![](<../.gitbook/assets/image (9).png>)

&#x20;Once done, you see: "Component update finished. See update\_log tab for effective changes."

{% hint style="info" %}
**What happens to AA functionality if I delete segments or calculated metrics?**

**Analysis Workspace projects** with deleted segments, calculated metrics or date ranges will still work

**DWH Exports** using deleted segments will still work.

API Queries using deleted calculated metrics, segments or date ranges will still work.&#x20;

**Alerts** using deleted segments or calculated metrics usually work, but there has been a case reported where they no longer worked.

You **cannot delete segments that are published to the Adobe Experience Cloud.** These will be reported as "issues" in the update logs (see next tab). Go into these segments in Adobe Analytics, unpublish them from the Experience Cloud and then you try again.

There has recently been a case however where a segment was used in an **Adobe Target** audience, and when that segment was deleted, that Target Activity stopped working. It also did not start to work again after the segment had been revived. So the Target experiment needed to be recreated completely (thanks to Adobe Analytics expert Mirko Catucci from the great [Softlab Italy](https://www.soft.it/en/) team for bringing this to my attention).&#x20;

To avoid that, check your Target experiments for Adobe Analytics segments before deleting them. Another method is to put all your Target and Alert segments and calculated metrics into a Workspace so they never appear as the "zero-usage" components.&#x20;
{% endhint %}

### 4. Check the change (update) logs

The "**update\_log**" tab contains&#x20;

* a list of all changes _sent_ to Adobe Analytics (does not mean the changes were effective)
* a link to an Excel file with a log of the effective results after the change has been executed: In this log file, you can see whether the changes actually were effective or if any errors occurred

![](<../.gitbook/assets/image (119).png>)

Download the log file by double-clicking on the cell next to "Effective changes (logs)" and open it in Microsoft Excel (or import the file into Google Sheets).

The following example screenshot should help you understand how to interpret the update logs. You can also [download this example](https://docs.google.com/spreadsheets/d/16vCgonWHEkTmy7iKYsAVq6pgxEO-2kVw/edit?usp=sharing\&ouid=104141914278396589924\&rtpof=true\&sd=true) for more comfortable viewing:

![How to interpret the update log](<../.gitbook/assets/image (19).png>)

### 5. Clear the Edit Area

To avoid accidentally sending the same change again, it is recommended to clear the edit area after each update run. Select "Component Editor -> Clear Edit Area" to do so:

![](<../.gitbook/assets/image (120).png>)
