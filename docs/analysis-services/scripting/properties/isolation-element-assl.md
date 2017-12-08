---
title: "Isolation 元素 (ASSL) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Isolation Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: Isolation element
ms.assetid: 28c98c6f-668e-4547-8d25-127cc3995a7d
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7a4f8b20b29956a77fc42450a229776e9ce91813
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="isolation-element-assl"></a>Isolation 元素 (ASSL)
  表示衍生自元素的隔離層級[DataSource](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)資料型別。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<DataSource>  
   ...  
   <Isolation>...</Isolation>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|資料類型和長度|字串 (列舉)|  
|預設值|*ReadCommitted*|  
|基數|0-1：只能出現一次的選擇性元素。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|-------------|  
|父元素|[資料來源](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)|  
|子元素|無|  
  
## <a name="remarks"></a>備註  
 這個元素的值限制為下表所列的其中一個字串。  
  
|值|Description|  
|-----------|-----------------|  
|*ReadCommitted*|指定陳述式不能讀取其他交易已修改而尚未認可的資料。 這個選項可避免中途讀取。 其他交易可以變更目前交易內部個別陳述式之間的資料。 這會導致不可重複讀取或虛設項目資料。 此值為 **Isolation** 元素的預設值。|  
|*快照式*|指定交易中任何陳述式所讀取的資料，都是交易啟動時就存在之資料的交易一致性版本。 交易只能查看交易啟動之前所認可的資料修改。 其他交易在目前交易開始之後所做的資料修改將不會顯示給在目前交易中執行的陳述式。 結果是交易中的陳述式會取得已認可之資料的快照集，如同資料在交易啟動時的狀態。|  
  
## <a name="see-also"></a>請參閱＜  
 [屬性 &#40;ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
