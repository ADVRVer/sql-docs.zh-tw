---
title: OLE DB 資料表值參數類型支援 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
ms.assetid: 147036a0-260e-4f81-8b3b-89209e023a32
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 73d391bcd0cd5476c9c494606e8215e6a96afb42
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421947"
---
# <a name="ole-db-table-valued-parameter-type-support"></a>OLE DB 資料表值參數類型支援
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  本主題描述資料表值參數的 OLE DB 類型支援。  
  
## <a name="table-valued-parameter-rowset-object"></a>資料表值參數資料列集物件  
 您可以針對資料表值參數建立專用的資料列集物件。 您可以使用 ITableDefinitionWithConstraints::CreateTableWithConstraints 或 iopenrowset:: Openrowset，以建立資料表值參數資料列集物件。 若要這樣做，請設定*eKind*隸屬*pTableID*參數為 DBKIND_GUID_NAME，並提供 CLSID_ROWSET_INMEMORY 當做*guid*成員。 資料表值參數的伺服器類型名稱必須指定在*pwszName*隸屬*pTableID*使用 iopenrowset:: Openrowset 時。 資料表值參數資料列集物件的行為就如同一般 SQL Server Native Client OLE DB 提供者物件。  
  
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
  
## <a name="dbtypetable"></a>DBTYPE_TABLE  
 新的類型 DBTYPE_TABLE 代表資料表類型。 這個類型會在需要 DBTYPE 的各種 OLE DB 介面中指定資料表值參數。  
  
```  
#define DBTYPE_TABLE (143)  
```  
  
 DBTYPE_TABLE 與 DBTYPE_IUNKNOWN 具有相同的格式。 它是資料緩衝區中物件的指標。 如需繫結中的完整規格，取用者會填滿 DBOBJECT 緩衝區，與*iid*設為其中一個資料列集物件介面 (IID_IRowset)。 如果繫結中不指定任何 DBOBJECT，則會假設 IID_IRowset。  
  
 不支援針對任何其他類型在 DBTYPE_TABLE 之間來回轉換。 IConvertType::CanConvert 會針對任何要求 dbtype_table 與 DBTYPE_TABLE 的轉換的不支援轉換傳回 S_FALSE。 這 dbconvertflags_parameter 命令物件。  
  
## <a name="methods"></a>方法  
 如需 OLE DB 方法支援資料表值參數的資訊，請參閱[OLE DB Table-Valued 參數類型支援&#40;方法&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md)。  
  
## <a name="properties"></a>屬性  
 如需 infornation 有關支援資料表值參數的 OLE DB 屬性，請參閱 < [OLE DB Table-Valued 參數類型支援&#40;屬性&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料表值參數&#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [使用資料表值參數&#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
