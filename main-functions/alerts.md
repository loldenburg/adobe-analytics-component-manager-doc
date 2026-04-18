---
description: How to get, delete, disable or renew Alerts in bulk.
---

# Alerts

## Summary

All your org's Adobe Analytics Alerts, all in one place together with the rest of your AA components - no problem with the Component Manager. And you delete, disable, or renew Alerts right from the Google Sheet - in bulk.&#x20;

## Get/Refresh Alerts

To get or refresh Alerts in your Component Manager Sheet, simply run:

**Extensions -> AA Component Manager -> Alerts -> Refresh Alerts:**

<figure><img src="../.gitbook/assets/image (123).png" alt=""><figcaption></figcaption></figure>

If you have never done this before, an "alerts" tab is created first. After that, the Component Manager gets all the Alerts including their definitions (JSON), owners, granularity etc. into that new tab:

<div data-full-width="true"><figure><img src="../.gitbook/assets/image (124).png" alt=""><figcaption></figcaption></figure></div>

## Delete, Disable, or Renew Alerts in Bulk

To delete, disable, or renew one or more Alerts, simply put an "**x**" into the colored columns to the right for those Alerts you want to update.&#x20;

* **Delete:** The Alert is deleted and cannot be accessed anymore
* **Disable**: The Alert is paused and won't trigger (send e-mails) anymore. It can be enabled at any time.
* **Renew**: The Alert's expiration time is extended by one year. If the Alert was disabled, it will be enabled again. So if you want to _**enable**_ some Alerts, just "renew" them.

<div data-full-width="true"><figure><img src="../.gitbook/assets/image (127).png" alt=""><figcaption><p>In this example, we would disable 2 Alerts, delete 2 others, and renew one Alert.</p></figcaption></figure></div>

Then, run **Alerts -> Delete/disable/renew Alerts:**

<figure><img src="../.gitbook/assets/image (125).png" alt=""><figcaption></figcaption></figure>

Once the updates are done, you get a link to an Excel file with the results of the operations. If any of the operations failed, you will be notified in the status bar, so you don't need to download the logs every time to check whether everything went well:

<figure><img src="../.gitbook/assets/image (128).png" alt=""><figcaption></figcaption></figure>

