## Reading an Asset

This allows you to retrieve information within an asset. You can read an asset in the following ways:


| Description | Request Path |
| ------------| -------------|
| To retrieve all the assets | `GET/v1/assets` |
| To retrieve a specific asset | `GET/v1/assets/{assetID}` |
| To retrieve all the links associated with a specific asset as the source | `GET/v1/assets/{assetID}/links`|
| To retrieve all versions of a specific asset | `GET/v1/assets/{assetID}/versions` |
| To retrieve a specific version of an asset | `GET/v1/assets/{assetID}/versions/ {versionID}`|

## Querying an Asset

Assets can be searched based on:

* the metadata present in them

* the URI of the resources within the asset

**Path**: `/v1/assets/: query`

**Request Type**: `POST/v1/assets/: query`

**Content-Type**: application/ json

**Query Parameters** `limit` ,`offset`, `sort`, `showDeleted`

**Input**

`uri`- string - _(Optional)_

* A valid http or hips URL of the asset that you want to query. 

* Length of `uri`= Max. 512 characters

`metadata` - object - _(Optional)_

* A key-value pair associated with the asset.

`managed`- boolean - _(Optional. Default: `false`)_

* This is a query parameter, and the value is either `true` or `false`. 

* This parameter filters the search based on **managed** or **unmanaged** assets respectively.

```
{
  "uri": "string",
  "metadata": "object",
  "managed": boolean
}
```
**Example JSON: Managed Assets**

This shall query all the managed assets that contain `"team": "mumbai"` as one of the key- value pairs in their metadata. 

```
{
  "metadata": {
    "team": "mumbai"
  },
  "managed": true
}
```

**Example JSON: Unmanaged Assets**

This shall query all the unmanaged assets that contain `"team" : "mumbai"` as one of the key-value pairs in their metadata.

```
{
  "metadata": {
    "team": "mumbai"
  },
  "managed": false
}
```

Additionally, the following query parameters can be used. When multiple query parameters are defined, an `AND` operation will be performed to combine them.

`limit`: number - _(Optional. Default: `10000`)_

* Number of records to return in a single page. For example, fetch `100` records that meet the condition.

`offset`- string - _(Optional. Default: `beginning of page`)_

* Page offset to continue the search and retrieve the next page.

`sort`- string - _(Optional. Default: `createdMS:desc`)_

* Defines the direction of the sorting. This field can have one of the following values: `createdMs: asc`, `modifiedMs: desc`, and `modifiedMs: asc` and `modifiedMs: desc` 

`showDeleted`- boolean - _(Optional. Default: `false`)_

* When `true`, deleted assets will also be included in the query results.

!!! success "Support"
    If you've hit a roadblock, reach out to us through any of the following support channels:    
    
    **Email**: helpid@cxxxxxs.com
    
    **Slack**: #<channel>