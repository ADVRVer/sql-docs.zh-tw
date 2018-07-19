---
title: DISCOVER_COMMAND_OBJECTS 資料列集 |Microsoft 文件
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a580be3c487416c6f5c710553f2e4a4d9869e206
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
ms.locfileid: "34030329"
---
# <a name="discovercommandobjects-rowset"></a>DISCOVER_COMMAND_OBJECTS 資料列集
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  提供參考命令使用中之物件的資源使用量與活動的有關資訊。  
  
 **適用於：** 表格式模型、 多維度模型  
  
## <a name="rowset-columns"></a>資料列集資料行  
 **DISCOVER_COMMAND_OBJECTS**資料列集包含下列資料行。  
  
|資料行名稱|類型指標|限制|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**SESSION_SPID**|**DBTYPE_I4**|是|工作階段識別碼。|  
|**SESSION_ID**|**DBTYPE_WSTR**|是|做為 GUID 的工作階段唯一識別碼。|  
|**SESSION_COMMAND_COUNT**|**DBTYPE_I4**||命令的序號。|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**|是|目前物件父系的路徑。|  
|**OBJECT_ID**|**DBTYPE_WSTR**|是|在建立物件時所定義的物件識別碼。|  
|**OBJECT_VERSION**|**DBTYPE_I4**||物件的中繼資料版本號碼，每次改變物件時，這個號碼就會變更。|  
|**OBJECT_DATA_VERSION**|**DBTYPE_I4**||物件之資料的歷程記錄號碼。 每次處理物件時，這個號碼就會增加。|  
|**OBJECT_CPU_TIME_MS**|**DBTYPE_I8**||命令開始以後，物件所耗用的 CPU 時間 (以毫秒為單位)。|  
|**OBJECT_READ_KB**|**DBTYPE_I8**||自從命令啟動之後，物件讀取的資料累積值 (以 KB 為單位)。|  
|**OBJECT_READS**|**DBTYPE_I8**||自從命令啟動之後，物件執行之讀取作業的累積數目。|  
|**OBJECT_WRITE_KB**|**DBTYPE_I8**||自從命令啟動之後，物件寫入的資料累積值 (以 KB 為單位)。|  
|**OBJECT_WRITES**|**DBTYPE_I8**||自從命令啟動之後，物件執行之寫入作業的累積數目。|  
|**OBJECT_ROWS_RETURNED**|**DBTYPE_I8**||自從命令啟動之後，物件傳回呼叫端的資料列數目。|  
|**OBJECT_ROWS_SCANNED**|**DBTYPE_I8**||自從命令啟動之後，物件掃描的資料列數目。|  
  
 這個結構描述資料列集並未排序。  
  
> [!IMPORTANT]  
>  DISCOVER_COMMAND_OBJECTS 結構描述資料列集不會透過 DMV 查詢來報告活動。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>使用 ADOMD.NET 傳回資料列集  
 使用 ADOMD.NET 和結構描述資料列集來擷取中繼資料時，您可以使用 GUID 或字串，在 GetSchemaDataSet 方法中參考結構描述資料列集物件。 如需詳細資訊，請參閱 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)。  
  
 下表將提供可識別此資料列集的 GUID 和字串值。  
  
|引數|值|  
|--------------|-----------|  
|GUID|a07ccd35-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|CommandObjects|  
  
## <a name="see-also"></a>另請參閱  
 [XML for Analysis 結構描述資料列集](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
