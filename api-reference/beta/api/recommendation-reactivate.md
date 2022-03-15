---
title: "recommendation: reactivate"
description: "Reactivate a completed, dismissed, or postponed recommendation object."
author: "hafowler"
ms.localizationpriority: medium
ms.prod: "directory-management"
doc_type: apiPageType
---

# Reactivate a recommendation
Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Reactivate a completed, dismissed, or postponed recommendation object. This action updates the **status** of the [recommendation](../resources/recommendation.md) to `active`. This method only works when the **status** of the recommendation is `completedByUser`, `dismissed`, or `postponed`.

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
POST https://graph.microsoft.com/beta/directory/recommendations/7918d4b5-0442-4a97-be2d-36f9f9962ece_Microsoft.Identity.IAM.Insights.ThirdPartyApps/reactivate
```

## Request headers
|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required.|

## Request body
Do not supply a request body for this method.

## Response

If successful, this action returns a `200 OK` response code and a [recommendation](../resources/recommendation.md) in the response body.

## Examples

### Request
<!-- {
  "blockType": "request",
  "name": "recommendationthis.reactivate"
}
-->
``` http
POST https://graph.microsoft.com/beta/directory/recommendations/7918d4b5-0442-4a97-be2d-36f9f9962ece_Microsoft.Identity.IAM.Insights.ThirdPartyApps/reactivate
```


### Response
>**Note:** The response object shown here might be shortened for readability.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.recommendation"
}
-->
``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#recommendation",
    "@odata.type": "#microsoft.graph.recommendation",
    "id": "7918d4b5-0442-4a97-be2d-36f9f9962ece_Microsoft.Identity.IAM.Insights.ThirdPartyApps",
    "createdDateTime": "2022-02-26T00:02:54Z",
    "impactStartDateTime": "2022-02-26T00:02:54Z",
    "postponeUntilDateTime": null,
    "lastModifiedDateTime": "2022-03-08T05:39:03.6654897Z",
    "lastModifiedBy": "131a8fea-5507-4ae4-90bf-20dbf1b6f1b5",
    "displayName": "Integrate your 3rd party apps with Azure AD",
    "insights": "No users are currently authenticating to any pre-integrated, custom app (BYOA) or SaaS app.",
    "benefits": "Integrating 3rd party apps with Azure AD allows you to leverage Azure AD's security features, which enables seamless, more productive and more secure sign-ins. You can add an additional security layer to your 3rd party app sign-ins by using conditional access.",
    "category": "configuration",
    "status": "active",
    "priority": "medium",
    "impactType": "tenantLevel",
    "actionSteps": [
        {
            "stepNumber": 1,
            "text": "1. Review your apps",
            "actionUrl": {
                "displayName": "Enterprise applications",
                "url": "https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AllApps/menuId/"
            }
        },
        {
            "stepNumber": 2,
            "text": "2. For each eligible apps, integrate your 3rd party app with Azure AD",
            "actionUrl": {
                "displayName": "Tutorials for integrating SaaS applications with Azure AD",
                "url": "https://docs.microsoft.com/en-us/azure/active-directory/saas-apps/tutorial-list"
            }
        }
    ]
  }
}
```