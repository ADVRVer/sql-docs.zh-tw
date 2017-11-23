---
title: "AffectEnum |Microsoft 文件"
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
f1_keywords: AffectEnum
helpviewer_keywords: AffectEnum enumeration [ADO]
ms.assetid: 1ab921a0-6c57-43b4-9291-701b2599f3e8
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 060740333ab0190d1a691f040b045f63a76b2e0d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="affectenum"></a>AffectEnum
指定的記錄作業所影響。  
  
|常數|值|Description|  
|--------------|-----------|-----------------|  
|**adAffectAll**|3|如果沒有[篩選](../../../ado/reference/ado-api/filter-property.md)套用至**資料錄集**，會影響所有的記錄。<br /><br /> 如果**篩選**屬性設定為字串準則 (例如 「 作者 = 'smith ' 距離 」)，則作業會影響在目前的章節中的可見記錄。<br /><br /> 如果**篩選**屬性設定為隸屬[FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md)陣列的書籤，則作業將會影響的所有資料列或**資料錄集**。 **注意：****adAffectAll**隱藏在 Visual Basic 物件瀏覽器。|  
|**adAffectAllChapters**|4|會影響所有同層級章節中的所有記錄**資料錄集**，包括透過任何看不見**篩選**，它會套用。|  
|**adAffectCurrent**|1|會影響目前的記錄。|  
|**adAffectGroup**|2|會影響滿足目前的記錄[篩選](../../../ado/reference/ado-api/filter-property.md)屬性設定。 您必須設定**篩選**屬性**FilterGroupEnum**值或陣列**書籤**才能使用此選項。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 封裝： **com.ms.wfc.data**  
  
|常數|  
|--------------|  
|AdoEnums.Affect.ALL|  
|AdoEnums.Affect.ALLCHAPTERS|  
|AdoEnums.Affect.CURRENT|  
|AdoEnums.Affect.GROUP|  
  
## <a name="applies-to"></a>適用於  
  
|||  
|-|-|  
|[CancelBatch 方法 (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|[Delete 方法 (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|  
|[Resync 方法](../../../ado/reference/ado-api/resync-method.md)|[UpdateBatch 方法](../../../ado/reference/ado-api/updatebatch-method.md)|
