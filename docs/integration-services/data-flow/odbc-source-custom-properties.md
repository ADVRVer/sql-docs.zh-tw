---
title: "ODBC 來源自訂屬性 |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 362bbcd8-b7b0-4bab-8afe-1212b2ad1af9
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 15c78bdb8f093b07ce62a7d710ba583aad96548d
ms.contentlocale: zh-tw
ms.lasthandoff: 08/03/2017

---
# <a name="odbc-source-custom-properties"></a>ODBC 來源自訂屬性
  下表將描述 ODBC 來源的自訂屬性。 所有屬性都可從 SSIS 屬性運算式設定。  
  
|屬性名稱|資料類型|說明|  
|-------------------|---------------|-----------------|  
|連接|ODBC 連接|用來存取來源資料庫的 ODBC 連接。|  
|AccessMode|整數 (列舉)|用來存取資料庫的模式。 可能值為資料表名稱 (0) 和 SQL 命令(1)。<br /><br /> 預設值為資料表名稱 (0)。|  
|BatchSize|Integer|大量擷取的批次大小。 這是當做陣列擷取的記錄數目。 如果選定的 ODBC 提供者不支援陣列，批次大小為 1。|  
|BindCharColumnAs|整數 (列舉)|此屬性決定 ODBC 來源如何繫結具有多位元組字串類型 (如 SQL_CHAR、SQL_VARCHAR 或 SQL_LONGVARCHAR) 的資料行。<br /><br /> 可能值為 Unicode (0) 和 ANSI (1)。前者繫結 SQL_C_WCHAR 等資料行，後者則繫結 SQL_C_CHAR 等資料行。 預設值為 Unicode (0)。<br /><br /> **注意**：雖然您無法在 **[ODBC 來源編輯器]**中使用這個屬性，但是可以使用 **[進階編輯器]**來設定這個屬性。|  
|BindNumericAs|整數 (列舉)|此屬性決定 ODBC 來源如何繫結具有 SQL_TYPE_NUMERIC 和 SQL_TYPE_DECIMAL 資料類型之數值資料的資料行。<br /><br /> 可能的選項為 Char (0) 和 Numeric (1)。前者繫結 SQL_C_CHAR 等資料行，後者則繫結 SQL_C_NUMERIC 等資料行。 預設值為 Char (0)。<br /><br /> **注意**：雖然您無法在 **[ODBC 來源編輯器]**中使用這個屬性，但是可以使用 **[進階編輯器]**來設定這個屬性。|  
|DefaultCodePage|Integer|要用於字串輸出資料行的字碼頁。<br /><br /> **注意**：雖然您無法在 **[ODBC 來源編輯器]**中使用這個屬性，但是可以使用 **[進階編輯器]**來設定這個屬性。|  
|ExposeCharColumnsAsUnicode|布林|此屬性決定元件如何公開 CHAR 資料行。 預設值為 False，表示 CHAR 資料行公開為多位元組字串 (DT_STR)。 如果為 True，則 CHAR 資料行公開為寬字元字串 (DT_WSTR)。<br /><br /> **注意**：雖然您無法在 **[ODBC 來源編輯器]**中使用這個屬性，但是可以使用 **[進階編輯器]**來設定這個屬性。|  
|FetchMethod|整數 (列舉)|用於取得資料的方法。 可能的選項為逐列 (0) 和批次 (1)。 預設值為批次 (1)。<br /><br /> 如需這些選項的詳細資訊，請參閱 [ODBC Source](../../integration-services/data-flow/odbc-source.md)。<br /><br /> **注意**：雖然您無法在 **[ODBC 來源編輯器]**中使用這個屬性，但是可以使用 **[進階編輯器]**來設定這個屬性。|  
|SqlCommand|字串|當 AccessMode 設為 [SQL 命令] 時要執行的 SQL 命令。|  
|StatementTimeout|Integer|在傳回至應用程式並出現錯誤之前等候 SQL 陳述式執行的秒數。 預設值為 120。 值為 0 表示系統不會逾時。|  
|TableName|字串|當 AccessMode 設為 [資料表名稱] 時所使用之資料的資料表名稱。|  
|LobChunckSize|Integer|LOB 資料行的區塊大小配置。|  
||||  
  
## <a name="see-also"></a>請參閱＜  
 [ODBC 來源](../../integration-services/data-flow/odbc-source.md)   
 [ODBC 來源編輯器 &#40;連接管理員頁面 &#41;](../../integration-services/data-flow/odbc-source-editor-connection-manager-page.md)  
  
  
