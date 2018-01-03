---
title: "ADCPROP_ASYNCTHREADPRIORITY_ENUM |Microsoft 文件"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: ADCPROP_ASYNCTHREADPRIORITY_ENUM
helpviewer_keywords: ADCPROP_ASYNCTHREADPRIORITY_ENUM [ADO]
ms.assetid: f0965617-17d8-41e0-98d0-f824274735a6
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8a03809de8f86cf4ece91be598a71cd24b3ad9d7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="adcpropasyncthreadpriorityenum"></a>ADCPROP_ASYNCTHREADPRIORITY_ENUM
針對 RDS[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)物件，指定非同步擷取資料的執行緒的執行優先順序。  
  
 使用這些常數**資料錄集**"**背景執行緒優先順序**"動態屬性，其參考 ADO-OLE DB 動態屬性的索引中，並記載於[Microsoft OLE DB 的資料指標服務](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)文件。  
  
|常數|ReplTest1|描述|  
|--------------|-----------|-----------------|  
|**adPriorityAboveNormal**|4|設定一般和最高優先順序。|  
|**adPriorityBelowNormal**|2|設定優先順序最低和標準之間。|  
|**adPriorityHighest**|5|設定的最高的可能優先權。|  
|**AdPriorityLowest**|@shouldalert|設定最低的可能優先權。|  
|**adPriorityNormal**|3|設定為 normal 的優先權。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 封裝： **com.ms.wfc.data**  
  
|常數|  
|--------------|  
|AdoEnums.AdcPropAsyncThreadPriority.ABOVENORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.BELOWNORMAL|  
|AdoEnums.AdcPropAsyncThreadPriority.HIGHEST|  
|AdoEnums.AdcPropAsyncThreadPriority.LOWEST|  
|AdoEnums.AdcPropAsyncThreadPriority.NORMAL|
