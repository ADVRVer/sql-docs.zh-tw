---
title: RecordOpenOptionsEnum |Microsoft 文件
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordOpenOptionsEnum
helpviewer_keywords:
- RecordOpenOptionsEnum enumeration [ADO]
ms.assetid: 9028aba4-90fc-4dfc-88e4-fa8a7b6fedee
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0795d6eb942f10a97be1acda77954ae43fd4f2e4
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281257"
---
# <a name="recordopenoptionsenum"></a>RecordOpenOptionsEnum
指定選項，開啟[記錄](../../../ado/reference/ado-api/record-object-ado.md)。 這些值可能會合併使用或者。  
  
|常數|ReplTest1|描述|  
|--------------|-----------|-----------------|  
|**adDelayFetchFields**|0x8000|表示欄位相關聯的提供者**記錄**需要一開始，擷取，但是可以在第一次嘗試存取該欄位擷取。 此旗標，如果沒有所指定的預設行為是來擷取所有**記錄**物件欄位。|  
|**adDelayFetchStream**|0x4000|指出提供者的預設資料流相關聯**記錄**需要一開始擷取。 預設行為，此旗標，如果沒有所指定是要擷取相關聯的預設資料流**記錄**物件。|  
|**adOpenAsync**|0x1000|表示**記錄**物件在非同步模式中開啟。|  
|**adOpenExecuteCommand**|0x10000|表示來源字串包含應該執行的命令文字。 此值相當於**adCmdText**選項**Recordset.Open**。|  
|**adOpenRecordUnspecified**|-1|預設值。 表示未指定任何選項。|  
|**adOpenOutput**|0x800000|表示如果來源會指向包含可執行的指令碼的節點 (例如。ASP 網頁），然後開啟**記錄**會包含執行的指令碼的結果。 這個值只適用於非集合的記錄。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 這些常數沒有 ADO/WFC 對等項目。  
  
## <a name="applies-to"></a>適用於  
 [Open 方法 (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)
