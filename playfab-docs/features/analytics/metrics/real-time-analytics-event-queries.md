---
title: Real-time Analytics - Event Queries
author: v-thopra
description: Describes how to compose simple and complex search queries for PlayFab events.
ms.author: v-thopra
ms.date: 01/11/2018
ms.topic: article
ms.prod: playfab
keywords: playfab, analytics, metrics, events, queries
ms.localizationpriority: medium
---

# Real Time Analytics - event queries

Several PlayFab Real Time analytics tools support querying for a specific set of events. Each query is represented as a text expression and follows the rules described in this tutorial.

Consider the event shown below.

```json
{
    "EventName": "title_statistic_version_changed",
    "StatisticName": "tournamentScore_hourly",
    "StatisticVersion": 1290,
    "ScheduledResetInterval": "Hour",
    "ScheduledResetTime": "2017-04-17T09:00:00Z",
    "EventNamespace": "com.playfab",
    "EntityType": "title",
    "Source": "PlayFab",
    "EventId": "a1883560c93b43f5b0543ade2d8cd093",
    "EntityId": "6EEA",
    "SourceType": "BackEnd",
    "Timestamp": "2017-04-17T09:00:22.4012656Z",
    "History": null,
    "CustomTags": null,
    "Reserved": null
}
```

In PlayFab, an event is represented as an *object* with a set of *fields*. Each field has a *value*.

You can compose a query expression to filter events by specific values on one or more fields. Query expressions can be [simplistic](#simplistic-queries) or [complex](#complex-queries).

PlayFab Free Tier only allows searching by the default event fields. The Paid Tier enables searching by custom event fields.

Please post on our [forums](https://community.playfab.com/questions/ask.html) to ask about Paid Tiers and enabling **PlayStream** history.

## Simplistic Queries

A simplistic query is just a value you want to search for. PlayFab goes through each property of each event looking for that specific value.

For example, consider the aforementioned event and its field called **StatisticName**.
This field has the value: **tournamentScore_hourly**.

Let's begin a query:

- Using the **Search Field** provided, enter **tournamentScore_hourly (1)**.
- Select the **Run Query** button **(2)**.
- The result will be rendered in the **Event Timeline** columns **(3)** and will contain the specified **Event**.

![Simplistic Event Query - Straight value](media/tutorials/simplistic-event-query-straight-value.png)  

This occurs because PlayFab analyzed all the events, and found that *this particular one* has some property with the value of **tournamentScore_hourly**.

> [!IMPORTANT]
> PlayFab supports wildcards, and some of the **regex** expressions.

This means that you may search by part of the value. In the example shown below:

- Querying **tournamentScore_** in the field **(1)**.
- Results in **no events found** in the list **(2)**.
- Using a wildcard, we adjust the query to **tournamentScore_\* (3)**.
- This results in displaying *all* events that have a field with the value starting with **tournamentScore_ (4)**.

![Simplistic Event Query - Wildcard value](media/tutorials/simplistic-event-query-wildcard-value.png)  

Using this technique, you can quickly search for relevant events, without a need to build complex queries or to use a query builder.

## Complex queries

To run a complex analysis, you will need complex queries with several conditions. A complex query consists of one or more query expressions, separated by AND/OR operators.

A *filter expression* consists of 2 parts, and has the format shown below.

`object_property:value_descriptor`.

**object_property** points to a property on your event data (that you want to filter by), and generally looks like the following example.

 `eventData.propertyName<.otherPropertyName*>`.

The `eventData` part is absolutely necessary to point PlayFab to an event object. You can then extract specific properties using dot notation: `eventData.eventName`. You may also refer to nested properties like this: `eventData.history.triggeredEvents`.

> [!IMPORTANT]
> Object property requires **camelCase** parts starting with a lowercase letter. For example, each event has a property called **EventName**. However, to access this property in a query, you have to adjust the first letter of the property and use **eventData.eventName**.

**value_descriptor** is an expression that describes the value of the field you want to use to filter. The simplest form of value descriptor is the value itself. The query shown below will look for all events with names equal to **player_created**.

`eventData.eventName:player_created`

We can customize the value descriptor by kicking in some regular expression elements, like wildcards.

> [!NOTE]
> By convention, *all* of the PlayFab player-oriented event names start with "**player_**".

![PlayFab player event names](media/tutorials/playfab-player-event-names.png)  

The query shown below will allow us to locate *all* such events.

`eventData.eventName:player_*`

Another example of a complicated value descriptor is the one for the date property. The following query incorporates all the events which have a timestamp between **April 1st** and **April 17th**.

`eventData.timestamp:[2017-04-01T00:00:00 TO 2017-04-17T00:00:00]`

Finally, we can combine *several* filter expressions using AND/OR operators, with parenthesis for grouping.

The query shown below will locate *all* of the events that occurred from **April 1st** to **April 17th**, and have the following event names.

- **player_logged_in**
- **player_statistic_changed**

`eventData.timestamp:[2017-04-01T00:00:00 TO 2017-04-17T00:00:00]  AND ( eventData.eventName:player_logged_in OR eventData.eventName:player_statistic_changed )`
