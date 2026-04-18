---
description: >-
  How to get started with the Adobe Analytics Component Manager for Google
  Sheets. Explains how to generate the JWT API 2.0 Token and more.
---

# 🏁 Getting started with the Component Manager

You can set the Component Manager up all by yourself with the steps below. Alternatively, we gladly guide you through the setup step-by-step. Just get in touch with us through our [contact form](https://datacroft.de/en/component-manager/) or send us an e-mail to [contact\[at\]datacroft.de](mailto:contact@datacroft.de).

{% hint style="info" %}
Not new, but simply want to know how to [**migrate an existing Component Manager from JWT to OAuth V2**](migrate-from-jwt-to-oauth-v2-server-to-server.md)?
{% endhint %}

## 1. Install the Add-On

You can install the Component Manager Add-on either

a) [**directly from the Google Workspace Marketplace**](https://workspace.google.com/marketplace/app/aa_component_manager/561445625333)**, or**

b) via the Extensions menu in Google Sheets: In Google Sheets, click on **Extensions -> Add-ons -> Get add-ons.**&#x20;

<figure><img src="../.gitbook/assets/image (171).png" alt=""><figcaption></figcaption></figure>

Then search for "AA Component Manager" and install.

<figure><img src="../.gitbook/assets/image (202).png" alt=""><figcaption></figcaption></figure>

If you have trouble installing, try to make sure you are logged in with ONE Google account (only for installing - you can later log in with other accounts again) or try in another browser.&#x20;

After installing, follow the steps below:

## 2. Set up your Component Manager

To start, **create a new Google Sheet and give it a useful name**, e.g. "Component Manager My Company".&#x20;

Set **File -> Settings -> Locale** to **"United States"** so your Google Sheet understands decimal numbers the same way the Component Manager does:&#x20;

<figure><img src="../.gitbook/assets/image (236).png" alt=""><figcaption></figcaption></figure>

Then follow the video or text guide below:

### Step-by-Step-Guide (OAuth V2)

You need to have **System Administrator** rights for your Adobe Experience Cloud. The process takes about 15 minutes.

### 1. Import the Component Manager Sheet Template

Click on Extensions -> AA Component Manager -> Setup:

<figure><img src="../.gitbook/assets/image (201).png" alt=""><figcaption></figcaption></figure>

This will import all the necessary tabs. So wait a while until you see the "Finished (Re)creating sheet" message below.&#x20;

### 2. View Terms & Conditions

After that, you should see an overlay to view the terms & conditions. With the next steps in the setup, you will also create a Component Manager account. This is why you first need to accept the terms & conditions when you run the setup for the first time.&#x20;

You can now close the overlay.

<figure><img src="../.gitbook/assets/image (208).png" alt=""><figcaption></figcaption></figure>

We will continue with the Component Manager setup later. Now let's first set up the Adobe Analytics credentials. &#x20;

### 3. Create an OAuth V2 API Credential & Adobe Analytics Admin Account

**Option a) Let us do it.** Simply give your contact from Datacroft (or write to **component-manager@datacroft.de**) Experience Cloud Admin rights for a day or arrange a 15-minute call where we walk you through everything.&#x20;

**Option b) Do it yourself:**

1\. Under [https://console.adobe.io/](https://console.adobe.io/), log in with a user who has Developer rights (can be given via Adobe Admin Console -> Users -> Developers) for Adobe Analytics and is an Adobe Analytics Admin.

2\. Create a "project" (ideally called "Component Manager API Access").

![](<../.gitbook/assets/image (24).png>)

3\. Click on "**Add API**", select "Adobe Analytics" -> Next -> select "**OAuth Server-to-Server**" -> Next&#x20;

4\. Select any Product Profile (technically, it does not matter which profile you choose because we will make this user an Admin soon, but choose one that makes the most sense for your organization), then **"Save configured API".**

5\. On the following page, click on **"OAuth Server-to-Server":**

<figure><img src="../.gitbook/assets/image (237).png" alt=""><figcaption></figcaption></figure>

6\. There, you should see the following **credentials.**&#x20;

<figure><img src="../.gitbook/assets/image (238).png" alt=""><figcaption></figcaption></figure>

7\. Now copy the **Technical Account&#x20;**_**EMAIL**_ (_not the Technical Account ID!_).&#x20;

<figure><img src="../.gitbook/assets/image (241).png" alt=""><figcaption></figcaption></figure>

**8. Log into the Adobe** [**Admin Console**](https://adminconsole.adobe.com/) and click on **Products:**&#x20;

<figure><img src="../.gitbook/assets/image (242).png" alt=""><figcaption></figcaption></figure>

**9. Go to Analytics**:

<figure><img src="../.gitbook/assets/image (244).png" alt=""><figcaption></figcaption></figure>

**10. Click on the "Admins"** tab and then "**Add Admin**".

<figure><img src="../.gitbook/assets/image (245).png" alt=""><figcaption></figcaption></figure>

12\. Paste the Technical Account Email you copied previously, then click the little arrow to the right and select the entry that appears below.&#x20;

<figure><img src="../.gitbook/assets/image (247).png" alt=""><figcaption></figcaption></figure>

In the preview, you should now see "Enterprise ID" and an "SSO User Name":

<figure><img src="../.gitbook/assets/image (248).png" alt=""><figcaption></figcaption></figure>

Click Save. Your new Admin should show as "Technical Account" in the list.

### 4. Validate Component Manager - Adobe Analytics connection

You are now ready to check if the Component Manager can connect to the Adobe Analytics API.&#x20;

1\. Go to the **config** tab, then, select **Extensions -> AA Component Manager -> Setup** from the main menu again to finish the setup. You can also run this anytime again to update the API credentials.

<figure><img src="../.gitbook/assets/image (182).png" alt=""><figcaption></figcaption></figure>

3\. Confirm the terms & conditions.

4\. You are now asked to add each of the OAuth V2 Credentials that are required for the connection, in the following order:

* Scopes
* Client ID
* Secret (click on "Retrieve Secret" to get it)
* Org ID&#x20;

Simply copy-paste them from your Adobe Developer project OAuth Credentials page.

<figure><img src="../.gitbook/assets/image (249).png" alt=""><figcaption></figcaption></figure>



Example:

<figure><img src="../.gitbook/assets/image (250).png" alt=""><figcaption></figcaption></figure>

5\. Decide whether the Component Manager shall import the names and email addresses of your organization's Adobe Analytics users (see [more here](../what-data-is-processed-and-stored-where.md#what-adobe-analytics-data-does-the-component-manager-use)).

6\. Confirm or change the **Base Report Suite ID** (see [below](./#id-5.-determine-the-base-report-suite-id)). For now, you can leave this blank or simply enter your main Report Suite ID.

7\. A "Thank you, we're setting up your account" message will appear. Check the config tab's columns G-I for the field "**setup\_status**". After 20-30 seconds, it should show "success" as well as some rows informing you of the duration of your contract. You should then also see a "Setup result" success message.

<figure><img src="../.gitbook/assets/image (251).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (252).png" alt=""><figcaption></figcaption></figure>

**Well done 👍**! Your Component Account is created and the Adobe Analytics connection works!

{% hint style="info" %}
After creating a new API User and linking it to an Admin account in Adobe Analytics, it can take a couple of minutes until the user _can_ actually use her Admin rights. So if the Component Manager tells you that your user does not have Admin rights, try again after a couple of minutes.
{% endhint %}

### **5. Determine the Base Report Suite ID**&#x20;

For some features to work, you need to set the Base Report Suite ID. Simply enter your main Report Suite ID into the config tab next to "base\_rsid":

<figure><img src="../.gitbook/assets/image (253).png" alt=""><figcaption></figcaption></figure>

You can get all Report Suite IDs directly in the Component Manager by running "AA Component Manager" -> "Report Suites" -> "Refresh Report Suites". Or you can find them under Admin -> Report Suites:

![](<../.gitbook/assets/image (111).png>)

#### **What is the Base Report Suite ID?**

Any Component Manager Google Sheet will always show _all Segments, Calculated Metrics and Date Ranges of your **entire** Adobe Analytics account,_ as these component types are not Report-Suite-specific. E.g., a segment you created in Report Suite A can be used in any other Report Suite.

However, _dimensions_ (eVars/props & classifications) and _metrics_ (Success Events) are Report-Suite-specifc. For example, eVar2 can mean something different in another Report Suite or it may not even be activated there. Similarly, _Virtual Report Suites_ are built on top of a "Base Report Suite" (officially "Parent Report Suite").

Thus, the "**Base Report Suite ID"** tells the Component Manager from which Report Suite it shall import dimensions, metrics and Virtual Report Suites.

In other words, the Base Report Suite ID is the Report Suite ID from which...

* eVars, props and Success Events are pulled in (segments, calculated metrics and date ranges are report-suite-independent)
* Virtual Report Suites will be shown: the VRSs that have the Main Report Suite as their "parent suite"

You can change this ID at any time in the **config** tab or create a second sheet with another Base Report Suite ID.

### 6. Optional: Set up Virtual Report Suite integration

You can also do this later, but to enable Virtual Report Suite functionalities, follow the [**steps here**](../main-functions/configuring-virtual-report-suites.md).

### 7. Create the full sheet **with all tabs and populate with data**

### 8. Populate the sheet with data from Adobe Analytics

After you have all tabs (e.g. "comp\_editor" etc.), you can start populating the sheet with data. You can take a shortcut by running **"Other -> Populate all tabs"**:&#x20;

<figure><img src="../.gitbook/assets/image (180).png" alt=""><figcaption></figcaption></figure>

After starting "Populate all Tabs", take a break and get a coffee, because the Component Manager should not be disturbed until it has finished the last tab to fill, which is the [Component Usage](../main-functions/the-component-usage-tab.md#summary) tab. Filling the Component Usage tab for the first time can take 15 minutes to an hour, but you can start working in the other tabs once the Component Usage tab update has started. You will know that it has started because you will be moved to that tab and you will see this message popping up on the bottom right:

![](<../.gitbook/assets/image (20).png>)

{% hint style="info" %}
"Populate all tabs" actually does not populate "all" tabs, but only those that do not require any up-front configuration (like "Compare Report Suites").
{% endhint %}

**Now enjoy the Component Manager! You have now officially become a hyper-efficient Adobe Analytics Admin!**

### Outdated: Step-by-Step-Guide Video (JWT)

**Attention: The video below explains how to set up the API credentials with the deprecated JWT method! We strongly recommend following the&#x20;**_<mark style="color:red;">**OAuth V2 guide above!**</mark>_ We will provide a new video for OAuth V2 soon!

{% embed url="https://youtu.be/MQCS2lM6c6U" %}
Step-by-step guide on how to set up the Component Manager for your organization
{% endembed %}
