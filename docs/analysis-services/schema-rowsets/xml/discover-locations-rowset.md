---
title: "DISCOVER_LOCATIONS 資料列集 |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 6d3a1171-8e4d-4022-ade0-b785cf795d70
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 61f69caeab165c4d6822f8f25667ad544d6014ec
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="discoverlocations-rowset"></a>DISCOVER_LOCATIONS 資料列集
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]傳回備份檔案的內容的相關資訊。 您必須擁有存取備份檔案位置的權限。  
  
## <a name="rowset-columns"></a>資料列集資料行  
 **DISCOVER_LOCATIONS**資料列集包含下列資料行。  
  
|資料行名稱|類型指標|限制|描述|  
|-----------------|--------------------|-----------------|-----------------|  
|**LOCATION_BACKUP_FILE_PATHNAME**|**DBTYPE_WSTR**|必要項，請參閱下文。|備份檔案的位置。|  
|**LOCATION_PARTITION_OBJECTPATH**|**DBTYPE_WSTR**||相對於 data 資料夾的資料分割路徑。|  
|**LOCATION_PARTITION_DATASOURCEID**|**DBTYPE_WSTR**||用於處理資料分割的資料來源識別碼。|  
|**LOCATION_PARTITION_DATASOURCENAME**|**DBTYPE_WSTR**||用於處理的資料來源名稱。|  
|**LOCATION_PARTITION_NAME**|**DBTYPE_WSTR**||資料分割名稱。|  
|**LOCATION_PARTITION_SIZE**|**DBTYPE_WSTR**||大約的資料分割大小。|  
|**LOCATION_CONNECTION_STRING**|**DBTYPE_WSTR**||處理中所用之資料來源的連接字串。|  
|**LOCATION_PARTITION_FOLDER**|**DBTYPE_WSTR**||產生備份檔案時此資料分割的原始位置。|  
  
 這個結構描述資料列集並未排序。  
  
## <a name="restriction-columns"></a>限制資料行  
 **DISCOVER_LOCATIONS**上表中列出的資料行可能會限制資料列集。  
  
|資料行名稱|類型指標|限制狀態|  
|-----------------|--------------------|-----------------------|  
|**LOCATION_BACKUP_FILE_PATHNAME**|**DBTYPE_WSTR**|必要項|  
|**LOCATION_PASSWORD PF_DBTYPE**|**DBTYPE_WSTR**|如果在備份期間指定它，則為必要項。 此限制不是用來限制傳回的資料列， 它是用來提供密碼以存取位置。|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>使用 ADOMD.NET 傳回資料列集  
 使用 ADOMD.NET 和結構描述資料列集來擷取中繼資料時，您可以使用 GUID 或字串，在 GetSchemaDataSet 方法中參考結構描述資料列集物件。 如需詳細資訊，請參閱 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)。  
  
 下表將提供可識別此資料列集的 GUID 和字串值。  
  
|引數|ReplTest1|  
|--------------|-----------|  
|GUID|a07ccd92-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|位置|  
  
## <a name="see-also"></a>請參閱  
 [XML for Analysis 結構描述資料列集](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
