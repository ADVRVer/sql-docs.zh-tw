---
title: 資料表值參數類型支援 (OLE DB 驅動程式)
description: OLE DB 資料表值參數類型支援
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 453609d2d5633b6270ab565a2da50a98c909e86a
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87244132"
---
# <a name="ole-db-table-valued-parameter-type-support"></a>OLE DB 資料表值參數類型支援
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  本文描述資料表值參數的 OLE DB 類型支援。  
  
## <a name="table-valued-parameter-rowset-object"></a>資料表值參數資料列集物件  
 您可以針對資料表值參數建立專用的資料列集物件。 您可以使用 ITableDefinitionWithConstraints::CreateTableWithConstraints 或 IOpenRowset::OpenRowset 來建立資料表值參數資料列集物件。 若要這樣做，請將 *pTableID* 參數的 *eKind* 成員設定為 DBKIND_GUID_NAME，並提供 CLSID_ROWSET_INMEMORY 當作 *guid* 成員。 使用 IOpenRowset::OpenRowset 時，您必須在 *pTableID* 的 *pwszName* 成員中指定資料表值參數的伺服器類型名稱。 資料表值參數資料列集物件的行為就如同一般 OLE DB Driver for SQL Server 物件。  
  
```  
const GUID CLSID_ROWSET_TVP =   
{0xc7ef28d5, 0x7bee, 0x443f, {0x86, 0xda, 0xe3, 0x98, 0x4f, 0xcd, 0x4d, 0xf9}};  
  
CoType RowsetTVP  
{  
[mandatory] interface IAccessor;  
[mandatory] interface IColumnsInfo;  
[mandatory] interface IConvertType;  
[mandatory] interface IRowset;  
[mandatory] interface IRowsetInfo;  
[optional]  interface IColumnsRowset;  
[optional]  interface IRowsetChange;  
[optional]  interface ISupportErrorInfo;  
};  
```  
  
## <a name="dbtype_table"></a>DBTYPE_TABLE  
 新的類型 DBTYPE_TABLE 代表資料表類型。 這個類型會在需要 DBTYPE 的各種 OLE DB 介面中指定資料表值參數。  
  
```  
#define DBTYPE_TABLE (143)  
```  
  
 DBTYPE_TABLE 與 DBTYPE_IUNKNOWN 具有相同的格式。 它是資料緩衝區中物件的指標。 若為繫結中的完整規格，取用者會填滿 DBOBJECT 緩衝區，並將 *iid* 設定為其中一個資料列集物件介面 (IID_IRowset)。 如果繫結中沒有指定任何 DBOBJECT，系統就會採用 IID_IRowset。  
  
 不支援針對任何其他類型在 DBTYPE_TABLE 之間來回轉換。 IConvertType::CanConvert 會針對任何要求的不支援轉換傳回 S_FALSE，但 DBTYPE_TABLE 與 DBTYPE_TABLE 的轉換除外。 這會採用 Command 物件的 DBCONVERTFLAGS_PARAMETER。  
  
## <a name="methods"></a>方法  
 如需有關支援資料表值參數之 OLE DB 方法的詳細資訊，請參閱 [OLE DB 資料表值參數類型支援 &#40;方法&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md)。  
  
## <a name="properties"></a>屬性  
 如需支援資料表值參數之 OLE DB 屬性的詳細資訊，請參閱 [OLE DB 資料表值參數類型支援 &#40;屬性&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料表值參數 &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [使用資料表值參數 &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
