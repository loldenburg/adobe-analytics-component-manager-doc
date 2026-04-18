---
description: >-
  How to make the magic happen around Virtual Report Suites Curated Components
  in the Adobe Analytics Component Manager for Google Sheets.
---

# Configuring Virtual Report Suites

You can set up the VRS's your Component Manager should support in the "**config**" tab in cells A4:B4 and below (column C "Import Sheet Prefix" is no longer needed).&#x20;

Simply **add a row per VRS ID and a "readable name"** (will be used in column headers in other sheets).&#x20;

_**Important:** All VRS's need to have_ [_**Component Curation**_](https://experienceleague.adobe.com/docs/analytics/components/virtual-report-suites/vrs-components.html?lang=en) _**enabled** and contain **at least one Curated Component!**_

![Add the VRS's your Component Manager should support here ](<../.gitbook/assets/image (68).png>)

{% hint style="info" %}
You can find a **list of all Report Suite IDs including Virtual Report Suites** in the "report\_suites" tab. Refresh the list via "Other -> Refresh Report Suites".
{% endhint %}

After updating the config tab, **run "Component Editor -> Reload Components from AA"** and "**Component Usage -> Update Component Usage Tab".**

You will then see Virtual Report Suites-related functionality in the following places:

* [**Component Editor**](the-component-editor-tab.md)**:** there will be a column for each VRS, and you can now add/remove components to/from one or more VRS's "Curated Components" and define "Curated Names" in bulk
* [**Component Usage**](the-component-usage-tab.md) (`all_comp_usage`) / **Full Components** (`full_comp_import`) tabs: additional columns to the right show if a component is among the Curated Components of a VRS and what its "Curated Name" is there.

![The VRS Columns in the Component Editor](<../.gitbook/assets/image (67).png>)

![VRS in columns in the "full\_comp\_import" and "all\_comp\_usage" (Component Usage) tabs. ](<../.gitbook/assets/image (51).png>)
