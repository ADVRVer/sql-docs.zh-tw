---
title: DISCOVER_KEYWORDS 資料列集 (XMLA) |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DISCOVER_KEYWORDS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_KEYWORDS rowset
ms.assetid: 99945e53-3a1b-4d7b-9aff-712977db8b2d
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: df7fd7c6bf7dbe9ebd0bb9057b5c82dc351afab3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36032416"
---
# <a name="discoverkeywords-rowset-xmla"></a>DISCOVER_KEYWORDS 資料列集 (XMLA)
  傳回 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) 提供者所保留關鍵字的相關資訊。  
  
 如果您呼叫[探索](../../xmla/xml-elements-methods-discover.md)方法`DISCOVER_KEYWORDS`中的列舉值[RequestType](../../xmla/xml-elements-properties/type-element-xmla.md)項目，`Discover`方法會傳回`DISCOVER_KEYWORDS`資料列集。  
  
## <a name="rowset-columns"></a>資料列集資料行  
 `DISCOVER_KEYWORDS`資料列集包含下列資料行。  
  
|資料行名稱|類型指標|長度|描述|  
|-----------------|--------------------|------------|-----------------|  
|`Keyword`|`DBTYPE_WSTR`||提供者保留的所有關鍵字的清單。<br /><br /> 範例：`AND`|  
  
 這個結構描述資料列集並未排序。  
  
## <a name="restriction-columns"></a>限制資料行  
 在下表列出的資料行上可能會限制 `DISCOVER_KEYWORDS` 資料列集。  
  
|資料行名稱|類型指標|限制狀態|  
|-----------------|--------------------|-----------------------|  
|`Keyword`|`DBTYPE_WSTR`|選擇性。|  
  
## <a name="see-also"></a>另請參閱  
 [XML for Analysis 結構描述資料列集](xml-for-analysis-schema-rowsets.md)   
 [DISCOVER_LITERALS 資料列集](discover-literals-rowset.md)  
  
  