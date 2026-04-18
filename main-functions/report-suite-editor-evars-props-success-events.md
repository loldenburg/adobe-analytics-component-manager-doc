---
description: >-
  The "Report Suite Editor" offers editing eVars, props and Success Events in
  bulk.
---

# Report Suite Editor (eVars, props, Success Events)

{% hint style="info" %}
**Note:** To edit or delete segments, calculated metrics, date ranges, curated components and curated names for Virtual Report Suites, see the [**Component Editor**](the-component-editor-tab.md)**.**
{% endhint %}

Want to deactivate 500 Success Events in 10 Report Suites at once?&#x20;

Want to finally get those names, descriptions and settings of your eVars and props streamlined across Report Suites after you found inconsistencies via the "[Compare Report Suites](compare-report-suites.md)" feature?&#x20;

Want to see those variables that track no data so you can disable them?

The "Report Suite Editor" (**rs\_editor** tab) can do all this for you, super-efficiently.

Check out the video guide:&#x20;

{% embed url="https://youtu.be/nAeA39Mirpg" %}
Edit, disable or enable eVars, props & Succes Events across one or more Report Suites
{% endembed %}

## Find Variables without data (new, not shown in video)

To identify those variables that have no data, you can now run **"Refresh Vars w. Stats"** (supported for eVars and Success Events):

<figure><img src="../.gitbook/assets/image (217).png" alt=""><figcaption></figcaption></figure>

This will add the **"Instances last 3 days"** column to the tab. It shows the number of Instances for that variable in the last 3 full days, i.e. the Hits in which the eVar or the Success Event was explicitly set. 0 Instances means you eVar or Event is never set.&#x20;

This helps detect implementation issues or find old stuff that you probably don't need anymore. Go ahead and set "enabled" to FALSE right away, then run "RS Editor: Send Var updates". Done! :smile:

<figure><img src="../.gitbook/assets/image (220).png" alt=""><figcaption></figcaption></figure>

