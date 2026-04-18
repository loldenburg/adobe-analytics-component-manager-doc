---
description: >-
  Get your workpace project schedules, filter by owner, or see which schedules
  have expired and when.
---

# Project Schedules

With daily scheduled projects now (since January 2023) expiring after a month already, it is easy to miss expired project schedules.&#x20;

However, in Adobe Analytics, only Admins can see their expired project schedules, i.e. projects delivered via CSV or PDF to users via email on a regular basis. **Non-Admin users can only see their&#x20;**_**running**_**, but not their&#x20;**_**expired**_**&#x20;schedules!**&#x20;

With the Component Manager, you (and whoever you share the Google Sheet with) can see all schedules, filter by owner, expired status, and more.

Simply run "Workspaces" -> "**Refresh Project Schedules**":

<figure><img src="../.gitbook/assets/image (172).png" alt=""><figcaption></figcaption></figure>

You can now add a filter to the tab and e.g. filter by the "expired" column. See a full list of the available columns here:

<figure><img src="../.gitbook/assets/image (186).png" alt=""><figcaption></figcaption></figure>

* **id:** Schedule ID
* **owner\_id, owner\_name, owner\_login:** owner (creator) of the schedule&#x20;
* **projectId:** scheduled workspace project
* **scheduledItemName:** Name of the scheduled item (=name of the Workspace)
* **description:** info text in the scheduled e-mail
* **rsid:** Main Report Suite ID associated with the scheduled project
* **tags:** Tags given to the schedule
* **tasks:** A JSON object containing further details, like the recipients of the schedule
* **modified:** last time the schedule was modified
* **rsLocalStartTime:** date in your Report Suite's timezone when the schedule started
* **rsLocalExpirationTime:**  date in your Report Suite's timezone when the schedule will expire or has expired&#x20;
* **triggerObject:** details on the sending frequency (e.g. daily at 4 PM)
* **expired:** TRUE if schedule has expired, otherwise FALSE
