---
title: DISCOVER_KEYWORDS 資料列集 (OLE DB for OLAP) |Microsoft Docs
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
ms.assetid: 70cc680d-9530-469b-8a61-4e6779aec17a
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 117e5b2d706a23bc847e5450ab2a2c5cf277a80e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247478"
---
# <a name="discoverkeywords-rowset-ole-db-for-olap"></a>DISCOVER_KEYWORDS 資料列集 (OLE DB for OLAP)
  列舉提供者所保留字詞的清單。  
  
## <a name="rowset-columns"></a>資料列集資料行  
 DISCOVER_KEYWORDS 資料列集包含下列資料行。  
  
|資料行名稱|類型指標|長度|描述|  
|-----------------|--------------------|------------|-----------------|  
|`Keyword`|`DBTYPE_WSTR`||保留的關鍵字。|  
  
 這個結構描述資料列集並未排序。  
  
## <a name="restriction-columns"></a>限制資料行  
 在下表列出的資料行上可能會限制 DISCOVER_KEYWORDS 資料列集。  
  
|資料行名稱|類型指標|限制狀態|  
|-----------------|--------------------|-----------------------|  
|`Keyword`|`DBTYPE_WSTR`|選擇性。|  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB for OLAP 結構描述資料列集](ole-db-for-olap-schema-rowsets.md)  
  
  
