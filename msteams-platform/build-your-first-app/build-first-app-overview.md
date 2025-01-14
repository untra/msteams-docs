---
title: Get started - Build your first app overview and prerequisites
author: heath-hamilton
description: Learn how to get started with Microsoft Teams app development and set up your environment.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
---
# Build your first Microsoft Teams app overview

In the **get started** lessons, you learn how to create basic Teams apps. Each tutorial walks through how to build a simple, real-world Teams app while introducing you to common tools, fundamental concepts, and more advanced features.

## What you'll learn

Here's an idea of what you'll know after going through the lessons.

> [!div class="checklist"]
  >
  > * **Get up and running quickly with the Teams Toolkit**: The Microsoft Teams Toolkit for Visual Studio Code takes care of creating your app project and scaffolding so you can have a running app in minutes.
  > * **Configure your app with App Studio**: Specify the capabilities and services your Teams app uses.
  > * **Scope your app's audience**: Build a Teams app for personal use, collaboration, or both.
> * **Get experience with Teams tools and SDKs**: Customize your app with help from the Teams JavaScript client SDK. For example, change your app's color scheme to match the Teams theme. Also, learn about common tools for creating and managing bots.
  > * **Expand on your app**: Throughout the lessons, you'll find related topics you're probably interested in (such as authentication and design guidelines).

## Teams app fundamentals

Before you begin the tutorials, you should know the following about building apps for Teams.

### Apps can have multiple capabilities and entry points

A Teams app is made up of one or more [platform capabilities](../concepts/capabilities-overview.md) (how people use the app) and [entry points](../concepts/extensibility-points.md) (where people use the app).

### Teams doesn't host your app

A Teams app includes the following important pieces:

* The logic, data storage, and API calls that power your app. These services are not hosted by Teams and must be accessible via HTTPS.
* The Teams client (web, desktop, or mobile) where people use your app.
* Your app ID, which lets you configure your app with App Studio.

## Get prerequisites

Verify you have the right account for building Teams apps and install some recommended development tools.

### Set up your development account

You need a Teams account that allows custom app sideloading. (Your account may already provide this.)

1. If you have a Teams account, verify if you can sideload apps in Teams:
    1. In the Teams client, select **Apps**.
    1. Look for an option to **Upload a custom app**.

    :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Illustration showing where in Teams you can upload a custom app.":::
    
    If you don't see the button, you don't have permission to upload custom apps in your org. You can get this feature by signing up for a free Microsoft 365 developer subscription.

<!-- markdownlint-disable MD033 -->
<details>

<summary><b>Get your free Microsoft 365 developer subscription</b></summary>

You can get a free Teams test account that allows app sideloading by joining the Microsoft 365 developer program. (The registration process takes approximately two minutes.)

1. Go to the [Microsoft 365 developer program](https://developer.microsoft.com/microsoft-365/dev-program).
1. Select **Join Now** and follow the onscreen instructions.
1. When you get to the welcome screen, select **Set up E5 subscription**.
1. Set up your administrator account. Once you finish, you should see a screen like this.
:::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Example of what you see after signing up for the Microsoft 365 developer program.":::
1. Log in to Teams using the administrator account you just set up.
1. Verify if you now have the **Upload a custom app** option.

</details>

> [!Note]
> If you still can't sideload apps, see [enable custom Teams apps and turn on custom app uploading](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).

### Install your development tools

You can build Teams apps with your preferred tools, but these lessons show how you can get started quickly with the Microsoft Teams Toolkit for Visual Studio Code.

Teams displays app content only through HTTPS connections. To debug certain types of apps locally, such as a bot, you'll learn how to use [ngrok to set up a secure tunnel](../concepts/build-and-test/debug.md#locally-hosted) between Teams and your app. (Production Teams apps are hosted in the cloud.)

1. Install [Node.js](https://nodejs.org/en/).
1. Install [ngrok](https://ngrok.com/download) if you plan to build a bot or messaging extension.
1. Install the latest version of [Visual Studio Code](https://code.visualstudio.com/download). (Earlier versions might not work with the toolkit.)
1. In Visual Studio Code, select **Extensions** :::image type="icon" source="../assets/icons/vs-code-extensions.png"::: on the left Activity Bar and install the **Microsoft Teams Toolkit**.

    :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Illustration showing where in Visual Studio Code you can install the Microsoft Teams Toolkit extension.":::

## About the tutorials

You can start with any of the Teams **get started** lessons. If you're not sure where to go first, follow our beginner friendly path and build a "Hello, World!" app.

:::image type="content" source="../assets/images/build-your-first-app/skill-tree-overview.png" alt-text="Skill tree showing learning paths for the Teams 'get started' lessons." border="false":::

## Next step

Once you set up your account and environment, you can start building.

### Beginner friendly tutorial

> [!div class="nextstepaction"]
> [Build a "Hello, World!" app](../build-your-first-app/build-and-run.md)

### Other tutorials

> [!div class="nextstepaction"]
> [Build a bot](../build-your-first-app/build-bot.md)
> [!div class="nextstepaction"]
> [Build a messaging extension](../build-your-first-app/build-messaging-extension.md)
