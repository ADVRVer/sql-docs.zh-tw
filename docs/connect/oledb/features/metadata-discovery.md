---
title: 中繼資料探索 | Microsoft Docs
description: OLE DB Driver for SQL Server 中的中繼資料探索
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 9891e5708110be83a4ef33cb2a142accaf93ffe2
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2020
ms.locfileid: "67989058"
---
# <a name="metadata-discovery"></a>中繼資料探索
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中的中繼資料探索改進可讓 OLE DB Driver for SQL Server 應用程式確保執行查詢時所傳回的資料行或參數中繼資料，與您在執行查詢之前指定的中繼資料格式完全相同或相容。 如果查詢執行之後傳回的中繼資料與您在查詢執行之前指定的中繼資料格式不相容，您就會收到錯誤。  
  
 在 bcp 以及 IBCPSession 和 IBCPSession2 介面中，您現在可以指定延遲讀取 (延遲中繼資料探索)，避免針對查詢輸出作業進行中繼資料探索。 這樣做可改善效能並排除中繼資料探索失敗。  
  
 如果您使用 OLE DB Driver for SQL Server 來開發應用程式，但卻連接至 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 之前的伺服器版本，則中繼資料探索功能將對應至該伺服器的版本。  
  
## <a name="remarks"></a>備註   
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 已經強化了下列 OLE DB 成員函數，以便提供改良的中繼資料探索：  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters::GetParameterInfo (如需詳細資訊，請參閱 [ICommandWithParameters](../../oledb/ole-db-interfaces/icommandwithparameters.md))  
  
 當您使用 IBCPSession::BCPSetBulkMode 來指定中繼資料格式時，也會看見效能改進  
  
 由於 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 加入了下列兩個預存程序，所以您可以在 OLE DB Driver for SQL Server 中進行改善的中繼資料探索：  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB Driver for SQL Server 功能](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
