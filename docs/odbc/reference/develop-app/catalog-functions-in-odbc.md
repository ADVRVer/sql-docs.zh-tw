---
title: "目錄函數在 ODBC |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- catalog functions [ODBC], listed
- functions [ODBC], catalog functions
ms.assetid: 4f28f557-7eca-4905-aa6d-45a6cf501a66
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 74b86dfd62a12938d18b4aa11a8d0502db50da13
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="catalog-functions-in-odbc"></a>在 ODBC 目錄函數
ODBC 包含下列目錄函數：  
  
|函數|Description|  
|--------------|-----------------|  
|**SQLTables**|傳回資料來源中的類別目錄、 結構描述、 資料表或資料表類型的清單。|  
|**SQLColumns**|傳回一或多個資料表中的資料行的清單。|  
|**SQLStatistics**|傳回單一資料表的相關統計資料的清單。 也會傳回一份該資料表相關聯的索引。|  
|**SQLSpecialColumns**|傳回可唯一識別單一資料表中的資料列的資料行清單。 也會自動更新該資料表中傳回資料行的清單。|  
|**SQLPrimaryKeys**|傳回組成單一資料表的主索引鍵資料行的清單。|  
|**SQLForeignKeys**|傳回單一資料表或單一資料表參考其他資料表中的外部索引鍵的清單中的外部索引鍵的清單。|  
|**SQLTablePrivileges**|傳回一個或多個資料表相關聯的權限清單。|  
|**SQLColumnPrivileges**|傳回單一資料表中的一個或多個資料行相關聯的權限清單。|  
|**SQLProcedures**|傳回資料來源中的程序的清單。|  
|**SQLProcedureColumns**|在單一程序的結果集傳回一份輸入和輸出參數、 傳回值，以及資料行。|  
|**SQLGetTypeInfo**|傳回資料來源所支援的 SQL 資料類型的清單。 這些資料類型通常用於**CREATE TABLE**和**ALTER TABLE**陳述式。|  
  
 因為**SQLTables**， **SQLColumns**， **SQLStatistics**，和**SQLSpecialColumns**符合開啟群組 CLI 和**SQLGetTypeInfo**符合 ISO 92 CLI，大多數的驅動程式實作。 其餘的類別目錄函式位於 ODBC 的一致性層級。  
  
 此章節包含下列主題。  
  
-   [目錄函數所傳回的資料](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)  
  
-   [目錄函數中的引數](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)  
  
-   [結構描述檢視](../../../odbc/reference/develop-app/schema-views.md)

