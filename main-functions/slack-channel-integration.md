---
description: >-
  Shows how to configure the Slack integration with the Datacroft Component
  Manager.
---

# Slack Channel Integration

To configure your Slack Channel to receive Component Manager messages, e.g. for the [Health Report Summary](variable-health-report.md#report-summary), follow these steps.&#x20;

{% hint style="warning" %}
Slack changes their layout occasionally, so the screenshots may not be up-to-date here.&#x20;
{% endhint %}

You need the necessary rights to do these steps. If you cannot see the options shown, talk to your Slack Administrator.

You can use an existing channel or create a new one. You can call it anything you like, e.g. "analytics-alerts".

<figure><img src="../.gitbook/assets/image (157).png" alt=""><figcaption></figcaption></figure>

Now, click on the caret next to the channel name to get to the channel settings. Then "Integrations", then "Add an App".

<figure><img src="../.gitbook/assets/image (223).png" alt=""><figcaption></figcaption></figure>

Now search for "**incoming-webhook**" and click "Install". You should be taken to the configuration page. Otherwise, click "Configuration".

On the Configuration page, select your channel (e.g. "analytics-alerts") and click "Add Incoming WebHooks integration":

<figure><img src="../.gitbook/assets/image (224).png" alt=""><figcaption></figcaption></figure>

You are now taken to a page where you can see your Webhook URL. Copy the URL to the clipboard:

<figure><img src="../.gitbook/assets/image (229).png" alt=""><figcaption></figcaption></figure>

Now go to the **config** tab of your Component Manager and paste the URL into the first empty row in column I. In column G, enter `slack_url`, in column H anything you like (e.g. "Slack URL"):

<figure><img src="../.gitbook/assets/image (228).png" alt=""><figcaption></figcaption></figure>

That's it. You will now receive Slack messages from the Component Manager. Currently, only the [Variable Health Report](variable-health-report.md) supports Slack notifications.&#x20;

When we add more, we will make them configurable so you only get those that you want. We will also never use your Slack integration to send you ads or anything not related to the particular feature.
