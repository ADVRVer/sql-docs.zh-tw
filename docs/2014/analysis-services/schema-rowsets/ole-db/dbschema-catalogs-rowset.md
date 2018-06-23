---
title: DBSCHEMA_CATALOGS 資料列集 |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DBSCHEMA_CATALOGS
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_CATALOGS rowset
ms.assetid: f02dc75d-5442-4eea-b33a-567dc816be7a
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: df3b146d3e1015fd4a78254be0d8a7a6083991d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36023212"
---
# <a name="dbschemacatalogs-rowset"></a>DBSCHEMA_CATALOGS 資料列集
  識別與可從資料庫管理系統 (DBMS) 存取之目錄相關聯的實體屬性 (Attribute)。  
  
## <a name="rowset-columns"></a>資料列集資料行  
 `DBSCHEMA_CATALOGS`資料列集包含下列資料行。  
  
|資料行名稱|類型指標|長度|描述|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|255|目錄的名稱。 不可為 null。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||資料表的可讀取描述。|  
|`ROLES`|`DBTYPE_WSTR`||目前使用者所屬角色的以逗號分隔的清單。<br /><br /> 星號 (\*) 是包含為角色，如果目前的使用者是伺服器或資料庫管理員。<br /><br /> 如果其中一個角色使用動態安全性，則 `Username` 會附加至 `ROLES`。|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||上次修改目錄的日期。|  
  
 資料列集會按 `CATALOG_NAME` 排序。  
  
## <a name="restriction-columns"></a>限制資料行  
 在下表列出的資料行上可能會限制 `DBSCHEMA_CATALOGS` 資料列集。  
  
|資料行名稱|類型指標|限制狀態|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|選擇性|  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 結構描述資料列集](ole-db-schema-rowsets.md)  
  
  