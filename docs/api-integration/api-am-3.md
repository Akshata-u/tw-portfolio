!!! example "About this article "
    Reference links to other articles are indicated but unavailable since these are sample documents.

!!! note "Note"
    - Currently, bulk update of assets is unsupported.
    
    - You need to have a write access on the assetID in order to perform an update.

### PUT Requests
**Path**: `/v1/assets/{assetID}`

**Request**: `PUT/v1/assets/{assetID}`

**Content-Type**: multipart/ form-data

**Headers**: `If-Match` / `If-None-Match`

**Input**

`id`- string - _(Required)_

* ID of the asset which you want to update.

`If-Match` and `If-None-Match` - string - _(Required)_

* At least one of these headers are required while updating the asset, in order to maintain integrity and verify the correctness of the update. An Etag header will be received in the response after the asset is updated. For more details, _click here_.

**Request Body** - _(Required)_

`file`: file upload - _(Required)_

* Any valid binary file such as image, text, etc. Provide either the actual file or the URL of the file.

`metadata` - object - _(Optional)_

* A key-value pair that you want to associate with the asset.

```
{
  "file": "string",
  "metadata": "object"
}
```

### PATCH Requests

**Path**: `/v1/assets/{assetID}`

**Request**: `PATCH/v1/assets/{assetID}`

**Content-Type**: multipart/ form-data or application/ json

**Headers**: `If-Match`/ `If-None-Match`

**Input**

`id`: string - _(Required)_

* ID of the asset which you want to update.

`If-Match` and `If-None-Match` - string - _(Required)_

* At least one of these headers are required while updating the asset, in order to maintain integrity and verify the correctness of the update. An Etag header will be received in the response after the asset is updated. For more details, _click here_.

**Request Body** - _(Required)_

`file`- file upload - _(Optional)_

* Any valid binary file such as image, text, etc. Provide either the actual file or the URL of the file.

`metadata` - object - _(Optional)_

* A key-value pair that you want to merge with the existing metadata. Albert follows JSON patch standards as mentioned in _this RFC_.

`uri` - string - _(Optional)_

* A valid http or https URL.

* This will create a new resource in the storage layer in the case of **managed assets**. 

* Length of `uri` = Max. 512 characters

`expires` - string - _(Optional)_

* The date and time at which the asset will cease to exist. The value can either be a duration in ISO8601 format, or `never`. 

* The value `never` indicates that the asset will exist perpetually i.e., without expiry. In asset and link responses, the same value is returned in the parameter `expiresOn`. If `"expires": "never"`, then `"expiresOn": null`. 

* If the `expires` parameter has already been defined at the time of asset creation, the new `expiresOn` value = the existing `expires` value + the `expires` value defined in the `PATCH` request.

```
{
  "file": "string",
  "metadata": "object",
  "uri": "string",
  "expires": "string"
}
```