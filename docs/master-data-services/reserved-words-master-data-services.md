---
title: 保留字 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
caps.latest.revision: 11
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 3386a8c4a37aafd747dd61bb37f3464c0c8efa56
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2018
ms.locfileid: "35335002"
---
# <a name="reserved-words-master-data-services"></a>保留字 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，當您建立模型物件或成員時，無法使用某些字詞。 使用這些字詞可能會導致錯誤。  
  
> [!NOTE]  
>  您也應該對使用特殊字元 (符號、連字號等) 加以限制。  
  
-   [模型](../master-data-services/reserved-words-master-data-services.md#models)  
  
-   [實體](../master-data-services/reserved-words-master-data-services.md#entities)  
  
-   [明確階層](../master-data-services/reserved-words-master-data-services.md#exhierarchies)  
  
-   [屬性](../master-data-services/reserved-words-master-data-services.md#attributes)  
  
-   [成員](../master-data-services/reserved-words-master-data-services.md#members)  
  
##  <a name="models"></a> 模型  
 如果您建立一個名稱設定為 **Name** 或 **Code** 的模型，請勿選取 [建立與模型同名的實體]，原因是 **Name** 或 **Code** 無法用於實體的名稱。  
  
##  <a name="entities"></a> 實體  
 您無法針對實體名稱使用 **Name** 或 **Code**。  
  
##  <a name="exhierarchies"></a> 明確階層  
 您無法針對明確階層名稱使用 **Name** 或 **Code**。  
  
##  <a name="attributes"></a> 屬性  
  
-   **ID**  
  
-   **Code**  
  
-   **EnterUserName**  
  
-   **LastChgUserName**  
  
-   **名稱**  
  
-   **EnterDTM**  
  
-   **EnterUserID**  
  
-   **EnterUserName**  
  
-   **LastChgDTM**  
  
-   **LastChgUserID**  
  
-   **Status_ID**  
  
-   **ValidationStatus_ID**  
  
-   **Version_ID**  
  
##  <a name="members"></a> 成員  
 對於成員而言，您無法針對 **Code**屬性值使用 **MDMMemberStatus**、 **MDMUnused** 或 **ROOT** 。  
  
## <a name="see-also"></a>另請參閱  
 [Master Data Services 概觀 &#40;MDS&#41;](../master-data-services/master-data-services-overview-mds.md)  
  
  
