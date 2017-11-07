---
title: "DISCOVER_MEMORYUSAGE 資料列集 |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: e416ea61-9615-468c-a96f-bbf731f803b1
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3dcbb314e1816757562f93290d95a3f9e345460b
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="discovermemoryusage-rowset"></a>DISCOVER_MEMORYUSAGE 資料列集
  傳回伺服器所配置之各種物件的 DISCOVER_MEMORYUSAGE 統計資料。  
  
> [!WARNING]  
>  這個資料列集可能會產生非常龐大的結果集。 如果結果由於所需的顯示記憶體超過 SQL Server Management Studio 允許的記憶體而無法顯示，這些結果就會寫入位於下列預設位置的暫存檔案：  
>   
>  '\<磁碟機 >: \Users\\< 使用者名稱\>\AppData\Local\Temp\\< fileID\>.xml'。  
  
 **適用於：**表格式模型、 多維度模型  
  
## <a name="rowset-columns"></a>資料列集資料行  
 **DISCOVER_MEMORYUSAGE**資料列集包含下列資料行。  
  
|資料行名稱|類型指標|限制|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**MemoryID**|**DBTYPE_UI8**||識別記憶體的編號。|  
|**MemoryName**|**DBTYPE_WSTR**||擁有記憶體之物件的名稱。|  
|**SPID**|**DBTYPE_UI4**|是|配置記憶體的工作階段。 零表示記憶體未繫結至特定工作階段。|  
|**依據 CreationTime**|**DBTYPE_DBTIMESTAMP**||「建立物件的時間」或「配置記憶體的時間」。|  
|**BaseObjectType**|**DBTYPE_UI4**|是|這是描述物件類型的編號。 具有相同 BaseObjectType 的物件會具有相同類型。|  
|**MemoryUsed**|**DBTYPE_UI8**|是|這是物件的目前大小，可能會小於配置給物件使用的記憶體。|  
|**MemoryAllocated**|**DBTYPE_UI8**||配置給物件使用的記憶體數量，可能會大於物件實際使用的記憶體數量。|  
|**MemoryAllocBase**|**DBTYPE_UI8**||一開始配置給物件本身的位元組 (不含物件內容的其他配置)。|  
|**MemoryAllocFromAlloc**|**DBTYPE_UI8**||配置給此物件內容的記憶體。|  
|**ElementCount**|**DBTYPE_UI4**||對於容器物件而言，這是該物件所包含的物件數目。|  
|**壓縮**|**DBTYPE_BOOL**|是|布林值，這個值會指出記憶體是否可壓縮 (可能會由於記憶體不足的壓力而收回)。 如果為 true，就表示記憶體可壓縮。如果為 false，就表示記憶體不可壓縮。|  
|**ObjectParentPath**|**DBTYPE_WSTR**||識別此物件之完整路徑的字串。|  
|**ObjectID**|**DBTYPE_WSTR**||識別物件的字串。 此物件的完整路徑由字串: (ObjectParentPath + '。 ' + ObjectId)。|  
  
 這個結構描述資料列集並未排序。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>使用 ADOMD.NET 傳回資料列集  
 使用 ADOMD.NET 和結構描述資料列集來擷取中繼資料時，您可以使用 GUID 或字串，在 GetSchemaDataSet 方法中參考結構描述資料列集物件。 如需詳細資訊，請參閱 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)。  
  
 下表將提供可識別此資料列集的 GUID 和字串值。  
  
|引數|值|  
|--------------|-----------|  
|GUID|A07CCD21-8148-11D0-87BB-00C04FC33942|  
|ADOMDNAME|MemoryUsage|  
  
## <a name="see-also"></a>另請參閱  
 [XML for Analysis 結構描述資料列集](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

