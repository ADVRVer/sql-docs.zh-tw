---
title: FILESTREAM 支援 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], SQL Server Native Client
- SQL Server Native Client [FILESTREAM support]
ms.assetid: 1ad3400d-7fcd-40c9-87ae-f5afc61e0374
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33e447048f7058ee81b0b144f0aa94a370f6d670
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63046260"
---
# <a name="filestream-support"></a>FILESTREAM 支援
  FILESTREAM 提供透過 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或直接存取 Windows 檔案系統來儲存及存取大型二進位值的方式。 大型二進位值是大於 2 GB 的值。 如需有關增強型 FILESTREAM 支援的詳細資訊，請參閱 < [FILESTREAM &#40;SQL Server&#41;](../../blob/filestream-sql-server.md)。  
  
 當開啟資料庫連接時，`@@TEXTSIZE` 預設會設定為 -1 (無限制)。  
  
 也可以使用 Windows 檔案系統 API 來存取及更新 FILESTREAM 資料行。  
  
 如需詳細資訊，請參閱下列主題：  
  
-   [FILESTREAM 支援&#40;OLE DB&#41;](../ole-db/filestream-support-ole-db.md)  
  
-   [FILESTREAM 支援&#40;ODBC&#41;](../odbc/filestream-support-odbc.md)  
  
-   [使用 OpenSqlFilestream 存取 FILESTREAM 資料](../../blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>查詢是否有 FILESTREAM 資料行  
 OLE DB 中的結構描述資料列集將不會報告某個資料行是否為 FILESTREAM 資料行。 OLE DB 中的 ITableDefinition 不能用來建立 FILESTREAM 資料行。  
  
 目錄函式，例如 ODBC 中的 SQLColumns 將不會報告資料行是否為 FILESTREAM 資料行。  
  
 若要建立 FILESTREAM 資料行或是偵測哪些現有的資料行是 FILESTREAM 資料行，您可以使用`is_filestream`資料行[sys.columns](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql)目錄檢視。  
  
 以下是一個範例：  
  
```  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a>下層相容性  
 如果您的用戶端使用的版本所編譯[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]隨附的原生用戶端[!INCLUDE[ssVersion2005](../../../includes/sscurrent-md.md)]，`varbinary(max)`行為將會與相容[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]。 也就是說，傳回之資料的大小最大值受限於 2 GB。 如果結果值大於 2 GB，將會發生截斷，而且將會傳回「字串資料右邊截斷」警告。  
  
 當資料類型相容性設定為 80 時，用戶端行為將會與下層用戶端行為一致。  
  
 使用 SQLOLEDB 或其他發行前的提供者的用戶端[!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)]Native Client，`varbinary(max)`會對應至映像。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Native Client 功能](sql-server-native-client-features.md)  
  
  
