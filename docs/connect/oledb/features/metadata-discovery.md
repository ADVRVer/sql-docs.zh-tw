---
title: 中繼資料探索 |Microsoft 文件
description: OLE DB 驅動程式的 SQL Server 中的中繼資料探索
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 3980b8064b565dc09ebb79e9d81be9c6f85fc21a
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/14/2018
ms.locfileid: "35611633"
---
# <a name="metadata-discovery"></a>中繼資料探索
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  中的中繼資料探索改進[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]可讓 OLE DB 驅動程式的 SQL Server 應用程式，以確保該資料行或參數中繼資料執行查詢所傳回等同於或之前指定相容的中繼資料格式執行查詢。 如果查詢執行之後傳回的中繼資料與您在查詢執行之前指定的中繼資料格式不相容，您就會收到錯誤。  
  
 在 bcp 和 IBCPSession 和 IBCPSession2 介面中，您現在可以指定延遲讀取 （延遲中繼資料探索） 若要避免針對查詢輸出作業的中繼資料探索。 這樣做可改善效能並排除中繼資料探索失敗。  
  
 如果您開發使用 SQL Server 的 OLE DB 驅動程式的應用程式，但連接到伺服器版本早於[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]，中繼資料探索功能將會對應到伺服器的版本。  
  
## <a name="remarks"></a>備註   
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 已經強化了下列 OLE DB 成員函數，以便提供改良的中繼資料探索：  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   Icommandwithparameters:: Getparameterinfo (請參閱[ICommandWithParameters](../../oledb/ole-db-interfaces/icommandwithparameters.md)如需詳細資訊)  
  
 您也會指定使用 IBCPSession::BCPSetBulkMode 的中繼資料格式時看到效能改進  
  
 改良的中繼資料探索，OLE DB 驅動程式的 SQL Server 中，是因為兩個預存程序中加入[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB Driver for SQL Server 功能](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
