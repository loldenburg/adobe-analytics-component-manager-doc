---
description: >-
  How to migrate from the old version of the Component Manager to the Google
  Sheets Add-on in 3 minutes.
---

# Migrate to the Google Sheets Add-on

## What changes with the Add-on?

Since January 2023, the Adobe Analytics Component Manager for Google Sheets is available as an [official Google Sheets Add-on in the Google Workspace Marketplace](https://workspace.google.com/marketplace/app/aa_component_manager/561445625333).&#x20;

This has a lot of benefits:

* The installation is a lot **easier and faster** and there are no more scary "unsafe" messages etc.
* You **automatically benefit from updates** - no need anymore to manually update the Component Manager to a new version
* The **app is faster** as we don't need to do things like version checks with data from a separate spreadsheet every time a function runs
* **Security:** your Google Workspace Admins can whitelist this particular app instead of having to give you unrestricted access to any unapproved Apps Script apps

## Do I need to migrate?

The old version will keep working until **Februar 28 2023**. We will not fix bugs or issues there. Migration is easy. Simply follow the steps below:

## How to migrate

Migration requires 2 steps:

### 1. Install the [official Google Sheets Add-on in the Google Workspace Marketplace](https://workspace.google.com/marketplace/app/aa_component_manager/561445625333).&#x20;

### 2. Remove the Apps Script code and Library connection in each of your Component Manager sheets:

I. Go to Extensions -> Apps Script.

<figure><img src="../.gitbook/assets/image (173).png" alt=""><figcaption></figcaption></figure>

II. Delete all code in the Code.gs panel and click the "Save" icon. If you cannot edit or save, make sure you are viewing the page with a Google account that has Editor rights.

<figure><img src="../.gitbook/assets/image (195).png" alt=""><figcaption></figcaption></figure>

III. Under "**Libraries**", click on the three dots next to "**libComponentEditor**", and then "**Remove**".

![](<../.gitbook/assets/image (178).png>)

IV. Reload your Google Sheet. Done.

You will now no longer see the "AA Component Manager" menu on top. Instead, all the Component Manager functions are now under **Extensions -> AA Component Manager:**&#x20;

<figure><img src="../.gitbook/assets/image (207).png" alt=""><figcaption></figcaption></figure>

