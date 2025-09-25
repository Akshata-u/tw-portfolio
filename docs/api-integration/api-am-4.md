!!! example "About this article "
    Reference links to other articles are indicated but unavailable since these are sample documents.

A **managed** or **unmanaged** asset is eliminated once its `expiredOn` date passes. This, however, is a soft delete only. The user can pass the following query string parameter to view the expired asset, but will be unable to modify it in any way:

**Path**: `/v1/assets/{id}` or `/v1/assets/route`

**Request Type**: `GET/v1/assets/{id}` or `GET/v1/assets/route`

**Content-Type**: application/ json

**Query Parameters**: `showDeleted=true`

To fully restore an asset, use the following route:

  * **Path**: `/v1/assets/{id}:restore`

  * **Request Type**: `POST/v1/assets/{id}:restore`

  * **Content-Type**: application/ json

```
{
"expires": "string"
}
```
`expires` - string - _(Optional)_

* When a value is defined, it will be used to calculate the expiration. Otherwise, the expiration of the restored asset will be calculated from the original `expires` field. The value can either be a duration in ISO8601 format, or `never`. 

* The value `never` indicates that the asset will exist perpetually i.e., without expiry. In asset and link responses, the same value is returned in the parameter `expiresOn` If `"expires": "never"`, then `"expiresOn": null`.

!!! note "Note"
    By updating the `expires` field, you can use this route to extend the expiration of a non-expired asset as an alternative method to using `PATCH` requests described in the earlier article.