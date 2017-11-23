---
title: "Open 方法 (ADO MD) |Microsoft 文件"
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
f1_keywords:
- Open
- Cellset::Open
helpviewer_keywords: Open method [ADO MD]
ms.assetid: a87d8080-a238-45e5-bc80-9a8625b3810f
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1b80a0a92956315d7d19db5d17a535b6fe2204b6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="open-method-ado-md"></a>Open 方法 (ADO MD)
擷取多維度查詢的結果，並傳回結果[資料格集](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)。  
  
## <a name="syntax"></a>語法  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>參數  
 *Source*  
 選擇性。 A **Variant**會評估為有效的多維度查詢，例如多維度運算式 (MDX) 查詢。 *來源*引數會對應至[來源](../../../ado/reference/ado-md-api/source-property-ado-md.md)屬性。 如需有關 MDX 的詳細資訊，請參閱[OLE DB 的線上分析處理 (OLAP)](http://msdn.microsoft.com/en-us/8a7673c6-3ca1-4411-9f1e-adf1e47df4f3) Microsoft Data Access Components SDK 中的文件。  
  
 *ActiveConnection*  
 選擇性。 A **Variant**會評估為字串，請指定有效的 ADO[連接](../../../ado/reference/ado-api/connection-object-ado.md)物件變數名稱或連線的定義。 *ActiveConnection*引數會指定用來開啟連接[資料格集](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)物件。 如果您要傳入的連接定義，這個引數，ADO 會開啟新的連接使用指定的參數。 *ActiveConnection*引數會對應至[ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)屬性。  
  
## <a name="remarks"></a>備註  
 **開啟**方法會產生錯誤，如果省略了其中一個它的參數，且其對應的屬性值未設定之前嘗試開啟**資料格集**。  
  
## <a name="applies-to"></a>適用於  
 [Cellset 物件 (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>請參閱＜  
 [資料格集範例 (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [ActiveConnection 屬性 (ADO MD)](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)   
 [Close 方法 (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [連接物件 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [來源屬性 (ADO MD)](../../../ado/reference/ado-md-api/source-property-ado-md.md)   
 [State 屬性 (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
