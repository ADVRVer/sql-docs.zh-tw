---
title: OLE DB 資料表值參數變更結構描述資料列 |Microsoft 文件
description: 變更 OLE DB Table-Valued 參數的結構描述資料列集
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- table-valued parameters (OLE DB), schema rowsets changed for (OLE DB)
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 6eb387969549f0ed72e3635a80fcd6db34852c10
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689831"
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a>針對 OLE DB 資料表值參數而變更的結構描述資料列集
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  下列是已變更或加入來支援資料表值參數的結構描述資料列集。  
  
|結構描述資料列集|描述|  
|-------------------|-----------------|  
|DBSCHEMA_PROCEDURE_PARAMETERS|兩個新的資料行會加在名為 SS_TYPE_CATALOG_NAME 和 SS_TYPE_SCHEMANAME 的資料列集結尾。 這些資料行可以針對未來的類型重複使用。 TYPE_NAME 和 LOCAL_TYPE_NAME 資料行會包含 TABLE 類型的資料表值參數的名稱。 DATA_TYPE 資料行對於資料表值參數具有 DBTYPE_TABLE = 143 值。|  
|DBSCHEMA_TABLE_TYPES|已新增這個資料列集來支援資料表值參數。 這與 DBSCHEMA_TABLES 完全相同，但它只會針對資料表類型 (而不會針對資料表、檢視或同義字) 傳回中繼資料。 TABLE_TYPE 資料行會具有 'TABLE TYPE' 值。|  
|DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS|已新增這個資料列集來支援資料表值參數。 這與 DBSCHEMA_PRIMARY_KEYS 完全相同，但它只會針對資料表類型 (而不會針對資料表) 傳回主索引鍵中繼資料。|  
|DBSCHEMA_TABLE_TYPE_COLUMNS|已新增這個資料列集來支援資料表值參數。 這與 DBSCHEMA_COLUMNS 完全相同，但它只會針對資料表類型 (而不會針對資料表、檢視或同義字) 傳回資料行中繼資料。|  
  
## <a name="see-also"></a>另請參閱  
 [資料表值參數&#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [您可以使用資料表值參數&#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
