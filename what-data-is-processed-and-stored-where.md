---
description: A Privacy Policy, written for humans
---

# Data Protection - what data is used and where is it stored?

## Privacy Policy regarding the Adobe Analytics data accessed and stored

### How does the Component Manager process data?

The Component Manager uses an API 2.0 JWT Token to pull component meta data (no report or individual user data) from Adobe Analytics, processes this data via various scripts hosted in a Google Cloud Platform (GCP) project in the European Union and finally writes the data to a Google Sheet. The Google Sheet can be owned by your organization if you want to.

### What Adobe Analytics data does the Component Manager use?

The Component Manager **never accesses Adobe Analytics report data**, so the data e.g. of your website visitors is untouched.

The Component Manager **accesses components meta data**, i.e. data on segments, calculated metrics, date ranges, dimensions, metrics, "Virtual" and regular Report Suites as well as Workspaces. "Meta data" refers to data like the name or description of a component, when it was created or in which Workspaces it is used. If you use the Account Usage Stats feature, the Component Manager will furthermore gather usage log data from Adobe Analytics (logins, workspace views of your organization's Analytics users).

### **Does the Component Manager store personal data (PII)?**

By default, the Component Manager does not store any personal data.&#x20;

However, the Component Manager is much more useful if it can display the names and email addresses of the owners of a component (e.g. the employees of your company who own certain workspaces) so you can e.g. inform these users about any changes you are doing to their components or filter out components of people who have left your company.

As this is personal data, you can sign an additional Data Processing Agreement when you sign a premium contract. The necessity of the additional data processing agreement depends on the laws of your region and is e.g. required in GDPR regions.

You can then deactivate the `no_personal_data` checkbox in the "config" tab:&#x20;

* if **active** (default), the "owner" and "shared with" columns of all tabs will simply show "pii disabled". The account usage tab will show salted hashes instead of email addresses for the user activity visualizations
* if **inactive,** the "owner" and "shared with" columns of all tabs will show their normal values, e.g. names of Adobe Analytics account users.

![If this box is unchecked, ...](<.gitbook/assets/image (33).png>)

![... instead of "pii disabled", you will see the names of your org's AA users](<.gitbook/assets/image (113).png>)

### **Where is which type of data stored?**

#### **Personal Data**&#x20;

If the `no_personal_data` checkbox mentioned above is unchecked, the Component Manager writes the names and (if Adobe IDs) email addresses into your Google Sheets. Personal data is **not stored anywhere else**, also not in logs or on our servers.

**API Credentials**

The credentials used for the Adobe Analytics API connection are stored safely and in an encrypted way using Google Cloud Platform's Secret Manager, an industry standard for security. You can furthermore simply disable the API Connection via the Adobe Developer Console at any time.

**Other non-sensitive data**

Some of the data in the Google Sheet, but no personal data, is stored in Google Cloud Platform's "Cloud Storage" as well as Google Cloud Platform's "Firestore" document database, both located in the European Union. This is done ...

* to make queries faster (e.g. to only query the delta between the last and the current "component usage" run makes the second and ensuing queries up to 95% faster, saves a lot of processing power)
* to track usage stats (e.g. how often which function is used and how long it runs) for performance and product optimization
* to generate parts of the "update logs" in the `update_log` tab (e.g. a list of all deleted Workspaces) to document changes.

#### Data in the Google Sheet

By default, all data in Google Sheets is stored [in Google's world-class data centers in an encrypted manner](https://support.google.com/docs/answer/10381817?hl=en), so this also applies to the Component Manager, which is basically a Google Sheets enhancement.

## Privacy Policy regarding the Google Sheets Add-on

If you install the Component Manager as a Google Sheets Add-on, the following applies regarding personally identifiable information from **your Google account**:

Upon first use of the Component Manager, we (Datacroft) ask you to accept the terms and conditions and this privacy policy. To remember who has accepted and when, we access and store your Google account's email address in the particular Google Sheet.&#x20;

To use the Component Manager, you need to share your Google Sheet with "edit" access to the Google Cloud Platform Service Account e-mail address that is mentioned in the ["getting started" guide](getting-started-with-the-component-manager/). When you do this, Datacroft gets programmatic read and write access to all data in this Google Sheet. This is required because the service cannot be provided otherwise.&#x20;

When you run the Component Manager Setup, we also store your Google account's e-mail address with the date when you agreed to the terms & conditions in our database in an encrypted form. This is required to prevent abuse and to have a legally binding proof of your agreement to the terms & conditions.&#x20;

### Google Privacy Policy

See [https://policies.google.com/privacy](https://policies.google.com/privacy) on how Google handles your data when using Google Sheets.

## End of Service

If you no longer wish to use the Component Manager, simply delete your Component Manager Google Sheet(s).

## Data access and deletion requests

You can at any time request us to send you all data stored about your person by writing to component-manager\[at]datacroft.de.

All account-related data is always deleted automatically after 6 months. You can at any time have all your personal and account-related data be deleted by writing to component-manager\[at]datacroft.de.

## Changes <a href="#h.f4pqvof1u1ec" id="h.f4pqvof1u1ec"></a>

Our Privacy Policy may change from time to time. We will not reduce your rights under this Privacy Policy without your explicit consent. We will post any privacy policy changes on this page and, if the changes are significant, we will provide a more prominent notice

## Last modified

March 10, 2025

