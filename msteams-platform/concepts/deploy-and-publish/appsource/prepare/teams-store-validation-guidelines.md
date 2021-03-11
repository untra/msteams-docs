---
title: Microsoft Teams store validation guidelines
description: Describes the guidelines every app submitted to the Teams store (AppSource) must follow.
author: heath-hamilton
ms.author: surbhigupta
ms.topic: reference
---
# Microsoft Teams store validation guidelines

Following these guidelines increases the likelihood your app will pass the Microsoft Teams store submission process. These Teams-specific guidelines complement the Microsoft [commercial marketplace certification policies](https://docs.microsoft.com/legal/marketplace/certification-policies) and are updated frequently to reflect new capabilities, user feedback, and business rule changes.

> [!TIP]
> Some guidelines may not be applicable to your app. For example, if your app doesn't include a bot, you can ignore bot-related guidelines.

## 1.0 Value proposition

### 1.1 App name

An app's name plays a critical role in how users discover it in the store. Remember the following about app names:

* The name must include terms relevant to your users.
* Names of core Teams features&#8212;such as **Chat**, **Contacts**, **Calendar**, **Calls**, **Files**, **Activity**, **Teams**, **Apps**, and **Help**&#8212;should not be included in your app name.
* Common nouns must be prefixed or suffixed with the developer's name (for example, **Contoso Tasks** rather than **Tasks**).
* It must not use **Teams** or other Microsoft product names that could falsely indicate co-branding or co-selling. (For more information about referencing Microsoft software, products, and services, see the [Microsoft Trademark and Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general)).
* If your app is part of an official partnership with Microsoft, the name of your app must come first (for example, **Contoso Connector for Microsoft Teams**).
* It must not copy the name of an app listed in the store or other offer in the commercial marketplace.
* It must not contain profane or derogatory terms. It also must not include racially or culturally insensitive language.

### 1.2 Suitable for workplace consumption

App content must be suitable for general workplace consumption and abide by all restrictions listed in the [commercial marketplace certification policies](https://docs.microsoft.com/legal/marketplace/certification-policies#10010-inappropriate-content). Content related to religion, politics, gambling, and prolonged entertainment is prohibited.

Your app must facilitate group collaboration, improve an individual's productivity, or both. Apps intended for team bonding and socializing must be collaborative and designed for multiple participants. These types of apps also should not require a substantial time investment or perceptively impact productivity.

### 1.3 Similar platforms and services

Apps must focus on the Teams experience and not include the names, icons, or imagery of other similar chat-based collaboration platforms or services unless the app provides specific interoperability.

### 1.4 Feature names

When referring to your app's features in buttons and other UI text, you must include your product name. For example, instead of **Start Meeting**, use **Start Contoso Meeting**.

## 2.0 Security

### 2.1 App permissions

Apps that request permissions during the Azure Active Directory (Azure AD) consent process must provide business justification for these requests.

### 2.2 Microsoft App Compliance Program

The [Microsoft 365 App Compliance Program](https://docs.microsoft.com/microsoft-365-app-certification/overview) is intended to help organizations assess and manage risk by evaluating security and compliance information about your app. As a Teams app developer, you must complete the following tiers of the program.

#### 2.2.1 Publisher Verification

You must complete [Publisher Verification](/azure/active-directory/develop/publisher-verification-overview), which helps admins and end users understand the authenticity of app developers integrating with the Microsoft identity platform. For more information, see how to [mark your app as publisher verified](/azure/active-directory/develop/mark-app-as-publisher-verified) and [troubleshoot publisher verification](/azure/active-directory/develop/troubleshoot-publisher-verification).

#### 2.2.2 Publisher Attestation

You must complete [Publisher Attestation](/microsoft-365-app-certification/docs/attestation), a process in which you share general, data handling, and security and compliance information to help potential customers make informed decisions about using your app.

### 2.3 Bots

For apps that use the Microsoft Azure Bot Service (bots and messaging extensions), you must follow all requirements as defined in the Microsoft [Online Services Terms](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46).

Bots must always ask permission to upload a file and display a confirmation message after the file uploads.

### 2.4 External domains

In most cases, you must not include domains outside of your organization's control (including wildcards) and tunneling services in the valid domains section of your app manifest. The following exceptions include:

* If your app uses the Azure Bot Service's OAuthCard, you must include `token.botframework.com` as a valid domain or the **Sign in** button won't work.
* If your app relies on SharePoint, you can include the associated root SharePoint site as a valid domain using the `{teamSiteDomain}` variable.

### 2.5 Authentication

For implementation details, see [authentication in Teams](~/concepts/authentication/authentication.md).

#### 2.5.1 External service experiences

Remember the following if your app authenticates users with an external service.

* **Sign in, sign out, and sign up experiences**:
  * Apps that depend on external accounts or services must provide clear and simple sign in, sign out, and sign up experiences.
  * When a user signs out, they must sign out only from the app and not the Teams client.
* **Content sharing**: Apps that require authentication with an external service to share content in channels must clearly state in help documentation (or similar resources) how to disconnect or unshare content if that feature is supported on the external service. This does not mean the ability to unshare content must be present in your Teams app.

#### 2.5.2 Government Community Cloud listings

To distribute your app to Government Community Cloud (GCC) users while avoiding duplicate listings in the Teams store, the authentication process must identify and route users to a GCC-specific or expected URL.

### 2.6 Sensitive content

Your app must not post sensitive data, such as credit card or financial payment instrument data. The app also must not display health, contact tracing, or other personally identifiable information (PII) to an audience not intended to view that content.

Warn users before your app downloads any files or executables (.exe) into the user's machine or environment.

### 2.7 Financial information

Apps must not ask users to make payments within the Teams interface. Financial instrument details must not be transmitted to users through a bot interface.

You may link to secure, external payment services only if you made the appropriate disclosure in your terms of use, privacy policy, or any profile page or website before the user agreed to use the app.

## 3.0 General functionality and performance

### 3.1 Launching external functionality

Apps must not take users out of Teams for core user scenarios. App content and interactions can occur within Teams capabilities, such as cards, task modules, and tabs. 

You should link users somewhere in Teams and not to an external site or app. For scenarios that require external functionality, your app must have explicit user permission to launch that functionality.

### 3.2 Compatibility

Apps must be fully functional on the following operating systems and browsers:

* Microsoft Windows 7 and later
* macOS 10.10 and later
* Microsoft Edge 12 and later
* Mozilla Firefox 47.0 and later
* Google Chrome 51.0 and later
* iOS 9.0 and later
* Android 4.4 and later

### 3.3 Response time

Teams apps must respond within a reasonable timeframe, which varies depending on the capability.

* Tabs must respond within three seconds or display a loading message or warning.
* Bots must respond to user commands within two seconds or display a typing indicator.
* Messaging extensions must respond to user commands within five seconds.
* Notifications must display within five seconds of the user action.

## 4.0 App package and store listing

App packages must be correctly formatted and include all required information and components.

### 4.1 App manifest

* The app manifest must conform to the [latest manifest schema](~/resources/schema/manifest-schema.md).
* If your app includes a bot or messaging extension, the manifest must be consistent with Bot Framework metadata, including bot name, logo, privacy policy link, and terms of service link.
* If your app uses Azure Active Directory (Azure AD) for authentication, include the Azure AD ID in the manifest. For more information, see the [manifest schema](~/resources/schema/manifest-schema.md#webapplicationinfo).

### 4.2 App icons

Icons are one of the main elements people see when browsing the store. Your icons should communicate your app's brand and purpose while also adhering to the following requirements:

* Your app package must include two PNG versions of your app icon: A color icon and an outline icon.
* The color version of your icon displays in most Teams scenarios and must be 192x192 pixels. Your icon symbol (96x96 pixels) can be any color or colors, but it must sit on a solid or fully transparent square background.
* The outline version of your icon displays when your app is in use and “hoisted” on the app bar on the left of Teams and when a user pins your app's messaging extension. It must be 32x32 pixels and can be white with a transparent background or transparent with a white background (no other colors are permitted). The icon should not have any extra padding around the symbol.
* Correctly sized and formatted icons must be specified in your app package. The icons must match what's submitted with the store listing metadata.

For more information, best practices, and examples see the Teams app [icon guidelines](~/concepts/build-and-test/apps-package.md#app-icons).

### 4.3 App descriptions

You must have a short and long description of your app. Include the same descriptions in your manifest and Partner Center must be the same.

Descriptions should not directly or through insinuation disparage another brand (Microsoft owned or otherwise). Make sure your description does not include claims that can't be substantiated (for example, "Guaranteed 200 percent increase in efficiency").

#### 4.3.1 Short description

A short description is a concise summary of your app that highlights its value proposition and is directed at your target audience. Keep the short description to one sentence.

**Do:**

* Put the most important information first.
* Include keywords that customers are likely to search for.

**Don't:**

* Repeat your app name.
* Use the word **app** in the name.

#### 4.3.2 Long description

The long description can provide an engaging narrative that highlights your app's value proposition, primary audience, and target industry. While this description can be as long as 4000 characters, most users will only read between 300-500 words.

**Do:**

* Clearly describe limitations, conditions, or exceptions to the functionality, features, and deliverables described in the listing and related materials before the customer installs your app. The Teams app capabilities you specify must relate to the core functions and description of your offer.
* Use [Markdown](https://support.office.com/article/use-markdown-formatting-in-teams-4d10bd65-55e2-4b2d-a1f3-2bebdcd2c772) to format your description.
* List features with bullet points so it's easier to scan the description.
* Use active voice and speak to users directly (for example, *You can ...*).
* Include a help or support link.
* Refer to **Microsoft 365** instead of **Office 365**.
* If you need to reference **Teams**, write the first reference as **Microsoft Teams**. Subsequent references can be shortened to **Teams**.
* Use the following language when describing how the app works with Teams (or Microsoft 365):
  * "... works with Microsoft Teams."
  * "... working with Microsoft Teams."
  * "... within Microsoft Teams."
  * "... for Microsoft Teams."

**Don't:**

* Exceed 500 words.
* Abbreviate **Microsoft** as **MS** or **MSFT**.
* Indicate the app is an offering from Microsoft, including using Microsoft slogans or taglines.
* Use copyrighted brand names you don't own.
* Include typos, grammatical errors, and unnecessary capitalizations (for example, **Users** instead of **users**).
* Contain links to AppSource.
* Use the following language unless you are a certified Microsoft partner:
  * "... integrated with Microsoft Teams"
  * "... integrates with ..."
  * "... built for ..."
  * "... built on ..."
  * "... runs on ..."
  * "... enabled by ..."
  * "... certified for ..."
  * "... developed for ..."
  * "... designed for ..."

### 4.4 Screenshots

Screenshots provide a prominent visual preview of your app to complement your app name, icon, and descriptions. Remember the following about screenshots:

* You can have up to five screenshots per listing.
* Supported file types include PNG, JPEG, and GIF.
* Dimensions should be 1366x768 pixels.
* Maximum size of 1,024 KB.

**Do:**

* Focus on your app's capabilities (for example, how people can communicate with your bot).
* Include content that accurately represents your app.
* Use text judiciously.
* Frame screenshots with a color that reflects your brand and include marketing content, similar to the [Freshdesk listing](https://appsource.microsoft.com/product/office/WA104381505?src=office&tab=Overview) example (dimension requirements apply to the whole image and not just the screenshot).

**Don't:**

* Show specific devices, such as phones or laptops.
* Display chrome or UI that isn't in your app.
* Capture any Teams or browser UI in your screenshots.
* Include mockups that inaccurately reflect your app's actual UI, such as showing your app in  a browser instead of a Teams tab.

### 4.5 Privacy policy

The privacy policy can be specific to your Teams app or an overall policy for all of your services.

* If you use a generic privacy policy template, you must reference **services**, **applications**, and **platforms** to include your Teams app and your website or service.
* Must include how you handle user data storage, retention, and deletion. You also must describe the security controls you use for data protection.
* Must include your contact information.
* Should not contain broken, beta, or staging URLs.
* Must not include links to AppSource.

### 4.6 Terms of use

Your terms of use should be specific and applicable to your offering.

### 4.7 Support links

An app's support URLs should not require authentication. For example. users should not have to log in to contact you.

### 4.8 Localization

App packages must include a file with language translations that display based on the Teams language setting. The file must conform to the [Teams localization schema](~/concepts/build-and-test/apps-localization.md).

## 5.0 Tabs

If your app includes a tab, make sure it adheres to these guidelines.

> [!TIP]
> For information on creating a high-quality experience, see the [tab design guidelines](~/tabs/design/tabs.md).

### 5.1 Setup

* Tab setup must not dead-end the new user. A way forward message should be provided to complete the workflow.
* Authentication should happen during tab setup and not after.
* Tabs must have a help tab with instructions on how to use and configure your app.

### 5.2 Views

* The sign-in screen area use must not use large logos or display an entire webpage.
* Content can be simplified by breaking it down across multiple tabs.
* Tabs should not have a duplicate header. Remove the logo from the iframe since the tab framework already displays the app icon and name.

### 5.3 Navigation

* Tabs must not have more than three levels of navigation.
* Tabs must not provide navigation that conflicts with the primary Teams navigation.
* The secondary and tertiary pages in a tab must be opened in a level two and level three view in the main tab area that is navigated via breadcrumbs or left nav. You can also include these components to aid tab navigation:
    * Back buttons
    * Page headers
    * Hamburger menus
* Tab should not have horizontal scroll.
* Deep links in tabs must not link to an external webpage but instead link somewhere within Teams (for example, task modules or other tabs).
* Tabs should not allow users to navigate outside Teams for the core app experience.

### 5.4 Usability

* Tabs must provide value beyond just hosting an existing website.
* Users must be able to undo their last action in the tab.
* Personal app tabs may aggregate content from team or group chat scoped instances of that app in a single view.
* Tabs must be responsive to Teams themes. When the Teams theme is changed, the theme within the app must also change to reflect that theme.
* Tabs must use Teams-styled components (adopting Teams fonts, type ramps, color palettes, grid system, motion, tone of voice, etc.) whenever possible.
* You must include a **Settings** tab.
* Tabs must use Teams interaction behaviors (in-page navigation, position and use of dialogs, information hierarchies, etc.) whenever possible.
* Tabs must use core Teams capabilities (bots for conversations, message extensions for search & share, deeplink, calling, meeting etc.) if applicable

## 6.0 Bots

If your app includes a bot, make sure it adheres to these guidelines.

> [!TIP]
> For information on creating a high-quality experience, see the [bot design guidelines](~/bots/design/bots.md).

### 6.1 Bot commands

* All commands that your bot supports must work correctly, including the "Hi", "Hello", and "Help" command.
* You should include supported bot commands in your app manifest to help users converse efficiently with your bot across all devices.
* Supported bot commands must be listed in the app manifest.
* Use command lists. Analyzing user input or predicting user intent is hard. Instead of letting users guess what your bot can do, provide a list of commands your bot understands.

### 6.2 Bot welcome messages

* Bots should almost always send first-run welcome messages. For the best experience, the message should include the value proposition of your bot, how to configure the bot, and briefly describe all supported bot commands. You can display the messaging using an Adaptive Card with buttons for better usability. For more information, see [how to trigger a bot welcome message](~/bots/how-to/conversations/send-proactive-messages.md).
* Channel bot welcome messages are optional during first run, especially if bot is available in personal scope performing similar actions. This bot must not send a personal message to all members of the team or channel as that will be considered as spamming. The welcome message should also mention the person who installed/added the bot to the channel.
* Notification-only bots must send a welcome message that includes a message conveying, "I am a notification-only bot and will not be able to reply to your chats".

### 6.3 Bot message spamming

Bots must not spam users by sending multiple messages in short succession.

* **Bot channel messages**: Don't spam users by creating separate posts. Create a single post with replies in the same thread.
* **Bot personal messages**: Don't send multiple messages in quick succession. Send one message with complete information. Avoid multi-turn conversations to complete a single workflow. Instead, consider using a form (or task module) to collect all inputs from a user at one time.
* **Welcome messages**: Repeating the same welcome message over regular intervals is not allowed and considered spamming. When a new member is added to a team, don't spam the other members with a welcome message that should be sent to the new member privately instead.

### 6.4 Bot notifications

Bot notifications must include content relevant for the scope you define for the bot (`team`, `groupchat`, or `personal`).

### 6.5 Bots and Adaptive Cards

Adaptive Cards are a common way to display bot messages and highly recommended. Your cards must be lightweight and include only 1-3 actions. If you need to display more content, consider using a task module or tab.

See the following resources for more information:

* [Designing Adaptive Cards](~/task-modules-and-cards/cards/design-effective-cards.md)
* [Cards reference](~/task-modules-and-cards/cards/cards-reference.md#types-of-cards)

## 7.0 Messaging extensions

If your app includes a messaging extension, make sure it adheres to these guidelines.

> [!TIP]
> For information on creating a high-quality experience, see the [messaging extension design guidelines](~/messaging-extensions/design/messaging-extension-design.md).

### 7.1 Action commands

Action-based messaging extensions should do the following:

* Allow users to trigger actions on a message without specifying intermediate steps, such as signing in.
* Pass the message context to the next work state.

### 7.2 Preview links (link unfurling)

Messaging extensions should preview recognized links in the Teams compose box. Do not add domains that are outside your control (either absolute URLs or wildcards). For example, `yourapp.onmicrosoft.com` is valid but `*.onmicrosoft.com` is not valid. Top-level domains also are prohibited (for example, `*.com` or `*.org`).

### 7.3 Search commands

* Search-based messaging extensions must provide text that helps users effectively search.
* `@mention` executables must be clear, easy to understand, and readable.

## 8.0 Task modules

A task module must include an icon and the short name of the app it's associated with.

> [!TIP]
> For information on creating a high-quality experience, see the [task module design guidelines](~/task-modules-and-cards/task-modules/design-teams-task-modules.md).

## 9.0 Meeting extensions

If your app includes a meeting extension, make sure it adheres to these guidelines.

> [!TIP]
> For information on creating a high-quality experience, see the [meeting extension design guidelines](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md).

### 9.1 Pre- and post-meeting experience

* Pre- and post-meeting screens must adhere to general [tab design guidelines](~/tabs/design/tabs.md).
* Tabs must not have horizontal scrolling.
* Tabs should have an organized layout when displaying multiple items (for instance, more than 10 polls or surveys). [See an example layout](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#after-a-meeting).
* Your app must notify users when the results of a survey or poll are exported by stating, "Results successfully downloaded".

### 9.2 In-meeting experience

* Apps must [only use a dark theme](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md#theming) during meetings.
* A tooltip should display the app name when hovering over the app icon during meetings.
* Messaging extensions must function the same during meetings as they do outside meetings.

### 9.3 In-meeting tabs

* Must be responsive and adapt within the provided space. Make sure to maintain padding and component sizes.
* Must have a back button if there is more than one layer of navigation.
* Must not include more than one dismiss or close button. This may confuse users since there's already a built-in header button in the header to dismiss the tab.
* Must not have horizontal scrolling.

### 9.4 In-meeting dialogs

* Should be used sparingly and for scenarios that are light and task-oriented.
* Must display content in a single column and not have multiple navigation levels.
* Must not use task modules.
* Must align with the center of the meeting stage.
* Should be dismissed once a user selects a button or performs an action.

## 10.0 Notifications

If your app uses the [activity feed APIs provided by Microsoft Graph](https://docs.microsoft.com/graph/teams-send-activityfeednotifications), make sure it adheres to these guidelines.

### 10.1 General

* All the notification triggers specified in your app manifest should get a notification in the app.
* The notifications must be localized as per the supported languages declared in the app manifest.
* Notifications must display within five seconds of the user action.

### 10.2 Avatars

* The notification avatar should match your app's color icon.
* Notifications triggered by an app user should include the user's avatar.

### 10.3 Spamming

* Apps must not send more than 10 notifications per minute to a user.
* Bots and the activity feed should not trigger duplicate notifications.
* Notifications must provide some value to users and not be used for trivial or irrelevant events.

### 10.4 Navigation and layout

* Notifications must adhere to the Teams activity feed layout and experience.
* When selecting a notification, the user must be directed to relevant content within Teams and not taken out of the Teams experience.

## 11.0 In-app purchases

Apps running in the iOS or Android version of Teams must adhere to the following guidelines:

* Apps must not include in-app purchases, trial offers, or UI that aims to upsell to paid versions or links to online stores where users can purchase or acquire other content, apps, or add-ins.
* If your app requires an account, users must be able to do so with no charge. The use of the term **free** or **free account** is prohibited.
* You may determine whether an account is active indefinitely or for a limited time, but if the account expires, no UI, text, or links indicating the need to pay may be shown.
* Your app's privacy policy and terms of use pages must be free of any commerce-related UI or links.

## 12.0 Advertising

Apps must not display advertising, including dynamic ads, banner ads, and ads in messages.

## Next step

> [!div class="nextstepaction"]
> [Prepare your store submission](~/concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)