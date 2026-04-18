---
description: >-
  How to use the "Compare Report Suites" tab to find inconsistencies across
  Report Suites
---

# Compare Report Suites

## Summary

The “compare\_rs” tab gives you a comparison of all Report Suites’ **eVars, props, Success Events including all List variables and Classifications’** names and descriptions.&#x20;

### Short Video guide

{% embed url="https://www.youtube.com/watch?v=6p7ZTR12hgk" %}

### Full Guide

1. Select the Report Suites to compare in the report\_suites tab:&#x20;

![](<../.gitbook/assets/image (37).png>)

2\. Run the Comparison via Report Suites -> Compare Report Suites:<br>

![](<../.gitbook/assets/image (26).png>)

3\. You are now taken to the "compare\_rs" tab and the comparison starts. After it is done, you see a screen like the one below.

The column “**Differences**” highlights the components that are not identically set up in all Suites. Then you can simply scan through the columns to the right to see where the differences are (to protect the client, I am showing “Rep Suite 1–14” instead of the real Report Suite IDs you normally see there).

![Clean, consistent variable setup
](<../.gitbook/assets/image (65).png>)

![Variable setup with inconsistencies](<../.gitbook/assets/image (81).png>)

#### Transparency and Version Control for your Report Suites

Simply run this function **regularly**, e.g. once a week (you can ask your Datacroft contact to set up such a regular run), and you always have the latest state as well as the history. Because in the Google Sheets version history, you can always go back.

Version History of Google Sheets is not exactly Git, but pretty useful anyway

![Version Control in Google Sheets helps finding out past statuses](https://miro.medium.com/max/582/1*UImnQ-Uwm2_Kjve6D9Bo2Q.png)

This makes it a lot easier to find out when something was deleted or edited accidentally and what that eVar was like before that guy accidentally changed it. And of course, it makes finding inconsistencies in your setup and reconciling those a lot easier.

### Found differences? Now reconcile them across multiple Report Suites

You can do extremely convenient bulk-editing for eVars, props and Success Events across multiple Report Suites with the [**Report Suite Editor**](report-suite-editor-evars-props-success-events.md).

See [more tips on standardizing your Report Suite setup](https://lukas-oldenburg.medium.com/9e57bb54ec88).
