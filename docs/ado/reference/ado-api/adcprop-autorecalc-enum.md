---
title: "ADCPROP_AUTORECALC_ENUM |Microsoft 文件"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: ADCPROP_AUTORECALC_ENUM
helpviewer_keywords: ADCPROP_AUTORECALC_ENUM [ADO]
ms.assetid: ded4f087-87b9-4efa-8026-bde53d3e9e8a
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2388e467e4224480fef339b7b3e407458964a692
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="adcpropautorecalcenum"></a>ADCPROP_AUTORECALC_ENUM
指定何時[MSDataShape](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)提供者會重新計算階層式資料錄集中的彙總和導出資料行。  
  
 這些常數僅能搭配**MSDataShape**提供者和**資料錄集**"**自動重新計算**"動態屬性，會參考[ADO動態屬性索引](../../../ado/reference/ado-api/ado-dynamic-property-index.md)與有記載在[Microsoft OLE DB 的資料指標服務](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)或[Microsoft Data Shaping Service 的 OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)文件。  
  
|常數|值|Description|  
|--------------|-----------|-----------------|  
|**adRecalcAlways**|1|預設值。 每當重新計算**MSDataShape**提供者會決定導出資料行而定的值已變更。|  
|**adRecalcUpFront**|0|開始建立階層時，才會計算**資料錄集**。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 這些常數沒有 ADO/WFC 對等項目。
