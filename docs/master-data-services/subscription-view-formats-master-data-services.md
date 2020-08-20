---
description: 訂閱檢視格式 (Master Data Services)
title: 訂閱檢視格式
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ff1e2566-ac8f-467d-a6d9-12c3f13879b9
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ac58c9c1edfce6b02f48c31e220d37d842b18527
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456730"
---
# <a name="subscription-view-formats-master-data-services"></a>訂閱檢視格式 (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  根據您選取的實體或衍生階層，訂閱檢視可以使用下列格式。  
  
## <a name="subscription-view-formats"></a>訂閱檢視格式  
  
|名稱|描述|  
|----------|-----------------|  
|**分葉成員**|包含分葉成員及其相關聯的屬性值。|  
|**分葉成員歷程記錄**|包含分葉成員的歷程記錄資料及其相關聯的屬性值。 檢視格式是「緩時變維度類型 4」樣式。|  
|**分葉成員 SCD 類型 2**|包含分葉成員的歷程記錄和目前資料，以及其相關聯的屬性值。 檢視格式是「緩時變維度類型 2」樣式。|  
|**合併成員**|包含合併成員及其相關聯的屬性值。|  
|**合併成員歷程記錄**|包含合併成員的歷程記錄資料及其相關聯的屬性值。 檢視格式是「緩時變維度類型 4」樣式。|  
|**合併成員 SCD 類型 2**|包含合併成員的歷程記錄和目前資料，以及其相關聯的屬性值。 檢視格式是「緩時變維度類型 2」樣式。|  
|**集合成員資格**|包含集合清單及其相關聯的屬性值。|  
|**集合**|包含集合清單、每個集合中的成員以及加權值和排序次序。|  
|**集合成員歷程記錄**|包含集合成員的歷程記錄資料及其相關聯的屬性值。 檢視格式是「緩時變維度類型 4」樣式。|  
|**集合成員 SCD 類型 2**|包含集合成員的歷程記錄和目前資料，以及其相關聯的屬性值。 檢視格式是「緩時變維度類型 2」樣式。|  
|**明確父子**|包含父子格式實體的明確階層結構。|  
|**明確層級**|包含層級格式實體的明確階層結構。|  
|**衍生父子 (衍生階層檢視)**|包含父子格式的衍生階層結構。|  
|**衍生層級 (衍生階層檢視)**|包含層級格式的衍生階層結構。|  
  
## <a name="see-also"></a>另請參閱  
 [總覽：將資料匯出 &#40;Master Data Services&#41;](../master-data-services/overview-exporting-data-master-data-services.md)   
 [建立訂閱檢視以匯出資料 &#40;Master Data Services&#41;](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)  
  
  
