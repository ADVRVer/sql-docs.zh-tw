---
title: Cube 屬性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Collation property
- ID property
- ErrorConfiguration property
- cubes [Analysis Services], properties
- Description property
- DefaultMeasure property
- ProcessingMode property
- AggregationPrefix property
- EstimatedRows property
- Visible property
- StorageLocation property
- StorageMode property
- ScriptErrorHandlingMode property
- Source property
- ScriptCacheProcessingMode property
- Language property
- Name property
- properties [Analysis Services], cubes
- ProcessingPriority property
- ProactiveCaching property
ms.assetid: 72ca3387-620d-4473-8e23-7fe1f2b3d5bf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4d2b99362f242ff7f815e9ceb9f67db9c80983c8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "62727644"
---
# <a name="cube-properties"></a>Cube 屬性
  Cube 有許多屬性，您可以設定這些屬性來影響整個 Cube 的行為。 這些屬性都摘要在下表中：  
  
> [!NOTE]  
>  有些屬性是在建立 Cube 時自動設定，且無法變更。  
  
 如需如何設定 cube 屬性的詳細資訊，請參閱[Cube 設計工具&#40;Analysis Services-多維度資料&#41;](../cube-designer-analysis-services-multidimensional-data.md)。  
  
|屬性|描述|  
|--------------|-----------------|  
|`AggregationPrefix`|指定用於彙總名稱的一般前置詞。|  
|`Collation`|指定用底線隔開的地區設定識別碼 (LCID) 和比較旗標 (例如，Latin1_General_C1_AS)。|  
|`DefaultMeasure`|包含定義 Cube 之預設量值的多維度運算式 (MDX) 運算式。|  
|`Description`|提供 Cube 的描述，可以在用戶端應用程式中公開。|  
|`ErrorConfiguration`|包含用來處理重複索引鍵、未知索引鍵、錯誤限制、發生錯誤時的動作、錯誤記錄檔和 Null 索引鍵處理的可設定錯誤處理設定。|  
|`EstimatedRows`|指定 Cube 中的估計資料列數目。|  
|`ID`|包含 Cube 的唯一識別碼 (ID)。|  
|`Language`|指定 Cube 的預設語言識別碼。|  
|`Name`|指定 Cube 的使用者易記名稱。|  
|`ProactiveCaching`|定義 Cube 的主動式快取設定。|  
|`ProcessingMode`|指出在處理期間或處理之後，是否應該進行檢索和彙總。 選項**定期**或`lazy`。|  
|`ProcessingPriority`|決定 Cube 在背景作業 (例如延遲彙總和索引) 期間的處理優先權。 預設值是 **0**。|  
|`ScriptCacheProcessingMode`|指出在處理期間或處理之後是否應建立指令碼快取。 選項**定期**和`lazy`。|  
|`ScriptErrorHandlingMode`|決定錯誤處理。 選項為 `IgnoreNone` 或 `IgnoreAll`。|  
|`Source`|顯示用於 Cube 的資料來源檢視。|  
|`StorageLocation`|指定 Cube 的檔案系統儲存位置。 如果未指定，會從包含 Cube 物件的資料庫中繼承位置。|  
|`StorageMode`|指定 Cube 的儲存模式。 值為`MOLAP`， `ROLAP`，或 `HOLAP``.`|  
|`Visible`|決定 Cube 的可見性。|  
  
> [!NOTE]  
>  如需有關如何設定 ErrorConfiguration 屬性的值，當使用 null 值和其他資料完整性議題的詳細資訊，請[Analysis Services 2005 中處理資料完整性問題](https://go.microsoft.com/fwlink/?LinkId=81891)。  
  
## <a name="see-also"></a>另請參閱  
 [主動式快取&#40;資料分割&#41;](partitions-proactive-caching.md)  
  
  
