---
title: ADCPROP_UPDATECRITERIA_ENUM | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_UPDATECRITERIA_ENUM
helpviewer_keywords:
- ADCPROP_UPDATECRITERIA_ENUM [ADO]
ms.assetid: 33fd7b65-2ec8-4f62-91a7-630b5dab1aa2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91b4d64095c02fbf3f969248fc78d375a191fe72
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63065259"
---
# <a name="adcpropupdatecriteriaenum"></a>ADCPROP_UPDATECRITERIA_ENUM
指定哪些欄位可用來偵測衝突，開放式資料來源之資料列更新期間[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)物件。  
  
 使用這些常數**資料錄集**"**更新準則**」 中參考的動態屬性[ADO 動態屬性索引](../../../ado/reference/ado-api/ado-dynamic-property-index.md)和記載於[Microsoft OLE DB 的資料指標服務](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)文件。  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|**adCriteriaAllCols**|1|如果已變更的資料列的資料來源的任何資料行，會偵測衝突。|  
|**adCriteriaKey**|0|偵測到衝突，如果索引鍵的資料行的資料來源的資料列已變更，這表示已刪除資料列。|  
|**adCriteriaTimeStamp**|3|偵測到衝突，如果時間戳記的資料來源的資料列已變更，這表示已存取之資料列之後**資料錄集**取得。|  
|**adCriteriaUpdCols**|2|偵測到衝突，如果任何資料來源的資料行的資料列，對應至已更新欄位**資料錄集**已變更。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 封裝： **com.ms.wfc.data**  
  
|常數|  
|--------------|  
|AdoEnums.AdcPropUpdateCriteria.ALLCOLS|  
|AdoEnums.AdcPropUpdateCriteria.KEY|  
|AdoEnums.AdcPropUpdateCriteria.TIMESTAMP|  
|AdoEnums.AdcPropUpdateCriteria.UPDCOLS|
