---
description: 變更追蹤 (Master Data Services)
title: 變更追蹤
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 134f6e6b573fd77440b656504c12c292e7ff37c4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500676"
---
# <a name="change-tracking-master-data-services"></a>變更追蹤 (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以使用變更追蹤群組在屬性值變更時採取動作。 當您不知道新值，但想要知道是否發生任何變更時，請使用變更追蹤。  
  
## <a name="configuring-change-tracking"></a>設定變更追蹤  
 若要設定變更追蹤，您要將屬性加入至變更追蹤群組。 此群組可以包含一個或多個屬性。 接著，您要建立商務規則來定義群組中的任何屬性變更時所要採取的動作。  
  
> [!NOTE]  
>  變更追蹤商務規則會將暫存 (匯入的) 資料視為變更。  
  
## <a name="related-tasks"></a>相關工作  
  
|工作描述|主題|  
|----------------------|-----------|  
|將屬性加入至變更追蹤群組。|[將屬性加入至變更追蹤群組 &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|建立根據屬性變更來起始動作的商務規則。|[根據屬性值變更來起始動作 &#40;Master Data Services&#41;](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a>相關內容  
  
-   [驗證 &#40;Master Data Services&#41;](../master-data-services/validation-master-data-services.md)  
  
-   [商務規則 &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
-   [屬性 &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
  
