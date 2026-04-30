---
description: >-
  The "account_usage" tab gives you transparency over the people you should care
  about most: your organization's Adobe Analytics users!
---

# Account Usage

* How popular is Adobe Analytics at my organization and how has this developed over time? For example, are logins and workspace views trending up or down?
* Who are my power users?
* Which users are at risk (less active recently compared to earlier)?

For questions like these, there is the account usage tab.

To **update the tab**, simply go to **"Adobe Component Manager -> Other -> Get Account Usage Stats"** and enjoy the insights.

![Shed light on the activity of your organization's Adobe Analytics users](<../.gitbook/assets/image (34).png>)

Updating the tab for the first time can take a while, usually between 5 and 45 minutes, depending on how much is going on in your Adobe Analytics account.

To see email addresses or login names instead of hashes, uncheck the "**no personal data**" **checkbox in the "config" tab.**

### **Frequent Questions**

#### Are views from technical users (e.g. via API) counted?

No. Account Usage Stats and Workspace Stats filter out all operations by technical users (via the "\*@techacct.adobe.com" email address).

#### Does the moment a Scheduled Project is generated count as a Workspace view?

Adobe Analytics does generate a project\_view event (= a Workspace view) for the respective project and the user that created the schedule at the time of dispatch. It can't be distinguished from a regular project\_view. The opinions on this differ: Some people see this as beneficial - this way, getting a Workspace PDF to your mailbox can be seen as a way to "view" a Workspace.
