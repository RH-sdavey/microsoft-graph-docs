---
title: "recommendation resource type"
description: "Represents an Azure AD best practice or improvement action recommended by Microsoft for your Azure AD tenant."
author: "hafowler"
ms.localizationpriority: medium
ms.prod: "directory-management"
doc_type: resourcePageType
---

# recommendation resource type

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents an Azure AD best practice or improvement action recommended by Microsoft for your Azure AD tenant. Our service runs on a daily basis to check your tenant against predefined conditions for every recommendation. If we detect that a recommendation applies, the corresponding recommendation object is generated and its status is set to `active`.

There are currently 5 possible recommendations you may see:

1.	Integrate 3rd party apps with Azure AD
2.	Convert from per user MFA to Conditional Access MFA
3.	Minimize MFA prompts for users signing in from known devices
4.	Migrate apps from AD FS to Azure AD
5.	Migrate eligible users from SMS and voice call to use the Authenticator app


Inherits from [entity](../resources/entity.md).

## Methods
|Method|Return type|Description|
|:---|:---|:---|
|[List recommendations](../api/directory-list-recommendations.md)|[recommendation](../resources/recommendation.md) collection|Get a list of [recommendation](../resources/recommendation.md) objects and their properties.|
|[Get recommendation](../api/recommendation-get.md)|[recommendation](../resources/recommendation.md)|Read the properties and relationships of a [recommendation](../resources/recommendation.md) object.|
|[Complete](../api/recommendation-complete.md)|[recommendation](../resources/recommendation.md)|Mark a [recommendation](../resources/recommendation.md) status as `completedByUser` after completing all [action steps](../resources/actionstep.md).|
|[Postpone](../api/recommendation-postpone.md)|[recommendation](../resources/recommendation.md)|Mark a [recommendation](../resources/recommendation.md) status as `postponed` to a specified date and time.|
|[Dismiss](../api/recommendation-dismiss.md)|[recommendation](../resources/recommendation.md)|Mark a [recommendation](../resources/recommendation.md) status as `dismissed`.|
|[Reactivate](../api/recommendation-reactivate.md)|[recommendation](../resources/recommendation.md)|Mark an accidentally dismissed, completed, or postponed [recommendation](../resources/recommendation.md) object as `active`. |
|[List impactedResources](../api/recommendation-list-impactedresources.md)|[recommendationResource](../resources/recommendationresource.md) collection|Retrieve the Azure AD resources that are associated with a recommendation.|

## Properties
|Property|Type|Description|
|:---|:---|:---|
|actionSteps|[actionStep](../resources/actionstep.md) collection|List of actions to take to complete a [recommendation](../resources/recommendation.md).|
|benefits|String|An explanation of why [completing the recommendation](../api/recommendation-complete.md) will benefit you. Corresponds to the *Value* section of a recommendation shown in the Azure AD portal.|
|category|recommendationCategory|Indicates the type of [recommendation](../resources/recommendation.md). The possible values are: `usageAndCompliance`, `security`, `productivity`, `health`, `configuration`, `unknownFutureValue`. To be deprecated.|
|createdDateTime|DateTimeOffset|The date and time when the recommendation was detected as applicable to your directory.|
|displayName|String|The title of the [recommendation](../resources/recommendation.md).|
|featureArea|String|The directory feature that the [recommendation](../resources/recommendation.md) is related to.|
|id|String|The unique identifer for the recommendation. Inherited from [entity](../resources/entity.md). This is a concatenation of your tenant id and the recommendation's nickname.|
|impactStartDateTime|DateTimeOffset|The future date and time when a [recommendation](../resources/recommendation.md) should be completed. |
|impactType|String|Indicates the scope of impact of a [recommendation](../resources/recommendation.md). `Tenant level` indicates that the recommendation impacts the whole tenant. Other possible values include `users`, `applications`, `devices`, and `groups`.|
|insights|String|Describes how a [recommendation](../resources/recommendation.md) uniquely applies to your directory. Corresponds to the *Description* section of a recommendation shown in the Azure AD portal. This is based on background information about your tenant including usage statistics and insights related to resource distribution and resource state. |
|lastCheckedDateTime|DateTimeOffset|The most recent date and time a [recommendation](../resources/recommendation.md) was deemed applicable to your directory.|
|lastModifiedBy|String|Name of the user who last updated the **status** of the [recommendation](../resources/recommendation.md).|
|lastModifiedDateTime|DateTimeOffset|The date and time the **status** of a [recommendation](../resources/recommendation.md) was last updated.|
|postponeUntilDateTime|DateTimeOffset|The future date and time when the **status** of a postponed [recommendation](../resources/recommendation.md) will be `active` again.|
|priority|recommendationPriority|Indicates the time sensitivity for a [recommendation](../resources/recommendation.md) to be completed. Microsoft auto assigns this value. The possible values are: `low`, `medium`, `high`. Read-only|
|status|recommendationStatus| Indicates the status of the [recommendation](../resources/recommendation.md) based on user or system action.  The possible values are: `active`, `completedBySystem`, `completedByUser`, `dismissed`, `postponed`, `unknownFutureValue`. By default, a recommendation's status is set to `active` when the recommendation is first generated. Status is set to `completedBySystem` when our service detects that a recommendation which was once `active` no longer applies.|

## Relationships
|Relationship|Type|Description|
|:---|:---|:---|
|impactedResources|[recommendationResource](../resources/recommendationresource.md) collection|List of directory resources associated with a recommendation. Supports `$expand` including a nested `$select` query.|

## JSON representation
The following is a JSON representation of the resource.
<!-- {
  "blockType": "resource",
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.recommendation",
  "baseType": "microsoft.graph.entity",
  "openType": false
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.recommendation",
  "id": "String (identifier)",
  "actionSteps": [
    {
      "@odata.type": "microsoft.graph.actionStep"
    }
  ],
  "benefits": "String",
  "category": "String",
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "impactType": "String",
  "impactStartDateTime": "String (timestamp)",
  "insights": "String",
  "lastCheckedDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": "String",
  "postponeUntilDateTime": "String (timestamp)",
  "priority": "String",
  "status": "String"
}
```
