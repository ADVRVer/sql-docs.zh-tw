---
title: MDSCHEMA_MEASUREGROUPS 資料列集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_MEASUREGROUPS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEASUREGROUPS rowset
ms.assetid: bab1bbd0-421b-4fad-9aee-e6511e0e1f1b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f889b66a9dcc72053c04adbd5e1949f6ebbf17dc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48060281"
---
# <a name="mdschemameasuregroups-rowset"></a>MDSCHEMA_MEASUREGROUPS 資料列集
  描述資料庫內的量值群組。  
  
## <a name="rowset-columns"></a>資料列集資料行  
 `MDSCHEMA_MEASUREGROUPS`資料列集包含下列資料行。  
  
|資料行名稱|類型指標|長度|描述|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||此量值群組所屬目錄的名稱。 如果提供者不支援目錄，則為 `NULL`。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||不支援。|  
|`CUBE_NAME`|`DBTYPE_WSTR`||此量值群組所屬 Cube 的名稱。|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||量值群組的名稱。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||成員的可讀取描述。|  
|`IS_WRITE_ENABLED`|`DBTYPE_BOOL`||布林值，指出量值群組是否為可寫入。<br /><br /> 如果量值群組為可寫入，則傳回 `true`。|  
|`MEASUREGROUP_CAPTION`|`DBTYPE_WSTR`||量值群組的顯示標題。|  
  
 這個結構描述資料列集並未排序。  
  
## <a name="restriction-columns"></a>限制資料行  
 下表中的資料行上可以限制 `MDSCHEMA_MEASUREGROUPS` 資料列集。  
  
|資料行名稱|類型指標|限制狀態|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|選擇性。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|選擇性。|  
|`CUBE_NAME`|`DBTYPE_WSTR`|選擇性。|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`|選擇性。|  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB for OLAP 結構描述資料列集](ole-db-for-olap-schema-rowsets.md)  
  
  
