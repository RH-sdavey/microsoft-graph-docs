---
title: "recommendationResource: complete"
description: "Complete a recommendationResource object and update its status to completedByUser."
author: "hafowler"
ms.localizationpriority: medium
ms.prod: "directory-management"
doc_type: apiPageType
---

# recommendationResource: complete
Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Complete a [recommendationResource](../resources/recommendationresource.md) object and update its status to `completedByUser`.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type|Permissions (from least to most privileged)|
|:---|:---|
|Delegated (work or school account)|DirectoryRecommendations.ReadWrite.All|
|Delegated (personal Microsoft account)|Not supported.|
|Application|DirectoryRecommendations.ReadWrite.All|

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
POST /directory/recommendations/{recommendationId}/impactedResources/{recommendationResourceId}/complete
```

## Request headers
|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required.|

## Request body
Do not supply a request body for this method.

## Response

If successful, this action returns a `200 OK` response code and a [recommendationResource](../resources/recommendationresource.md) in the response body.

## Examples

### Request
<!-- {
  "blockType": "request",
  "name": "recommendationresourcethis.complete"
}
-->
``` http
POST https://graph.microsoft.com/beta/directory/recommendations/7918d4b5-0442-4a97-be2d-36f9f9962ece_Microsoft.Identity.IAM.Insights.ServicePrincipalKeyExpiry/impactedResources/3ba3165c-2a6e-4a21-8046-3b4d461a63fb/complete
```


### Response
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.recommendationResource"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#recommendationResource",
    "@odata.type": "#microsoft.graph.recommendationResource",
    "id": "3ba3165c-2a6e-4a21-8046-3b4d461a63fb",
    "recommendationId": "7918d4b5-0442-4a97-be2d-36f9f9962ece_Microsoft.Identity.IAM.Insights.ApplicationCredentialExpiry",
    "resourceType": "app",
    "addedDateTime": "2022-02-28T06:26:13.9349146Z",
    "displayName": "Contoso IWA App Tutorial",
    "owner": null,
    "rank": 1,
    "portalUrl": "https://portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationMenuBlade/Credentials/appId/3ba3165c-2a6e-4a21-8046-3b4d461a63fb",
    "apiUrl": null,
    "status": "completedByUser",
    "additionalDetails": [
        {
            "key": "ExpiringCredentialsCount",
            "value": "1"
        }
    ]
}
```