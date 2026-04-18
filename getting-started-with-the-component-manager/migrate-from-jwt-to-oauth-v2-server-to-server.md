---
description: >-
  How to migrate your Adobe Analytics API credentials for the Component Manager
  from JWT to OAuth.
---

# Migrate from JWT to OAuth V2 (Server-to-Server)

## JWT is going out of business, and you need to migrate

JWT API Credentials will no longer be supported after Januar 27 2025. Starting June 3, you can no longer create new JWT credentials, only OAuth V2 (Server-to-Server). See [Adobe's deprecation timeline and more details here](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#deprecation-timelines).&#x20;

The Component Manager will support JWT credentials as long as Adobe does (Jan 27, 2025), so you don't need to change to OAuth right away.&#x20;

If your Component Manager account previously had JWT credentials, you need to eventually migrate them to OAuth V2. This guide shows you how to do that:

1. Go to [developer.adobe.com -> Projects](https://developer.adobe.com/console/projects/) and open your Component Manager Project
2. Click on **"Go to credential"** in the blue popup (or click on "Service Account (JWT)" below).&#x20;

<figure><img src="../.gitbook/assets/image (129).png" alt=""><figcaption></figcaption></figure>

3. Click on "Add new credential":

<figure><img src="../.gitbook/assets/image (130).png" alt=""><figcaption></figcaption></figure>

4. After confirming, you should see "Step completed" in green. Click on "OAuth Server-to-Server" on the left side.

<figure><img src="../.gitbook/assets/image (133).png" alt=""><figcaption></figcaption></figure>

5. Scroll down to review your new OAuth V2 credential. Note that Client ID, Secret, Tech ID, Tech E-Mail and Org ID stay the same as with JWT! The only new thing are the **Scopes** and the Credential Name. For our migration, we only need the **Scopes.**

<figure><img src="../.gitbook/assets/image (136).png" alt=""><figcaption></figcaption></figure>

6. Now go to your Component Manager Google Sheet and click on Extensions -> AA Component Manger -> Setup

<figure><img src="../.gitbook/assets/image (137).png" alt=""><figcaption></figcaption></figure>

7. The first question is now for the Scopes. Copy the Scopes from the Credential Details page shown under point 5 above and paste them:

<figure><img src="../.gitbook/assets/image (254).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
If you do not provide Scopes, the Component Manager assumes you are still on JWT and will ask for JWT-related credentials like Tech ID and Private Key.
{% endhint %}

8. You can **then click OK for all the next steps** because neither your Client ID, Secret nor Org ID should have changed. You won't be asked for the **Tech ID and Private Key**, because they are **not needed for OAuth V2.**

<figure><img src="../.gitbook/assets/image (138).png" alt=""><figcaption></figcaption></figure>

9. With JWT, you needed the credentials plus the private key to do anything. For OAuth V2, Scopes, Client ID, Org ID and the Secret are enough. That is why we no longer store the **Client Secret** in the sheet's "config" tab, as that would give anyone with access to the sheet all the credentials to query your Adobe Analytics API:

<figure><img src="../.gitbook/assets/image (255).png" alt=""><figcaption></figcaption></figure>

After going through the rest of the setup as usual, you should finally receive a success message on the bottom right when everything has been completed.

You should now also see your scopes at the bottom of the "Other Settings" columns:

<figure><img src="../.gitbook/assets/image (256).png" alt=""><figcaption></figcaption></figure>

10. We recommend you go to the Developer Project page now and delete the JWT credentials to avoid confusion later (and all those reminder e-mails from Adobe 😆).

<figure><img src="../.gitbook/assets/image (258).png" alt=""><figcaption></figcaption></figure>

## Struggling? Found a bug?

Please don't hesitate to reach out to us [via our Contact options](https://docs.datacroft.de/contact) or via component-manager\[at]datacroft.de.
