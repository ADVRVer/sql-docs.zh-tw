---
title: LINKEDSERVERS 資料列集（OLE DB） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
ms.assetid: 2633fd8a-65e7-498d-9aed-8e4b1cca2381
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3a109f663ade5c1b52f9e6d6ca9cd83efac4b3ec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "73759358"
---
# <a name="schema-rowsets---linkedservers-rowset"></a>結構描述資料列集 - LINKEDSERVERS 資料列集
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  
  **LINKEDSERVERS** 資料列集會列舉可以參與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散式查詢的組織資料來源。  
  
 
  **LINKEDSERVERS** 資料列集包含下列資料行。  
  
|資料行名稱|類型指標|描述|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|連結伺服器的名稱。|  
|SVR_PRODUCT|DBTYPE_WSTR|製造商或是識別由連結伺服器名稱表示之資料存放區類型的其他名稱。|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|用來耗用伺服器中之資料的 OLE DB 提供者易記名稱。|  
|SVR_DATASOURCE|DBTYPE_WSTR|用來從提供者當中取得資料來源的 OLE DB DBPROP_INIT_DATASOURCE 字串。|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|用來從提供者當中取得資料來源的 OLE DB DBPROP_INIT_PROVIDERSTRING 值。|  
|SVR_LOCATION|DBTYPE_WSTR|用來從提供者當中取得資料來源的 OLE DB DBPROP_INIT_LOCATION 字串。|  
  
 資料列集會根據 SRV_NAME 排序，而且 SRV_NAME 上可支援單一限制。  
  
## <a name="see-also"></a>另請參閱  
 [架構資料列集支援 &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/schema-rowset-support-ole-db.md)  
  
  
