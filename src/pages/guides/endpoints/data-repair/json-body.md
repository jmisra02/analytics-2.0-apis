---
title: Job definition reference
description: Supported variables, actions, and filters when using the Data Repair API.
---

# Job definition reference

A JSON request body is required when creating a Data Repair API job. This page provides a full list of variables, actions, and filters that you can include to create a valid JSON request body.

## Structure

A request body consists of one or more variables with the desired action for each variable. You can also optionally include a filter for a given variable.

```json
{
  "variables": {
    "{VARIABLE_1}": {
      "action": "{ACTION_1}",
      "filter": {"condition":  "{CONDITION_1}"}
    },
    "{VARIABLE_2}": {
      "action": "{ACTION_2}"
    }
  }
}
```

## Variables

The Data Repair API supports the following variables, with their supported actions.

Variable | Supported actions | Supported filters by action | Description
--- | --- | --- | ---
`activitymap` | `delete` | Does not support any filters. | Deletes all [Activity map](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/activitymap-reporting-analytics.html) data for the hit.
`campaign` | `set`<br/>`delete`<br/>`deleteQueryString`<br/>`deleteQueryStringParameters` | `delete` and `set` support default filters for their respective action. `deleteQueryString` and `deleteQueryStringParameters` do not support filters. | The [Tracking code](https://experienceleague.adobe.com/docs/analytics/components/dimensions/tracking-code.html) dimension. Only tracking codes with an [expiration](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/conversion-variables/conversion-var-admin.html) of page view, visit, or time period of 1 day or shorter are supported with this API. A data repair job fails if it includes this variable with an expiration of a time period greater than 1 day or on an event. As a best practice, Adobe recommends [resetting](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/conversion-variables/conversion-var-admin.html) the tracking code before a repair job runs so that values persisted by visitors do not reappear after a repair job is complete.
`entrypage`<br/>`entrypageoriginal` | `set`<br/>`delete`<br/>`deleteQueryString`<br/>`deleteQueryStringParameters` | `delete` and `set` support default filters for their respective action. `deleteQueryString` and `deleteQueryStringParameters` do not support filters. | The [Entry page](https://experienceleague.adobe.com/docs/analytics/components/dimensions/entry-dimensions.html) dimension.
`evar1` - `evar250` | `set`<br/>`delete`<br/>`deleteQueryString`<br/>`deleteQueryStringParameters` | `delete` and `set` support default filters for their respective action. `deleteQueryString` and `deleteQueryStringParameters` do not support filters. | [eVar](https://experienceleague.adobe.com/docs/analytics/components/dimensions/evar.html) dimensions. Only eVars with an [expiration](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/conversion-variables/conversion-var-admin.html) of page view, visit, or time period of 1 day or shorter are supported with this API. Merchandising variables, enabled currently or historically, are not supported. As a best practice, Adobe recommends [resetting](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/conversion-variables/conversion-var-admin.html) the eVar in question before a repair job runs so that values persisted by visitors do not reappear after a repair job is complete.
`geodma` | `delete` | The only supported filter is `inList`. | The [US DMA](https://experienceleague.adobe.com/docs/analytics/components/dimensions/us-dma.html) dimension.
`geocity` | `delete` | The only supported filter is `inList`. | The [Cities](https://experienceleague.adobe.com/docs/analytics/components/dimensions/cities.html) dimension.
`geocountry` | `delete` | The only supported filter is `inList`. | The [Countries](https://experienceleague.adobe.com/docs/analytics/components/dimensions/countries.html) dimension.
`geolatitude`<br/>`geolongitude` | `delete` | The only supported filter is `inList`. | N/A
`georegion` | `delete` | The only supported filter is `inList`. | The [Regions](https://experienceleague.adobe.com/docs/analytics/components/dimensions/regions.html) dimension.
`geozip` | `delete` | The only supported filter is `inList`. | The [Zip code](https://experienceleague.adobe.com/docs/analytics/components/dimensions/zip-code.html) dimension collected through geolocation. See also `zip`.
`ipaddress` | `delete` | The only supported filter is `inList`. | The IP address of the visitor.
`latitude`<br/>`longitude` | `delete` | The only supported filter is `inList`. | N/A
`latlon1`<br/>`latlon23`<br/>`latlon45`<br/>`pointofinterest`<br/>`pointofinterestdistance` | `delete` | Does not support any filters. | [Mobile](https://experienceleague.adobe.com/docs/analytics/components/dimensions/mobile-dimensions.html) dimensions.
`mobileaction` | `delete` | Supports all default `delete` filters. | The [Mobile action](https://experienceleague.adobe.com/docs/analytics/components/dimensions/mobile-dimensions.html) dimension.
`mobileappid`<br/>`mobilemessagebuttonname`<br/>`mobilemessageid`<br/>`mobilerelaunchcampaigncontent`<br/>`mobilerelaunchcampaignmedium`<br/>`mobilerelaunchcampaignsource`<br/>`mobilerelaunchcampaignterm`<br/>`mobilerelaunchcampaigntrackingcode` | `set`<br/>`delete`<br/>`deleteQueryString`<br/>`deleteQueryStringParameters` | `set` supports all default filters. `delete`, `deleteQueryString`, and `deleteQueryStringParameters` do not support any filters. | [Mobile](https://experienceleague.adobe.com/docs/analytics/components/dimensions/mobile-dimensions.html) dimensions.
`page` | `set`<br/>`deleteQueryString`<br/>`deleteQueryStringParameters` | `set` supports default filters _except_ `isEmpty`. `deleteQueryString` and `deleteQueryStringParameters` do not support filters. | The [Page](https://experienceleague.adobe.com/docs/analytics/components/dimensions/page.html) dimension.
`pageeventvar1` | `set`<br/>`deleteQueryString`<br/>`deleteQueryStringParameters` | `set` supports default filters _except_ `isEmpty`. `deleteQueryString` and `deleteQueryStringParameters` do not support filters. | The [`linkURL`](https://experienceleague.adobe.com/docs/analytics/implementation/vars/config-vars/linkurl.html) implementation variable.
`pageeventvar2` | `set`<br/>`deleteQueryString`<br/>`deleteQueryStringParameters` | `set` supports default filters _except_ `isEmpty`. `deleteQueryString` and `deleteQueryStringParameters` do not support filters. | The [Download link](https://experienceleague.adobe.com/docs/analytics/components/dimensions/download-link.html), [Exit link](https://experienceleague.adobe.com/docs/analytics/components/dimensions/exit-link.html), or [Custom link](https://experienceleague.adobe.com/docs/analytics/components/dimensions/custom-link.html) dimension, depending on the type of link.
`pageurl` | `deleteQueryString`<br/>`deleteQueryStringParameters` | Does not support filters. | The [Page URL](https://experienceleague.adobe.com/docs/analytics/components/dimensions/page-url.html) dimension.
`pageurlfirsthit`<br/>`pageurlvisitstart` | `deleteQueryString`<br/>`deleteQueryStringParameters` | Does not support any filters. | N/A
`prop1` - `prop75` | `set`<br/>`delete`<br/>`deleteQueryString`<br/>`deleteQueryStringParameters` | `delete` and `set` support default filters for their respective action. `deleteQueryString` and `deleteQueryStringParameters` do not support filters. | [Prop](https://experienceleague.adobe.com/docs/analytics/components/dimensions/prop.html) dimensions.
`referrer` | `deleteQueryString`<br/>`deleteQueryStringParameters` | Does not support filters. | The [Referrer](https://experienceleague.adobe.com/docs/analytics/components/dimensions/referrer.html) dimension.
`referrerfirsthit`<br/>`referrervisit` | `deleteQueryString`<br/>`deleteQueryStringParameters` | Does not support filters. | N/A
`sitesections` | `set`<br/>`delete`<br/>`deleteQueryString`<br/>`deleteQueryStringParameters` | `delete` and `set` support default filters for their respective action. `deleteQueryString` and `deleteQueryStringParameters` do not support filters. | The [Site section](https://experienceleague.adobe.com/docs/analytics/components/dimensions/site-section.html) dimension.
`video`<br/>`videoad` | `set`<br/>`deleteQueryString`<br/>`deleteQueryStringParameters` | `set` supports default filters. `deleteQueryString` and `deleteQueryStringParameters` do not support filters. | [Media Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/metrics-and-metadata/audio-video-parameters.html) dimensions.
`videoadname`<br/>`videoadplayername`<br/>`videoadadvertiser`<br/>`videoaudioalbum`<br/>`videoaudioartist`<br/>`videoaudioauthor`<br/>`videoaudiolabel`<br/>`videoaudiopublisher`<br/>`videoaudiostation`<br/>`videoadcampaign`<br/>`videochannel`<br/>`videocontenttype`<br/>`videoepisode`<br/>`videofeedtype`<br/>`videomvpd`<br/>`videoname`<br/>`videonetwork`<br/>`videopath`<br/>`videoplayername`<br/>`videoseason`<br/>`videoshow`<br/>`videoshowtype`<br/>`videostreamtype` | `set`<br/>`delete`<br/>`deleteQueryString`<br/>`deleteQueryStringParameters` | `set` supports all default filters. `delete`, `deleteQueryString`, and `deleteQueryStringParameters` do not support any filters. | [Media Analytics](https://experienceleague.adobe.com/docs/media-analytics/using/metrics-and-metadata/audio-video-parameters.html) dimensions.
`zip` | `delete` | The only supported filter is `inList`. | The [Zip code](https://experienceleague.adobe.com/docs/analytics/components/dimensions/zip-code.html) dimension collected through the `zip` variable (not geosegmentation). See also `geozip`.

## Actions

Each variable requires an action. Adobe supports the following four actions:

* **`set`**: Overwrites the variable to the value in the `setValue` property. Include the `setValue` property alongside the `action` property inside the variable. It supports all filters by default; however, some variables do not support all filters for this action. See the above table to confirm that a variable supports a filter with this action.
* **`delete`**: Clears the variable value. It supports all filters except `isEmpty` by default. Some variables do not support all filters for this action. See the above table to confirm that a variable supports a filter with this action.
* **`deleteQueryString`**: Remove the entire query string from a variable value. If the value does not appear to be a URL, no action is taken. Filters are not supported with this action.
* **`deleteQueryStringParameters`**: Remove one or more query string parameters and their values from a variable. The query parameters removed are based on the string array `parameters`. Include the `parameters` array alongside the `action` property inside the variable. Up to 10 parameters are supported. If the value does not appear to be a URL, no action is taken. Filters are not supported with this action.

<CodeBlock slots="heading, code" repeat="4" languages="JSON,JSON,JSON,JSON"/>

#### set

```json
{
  "variables": {
    "evar1": {
      "action": "set",
      "setValue": "New value"
    }
  }
}
```

#### delete

```json
{
  "variables": {
    "evar1": {
      "action": "delete"
    }
  }
}
```

#### deleteQueryString

```json
{
  "variables": {
    "evar1": {
      "action": "deleteQueryString"
    }
  }
}
```

#### deleteQueryStringParameters

```json
{
  "variables": {
    "evar1": {
      "action": "deleteQueryStringParameters",
      "parameters": ["param1", "param2"]
    }
  }
}
```

## Filters

The `set` and `delete` actions support filters, which allow you to selectively repair certain rows based on the filter criteria. Make sure that an action supports the desired filter when creating the JSON body.

* **`inList`**: Include all rows where the variable contains at least one value from the `matchValues` array. The `matchValues` array can hold up to 1000 values.
* **`isEmpty`**: Only include rows where the variable does not contain a value. Cannot be used with the `delete` action.
* **`contains`**: Include rows where the variable contains the value in `matchValue`.
* **`doesNotContain`**: Include rows where the value in `matchValue` is not present.
* **`startsWith`**: Limit the action to rows where the value starts with the value in `matchValue`.
* **`doesNotStartWith`**: Limit the action to rows where the value does not start with the value in `matchValue`.
* **`endsWith`**: Limit the action to rows where the value ends with the value in `matchValue`.
* **`doesNotEndWith`**: Limit the action to rows where the value does not end with the value in `matchValue`.
* **`isURL`**: Only include the row if Adobe recognizes the value as a URL.
* **`isNotURL`**: Only include the row if Adobe recognizes that the value is not a URL.

<CodeBlock slots="heading, code" repeat="6" languages="JSON,JSON,JSON,JSON,JSON,JSON"/>

#### inList

```json
{
  "variables": {
    "evar1": {
      "action": "delete",
      "filter": {
        "condition": "inList",
        "matchValues": ["match1", "match2"]
      }
    }
  }
}
```

#### isEmpty

```json
{
  "variables": {
    "evar1": {
      "action": "set", 
      "setValue": "new value", 
      "filter": {
        "condition": "isEmpty"
      }
    }
  }
}
```

#### contains

```json
{
  "variables": {
    "evar1": {
      "action": "delete",
      "filter": {
        "condition": "contains",
        "matchValue": "@"
      }
    }
  }
}
```

#### startsWith

```json
{
  "variables": {
    "evar1": {
      "action": "delete",
      "filter": {
        "condition": "startsWith",
        "matchValue": "ABC"
      }
    }
  }
}
```

#### endsWith

```json
{
  "variables": {
    "evar1": {
      "action": "delete",
      "filter": {
        "condition": "endsWith",
        "matchValue": "XYZ"
      }
    }
  }
}
```

#### isURL

```json
{
  "variables": {
    "evar1": {
      "action": "delete",
      "filter": {
        "condition": "isURL"
      }
    }
  }
}
```

## Example repair definition file

The following data repair definition simultaneously performs the following four actions:

* Deletes all activity map data
* Deletes the value in `prop12` across all rows
* Sets `eVar74` to the value of "Turtles" across all rows
* Deletes the value in `eVar107` if the existing eVar value contains "Fox" or "Dog"

```json
{
  "variables": {
    "activitymap": {
      "action": "delete"
    },
    "prop12": {
      "action": "delete"
    },
    "evar74": {
      "action": "set",
      "setValue": "Turtles"
    },
    "evar107": {
      "action": "delete",
      "filter": {
        "condition": "inList",
        "matchValues": ["Fox", "Dog"]
      }
    }
  }
}
```

Once you have a completed JSON body and a `validationToken` from the [Server call estimate endpoint](server-call-estimate.md), you can make a call to the [Job endpoint](job.md) to make the data repair API call.