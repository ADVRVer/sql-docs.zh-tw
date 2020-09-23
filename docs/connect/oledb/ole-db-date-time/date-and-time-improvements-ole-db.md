---
title: 日期和時間改善 (OLE DB) | Microsoft Docs
description: 這些文章描述 OLE DB Driver for SQL Server 如何支援新的日期和時間資料類型。 查看概觀與範例。
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cd0f564a68f0b296008907f8620cd870c0e5ca7d
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862032"
---
# <a name="date-and-time-improvements-ole-db"></a>日期和時間改善 (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 導入了新的日期和時間資料類型。 本節描述如何將這些新類型公開為 OLE DB Driver for SQL Server 中的擴充功能。 如需 OLE DB Driver for SQL Server 對新日期和時間資料類型之支援的概觀，請參閱[日期和時間改善](../../oledb/features/date-and-time-improvements.md)。 如需範例，請參閱[使用增強型日期和時間功能 &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md)。  
  
 如需更多日期和時間資料類型的一般資訊，請參閱 [datetime &#40;Transact-SQL&#41;](../../../t-sql/data-types/datetime-transact-sql.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [對 OLE DB 日期和時間改善的資料類型支援](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 提供有關支援 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 日期/時間資料類型之 OLE DB (OLE DB Driver for SQL Server) 類型的資訊。  
  
 [中繼資料 &#40;OLE DB&#41;](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)  
 包含 DBBINDING 結構、**ICommandWithParameters::GetParameterInfo**、**ICommandWithParameters::SetParameterInfo**、**IColumnsRowset::GetColumnsRowset** 及 I**ColumnsInfo::GetColumnInfo** 的相關資訊。 同時提供有關 OLE DB 結構描述資料列集更新的資訊。  
  
 [繫結和轉換 &#40;OLE DB&#41;](../../oledb/ole-db-date-time/conversions-ole-db.md)  
 描述在伺服器和用戶端之間，針對現有日期類型和新日期類型進行轉換的規則。  
  
 [增強型日期和時間類型的大量複製變更 &#40;OLE DB&#41;](../../oledb/ole-db-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db.md)  
 描述可支援大量複製作業的日期/時間增強功能。  
  
 [OLE DB API 對日期和時間增強功能的支援](../../oledb/ole-db-date-time/ole-db-api-support-for-date-and-time-enhancements.md)  
 描述支援日期/時間增強功能的 OLE DB API。  
  
 [IRowsetFind 的相容性](../../oledb/ole-db-date-time/comparability-for-irowsetfind.md)  
 描述日期/時間類型和 **IRowsetFind**。  
 
  
## <a name="see-also"></a>另請參閱  
 [OLE DB Driver for SQL Server 程式設計](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
