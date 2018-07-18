---
title: 日期和時間改善 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5761eec08e0e76abd7b9e79e6c0730c8d8af836d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37422257"
---
# <a name="date-and-time-improvements-odbc"></a>日期和時間改善 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 導入了新的日期和時間資料類型。 本章節描述如何將這些新類型公開為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 中的延伸模組。 如需概觀[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client 支援新的日期和時間資料類型，請參閱[日期和時間改善](../../relational-databases/native-client/features/date-and-time-improvements.md)。 如需示範 ODBC 日期/時間支援的範例，請參閱 <<c0> [ 使用日期和時間類型](../../relational-databases/native-client-odbc-how-to/use-date-and-time-types.md)。  
  
 一般日期和時間資料類型的詳細資訊，請參閱[datetime &#40;TRANSACT-SQL&#41;](../../t-sql/data-types/datetime-transact-sql.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [資料類型對 ODBC 日期和時間支援的改善](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 提供有關支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期和時間資料類型之 ODBC 類型的資訊。  
  
 [中繼資料&#40;ODBC&#41;](http://msdn.microsoft.com/library/99133efc-b1f2-46e9-8203-d90c324a8e4c)  
 描述在實作參數描述項 (IPD) 和實作資料列描述項 (IRD) 欄位，以及所傳回的資料行中繼資料中傳回的資訊**SQLColumns**和**SQLProcedureColumns**. 也會說明所傳回的資料型別中繼資料**SQLGetTypeInfo**。  
  
 [datetime 資料類型轉換&#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-odbc.md)  
 描述如何在 datetime 和 datetimeoffset 值之間轉換。  
  
 [日期和時間類型的 sql_variant 支援](../../relational-databases/native-client-odbc-date-time/sql-variant-support-for-date-and-time-types.md)  
 描述 SQL_VARIANT 函數對日期和時間增強功能的支援。  
  
 [大量複製變更增強型的日期和時間型別&#40;OLE DB 和 ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 描述可支援大量複製作業的日期/時間增強功能。  
  
 [增強型的日期和時間類型行為與舊版 SQL Server &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 描述當使用日期和時間增強功能的用戶端應用程式與舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 進行通訊時，以及使用舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 編譯的用戶端將命令傳送到支援日期和時間增強功能的伺服器時，將會發生的預期行為。  
  
 [增強型日期和時間功能的 ODBC API 支援](../../relational-databases/native-client-odbc-date-time/odbc-api-support-for-enhanced-date-and-time-features.md)  
 列出支援日期和時間增強功能的 ODBC 函數。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
