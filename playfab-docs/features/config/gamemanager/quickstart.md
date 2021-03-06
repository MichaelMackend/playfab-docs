---
title: Game Manager quickstart
author: v-thopra
description: Provides an overview of the features in the PlayFab Game Manager.
ms.author: v-thopra
ms.date: 10/26/2018
ms.topic: article
ms.prod: playfab
keywords: playfab, config, game manager
ms.localizationpriority: medium
---

# Game Manager quickstart

This quickstart familiarizes you with the high-level aspects of the Game Manager. For more detailed information, select your specific topic of interest in the PlayFab documentation. By now, you should have created your PlayFab account, logged in, and viewed the Game Manager for your title, even if it's an empty title for now.

The following provides more detail on each Game Manager area. Each time you perform an **API** call or task, view the results in the Game Manager in the appropriate area for that task.

## Game Manager sections

Now that you have an account, select a title (either the one we created or one of your own) to follow along. Within each title, the scope of a new Game Manager is distributed across the following major sections:

1. **Dashboard** - An overview of the performance of your title.
2. **Players** - Settings and data pertaining to your individual players, including player segmentation.
3. **Economy** - Settings and data pertaining to virtual items, stores, currencies and loot distribution. Also stores and coupons.
4. **Leaderboards** - Configure leaderboard settings, and view current rankings.
5. **Multiplayer** - Configure server hosting, and view match records.
6. **Content** - Manage content for your game, including news, remote configuration, and files.
7. **Automation** - Server-side logic for your game, including scriptings, rules, and tasks. Trigger actions based on events from your title.
8. **Analytics** - View reports and event data for your game, and configure how data is routed to other systems.
9. **Add-ons** - The control center for managing partner integrations.
10. **Settings** - Settings and data pertaining to the entire title.
11. **Admin** - Billing and audit history.

### 1. Settings

The **Credentials** tab provides basic information that you will use to configure your **SDK**.

![Game Manager - Settings - Credentials Tab](media/tutorials/game-manager-settings-credentials-tab.png)

Never share your PlayFab **API** secret key with anyone; doing so may jeopardize your title's security.

- **Game Title ID**: The unique identifier for your title in the PlayFab system.
- **PlayFab API Endpoint**: The unique base **URI** for your title. **API** calls to this endpoint are tracked in your title's reports.
- **PlayFab API Secret Key**: The unique identifier for your game when making Admin and server **API** calls. This key should only be shared with trusted members of your development team, since it enables **API** calls that can affect game data and player accounts.
- **Publisher ID**: The unique identifier for your studio.

### 2. Dashboard

The **Dashboard** shows your game’s basic statistics and Key Performance Indicators (KPIs). In the top left, you will find filter controls that limit the information displayed:

- **4h**: This will load data generated within the last 4 hours.
- **24h**: This will load data generated within the last 24 hours.
- **3d**: This will load data generated within the last 3 days.
- **7d**: This will load data generated within the last 7 days.
- **mtd**: This will load data generated within the current month.

You can see data for previous months in the [Reports Section](#9-reports).

> [!NOTE]
> In Game Manager, all times are displayed in local time.

![Game Manager - Dashboard](media/tutorials/game-manager-dashboard.png)

Monitor your title's KPIs and watch your **PlayStream** events in real time.

The dashboard has six sections. Left to right, top to bottom they are the following.

1. **LOGIN**: The number of logins recorded for the selected time span.
2. **INSTALL**: The number of accounts created (players logging in for the very first time) for the selected time span.
3. **REVENUE**: The USD value of real money transactions processed for the selected time span.
4. **MONTH OVERVIEW**: Useful KPIs pulled from the month-to-date data
    - **Revenue**: The USD value of real money transactions processed.
    - **DAU (Daily Active Users)**: The average number of unique players logging in per day.
    - **MAU (Monthly Active Users)**: the average number of unique players logging in per month.
5. **PLAYSTREAM DEBUGGER**: This will display title events as they are generated in real time.
6. **VIRTUAL CURRENCY TRANSACTIONS**: The number of virtual currency transactions recorded for the selected time span.

[Back to Game Manager Sections](#game-manager-sections)

### 3. PlayStream

This section houses the control panel for everything that is **PlayStream**. Here you will find a graph of the **PlayStream** activity (filtered for the selected time span). The stream debugger (like in other sections) displays title events as they are generated in real time.

![Game Manager - PlayStream](media/tutorials/game-manager-playstream.png)

Use the sampling controls to gather more or less events per second.

**PlayStream** is our latest and greatest addition to the PlayFab platform. More information will be coming soon on what actions you can do with **PlayStream**.

[Back to Game Manager Sections](#game-manager-sections)

### 4. Players

The **Players** tab presents you with a sorted list by most recent login. Selecting any of the records will take you to that player's overview. Using the search box you can easily search for players by **ID**, **Username**, **Display Name**, or **Email**.

![Game Manager - Players Tab](media/tutorials/game-manager-players-tab.png)

#### Player overview

This detailed screen provides a wealth of insight into the players activity. The **Overview** sub-menu contains many links to other **Players**-centric information, as shown below.

![Game Manager - Player - Overview](media/tutorials/game-manager-player-overview.png)

Tools your team can use to remedy defrauded players and identify potential abusers.

- **Overview**- View basic details and linked account status.
- **PlayStream**- View player generated events.
- **Logins**- View player login history.
- **Segments**- View which segments a player has entered.
- **Statistics**- View and edit player statistics.
- **Data**- View and edit player data records.
- **Inventory**- View, grant, and revoke **ItemInstances**.
- **Purchases**- View a player's real money purchase history.
- **Virtual Currency**- View and edit player virtual currency (**VC**) balances.
- **Characters**- View player-owned characters and edit basic details.
- **Multiplayer**- View player match history from multiplayer sessions.
- **Bans**- View player ban history.

#### Leaderboards

**Leaderboards**, the second tab, displays all the active leaderboards for your title. PlayFab leaderboards are driven by your player statistics. Selecting a statistic will display the corresponding leaders.

![Game Manager - Players - Leaderboards](media/tutorials/game-manager-player-leaderboards.png)

Selecting a **Player Name** will take you to that player overview.

The leaderboard reset frequency controls when one "season" begins and another ends. Our leaderboards can optionally to reset themselves **hourly**, **daily**, **weekly** and **monthly**.

Selecting the orange **EDIT LEADERBOARD** button allows you to edit your leaderboard name, as well as the reset frequency.

**Additional information:**

- [Using resettable statistics and leaderboards](../../social/tournaments-leaderboards/using-resettable-statistics-and-leaderboards.md)

[Back to Game Manager Sections](#game-manager-sections)

### 5. Economy

At the center of PlayFab economies is the concept of catalogs.

Catalogs are a collection of items, currencies, stores, and drop tables. This section provides all the tools needed to manage your game's virtual economy.

As an example, the following image shows **Unicorn Battle's** primary catalogs.

![Game Manager - Economy - Catalogs](media/tutorials/game-manager-economy-catalogs.png)

- **Catalog Items** - An item within the catalog. Items can be of several different types.
- **Virtual Currencies** - Arbitrary trackers for the mediums that can be exchanged for catalog items.
- **Stores**- A subset of catalog items that can be set to prices that are different than those specified by the catalog.
- **Drop Tables** - Control the item distribution when players open containers and bundles.

![Game Manager - Economy - Catalogs - Edit Container](media/tutorials/game-manager-economy-catalogs-edit-container.png)

Selecting any catalog item opens a detailed editor for the item properties.

The following example shows the **Edit Currency** page for the **Unicorn Battle's VC** called **Hearts**. The settings show that it is being used as a "lives" mechanic that regenerates every hour.

![Game Manager - Economy - Catalogs - Edit Container](media/tutorials/game-manager-economy-catalogs-edit-container.png)

**Additional Information:**

- [Catalogs Tutorial](../../commerce/items/catalogs.md)
- [Currencies Tutorial](../../commerce/economy/currencies.md)

[Back to Game Manager Sections](#game-manager-sections)

### 6. Servers

PlayFab works with many architectures and game types. Whether you are looking to hosting multi-player matches or just need a secure environment that can reduce many common forms of hacking and abuse.

![Game Manager - Servers - CloudScript](media/tutorials/game-manager-servers-cloudscript.png)

**CloudScript** offers an excellent alternative when compared with the overhead of dedicated game servers.

The servers section of the Game Manager has two major roles:

1. The main interface for uploading **CloudScript** files.
2. A control panel for your hosted multiplayer servers.

**Additional information:**

- [CloudScript Quickstart](../../automation/cloudscript/quickstart.md)
- [Building Custom Game Servers Tutorial](../../multiplayer/servers/custom-game-servers.md)

[Back to Game Manager Sections](#game-manager-sections)

### 7. Promotions

The promotions section offers tools for engaging with your players.

The following example shows the active **News** articles within **Unicorn Battle**.

![Game Manager - Promotions - Title News](media/tutorials/game-manager-promotions-title-news.png)

[Back to Game Manager Sections](#game-manager-sections)

### 8. Add-ons

We have many great vendors, and each one brings something unique to the table. We could tell you all about it here, but its better if you see it for yourself.

- To configure marketplace integrations for your title: Explore the **Add-ons** section of the **Game Manager** for details on the various add-ons.

  ![Game Manager - Add-ons - Partner Add-ons](media/tutorials/game-manager-add-ons-partner-add-ons.png)

Setup instructions for each add-on may vary. Additional billing information may also be required.

[Back to Game Manager Sections](#game-manager-sections)

### 9. Reports

PlayFab generates catalogs that capture daily and monthly activity. Currently, there are three reports available to all developers:

- **Daily Overview Report**: Reports the daily KPIs for your title.
- **Monthly Overview Report**: Reports the aggregated KPIs for the month.
- **Monthly Top Spender Report**: Reports the month's top paying player.

![Game Manager - Reports](media/tutorials/game-manager-reports.png)

For additional or custom reports, please open a feature request in our [community forums](https://community.playfab.com/spaces/24/index.html).

[Back to Game Manager Sections](#game-manager-sections)

## Basic actions

### Editing profile settings

1. Open the **Admin** menu by selecting the current **User**.
2. Then select **Edit Profile**.
3. Specify **Your Name**, a **Password**, add a **Phone number**, set your **Time zone**, and specify whether you want to enable **Two-Factor Authentication**.
4. Select the **Save Profile** button to save your changes and return to the studios page.

![Game Manager - Edit Profile](media/tutorials/game-manager-edit-profile.png)

- **Two-Factor Authentication** - Two-factor authentication improves the security of your developer accounts by requiring a code to be supplied when logging in.

### View PlayFab notifications

New notifications will be called out with a pink delimiter containing the number of new notifications.

![Unicorn Battle - Notifications indicator](media/tutorials/unicorn-battle-notifications-indicator.png)

1. Open the **Admin** menu by selecting the current **User**. Then select **News**.
2. View the published notifications.

![Game manager - Published Notifications](media/tutorials/game-manager-published-notifications.png)

Notifications include information on new features, **API** updates, and service outages.

### Create and edit studios and titles

#### To add a new studio

1. Select the orange **NEW STUDIO** button in the top right of the **Studios** page.
2. Enter a **Studio Name**.
3. Save your changes and return to the **Studios** page.

#### To edit an existing studio

![Game manager - Edit Studio](media/tutorials/game-manager-edit-studio.png)

1. Select the down-arrow next to your **Studio's Name**, and then select **Edit Studio**.
2. Make your edits.
3. Save your changes and return to the **Studios** page.

#### To add a new Title

![Game manager - Create a new game](media/tutorials/game-manager-create-a-new-game.png)

1. Select the **Create a new game** button under your existing **Titles**.
2. Enter your **Title** details. Optionally, this information can be added after title creation.
3. Save your changes and return to the **Studios** page.

#### To edit an existing title

![Game manager - Edit game](media/tutorials/game-manager-edit-game.png)

1. Select the down-arrow next to the **Title** you wish to edit and select **Edit game**.
2. Make your edits.
3. Save your changes and return to the **Studios** page.
    - **Title** - An individual instance of a game within **PlayFab**.
    - **Studio** - A group of **Titles** that can share data and developer access.

Developer accounts are special PlayFab accounts permitting access to one or more sections on one or more titles of a given studio.

![Game manager - PlayFab Demo Studio](media/tutorials/game-manager-playfab-demo-studio.png)

1. Select the down-arrow next to your **Studio's Name**, and then select **Manage Users**.
2. Add **Developer** accounts using the orange **NEW USER** button in the top right.
3. Remove **Developer** accounts by checking the box next to the account, and then selecting the **X DELETE** link in the top-left, above the **User** table.

If you do not already have a PlayFab developer account, an email will be sent to the address you provided. Upon confirmation, the new account will have access to the title.

## Settings actions

### Toggle API features

The **API Features** tab provides optional permissions that affect what an **API** set has permission to do. By default, all options are *Off*. Enabling these features will allow your title to be client-authoritative at the expense of security.

![Game manager - Settings - API Features](media/tutorials/game-manager-settings-api-features.png)

Choose your preferred permissions, and select the **Save API Features** button.

### View and edit title data

Title data is accessible from all **API** sets by all users. This makes title data an ideal place to store your custom title settings.

In the example below, we store: quests, enemy encounter details, achievement thresholds, events and sales data, and more.

![Game manager - Settings - Title Data](media/tutorials/game-manager-settings-title-data.png)

We provide tall and short views that make viewing text blobs easier.

#### Add or edit title data keys

1. Enter text for your **Key** (keys must be unique).
2. Enter text for your value (accepts strings up to 10KB).
3. Save your changes with the orange **SAVE TITLE DATA** button under the data table.

#### Remove title data keys

1. Check the box that corresponds to the row(s) that you wish to remove.
2. Select the **X Remove** link in the top-left, above the **User** table.
3. Save your changes with the orange **SAVE TITLE DATA** button under the data table.

### Update account permissions and view audit history

The **Permissions** tab displays an account table containing all of the developer accounts with access to the current title.

Users are added and removed at the studio level, but individual permissions are set on a per-title level. This flexibility enables you to provide your team with variable access depending on their role.

![Game manager - Settings - Permissions](media/tutorials/game-manager-settings-permissions.png)

#### Update account permissions

1. Select the **Account** you wish to edit.
2. Select the appropriate **Permissions** (Note: Admins have view and edit permissions for all sections).
3. Save your changes by selecting the orange **SAVE PERMISSIONS** button.

![Game manager - Settings - Edit permissions](media/tutorials/game-manager-settings-edit-permissions.png)

You can set viewing and editing restrictions for virtually every section within the Game Manager.

#### Track changes across your title

Every action taken within the Game Manager is logged for posterity. Check the **Audit History** tab to see what changes have been recently made.

![Game manager - Settings - Audit History](media/tutorials/game-manager-settings-audit-history.png)

Select any change to view the complete details.

## Promotions actions

### View or edit title news

1. Select an old **News** item to edit, or create a new one by selecting **NEW TITLE NEWS**.
2. Enter a **Title**, set the **Status** to **Published**, and enter your text into the **Body** field.
3. Select **SAVE TITLE NEWS** and your **News** is now ready for the client to receive.

![Game manager - Promotions - Edit Title News](media/tutorials/game-manager-promotions-edit-title-news.png)

Title news makes a great tool for in-game tips or message-of-the-week style communication.

### Generate coupon codes

1. Select your primary **Catalog** and the **Item ID** for the **Item** you wish to grant.
2. Choose the appropriate quantity, and select the **GENERATE COUPONS** button.
3. Game Manager will generate the codes in a downloadable **.csv** file.

![Game manager - Promotions - Coupons](media/tutorials/game-manager-promotions-coupons.png)

This coupon tool works great for generating the digital rewards for "backers" and testers.
