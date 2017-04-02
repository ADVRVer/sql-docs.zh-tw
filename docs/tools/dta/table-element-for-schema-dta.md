---
title: "結構描述的 Table 元素 (DTA) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "XML"
helpviewer_keywords: 
  - "Table 元素 [DTA]"
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# 結構描述的 Table 元素 (DTA)
  指定要微調的資料表。  
  
## 語法  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## 元素屬性  
  
|Attribute|描述|  
|---------------|-----------------|  
|**NumberOfRows**|選擇性。 可讓您模擬不同大小的資料表之整數。|  
  
## 元素特性  
  
|特性|說明|  
|--------------------|-----------------|  
|**資料類型和長度**|**string**，在 1 和 255 個字元之間。|  
|**預設值**|無。|  
|**出現次數**|選擇性。 依照工作負載的需要，列出儘可能多的資料表。|  
  
## 元素關聯性  
  
|關聯性|元素|  
|------------------|--------------|  
|**父元素**|[資料庫的 Schema 元素 &#40;DTA&#41;](../../tools/dta/schema-element-for-database-dta.md)|  
|**子元素**|[資料表的 Name 元素 &#40;DTA&#41;](../../tools/dta/name-element-for-table-dta.md)|  
  
## 備註  
 如果您沒有指定 **Table** 元素，Database Engine Tuning Advisor 會假設指定資料庫的所有資料表都可以微調。  
  
## 範例  
 如需使用範例，請參閱[伺服器元素 &#40;DTA&#41;](../../tools/dta/server-element-dta.md)。  
  
## 另請參閱  
 [XML 輸入檔參考 &#40;Database Engine Tuning Advisor&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  