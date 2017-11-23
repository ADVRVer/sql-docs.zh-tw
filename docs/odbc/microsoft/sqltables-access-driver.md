---
title: "SQLTables （存取驅動程式） |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLTables function [ODBC], Access Driver
- Access driver [ODBC], SQLTables
ms.assetid: 94423cf9-341a-4db6-bb10-8f5448df7fc3
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a14293bf4dcbe8e0c6f968a8a020475bfd4d8f1c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2017
---
# <a name="sqltables-access-driver"></a>SQLTables （存取驅動程式）
> [!NOTE]  
>  本主題提供存取驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC 應用程式開發介面參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
|引數|註解|  
|--------------|--------------|  
|*szTableOwner*|唯一有效的引數，如*szTableOwner*是 NULL，因為沒有驅動程式支援擁有者名稱。 與*szTableOwner*設為 NULL，會傳回所有資料表。 TABLE_OWNER 資料行就會傳回 NULL。|  
|*szTableQualifier*|TABLE_QUALIFIER 資料行中**SQLTables**會傳回資料庫檔案的路徑。|  
|*SzTableType*|使用 Microsoft Access 驅動程式時，才支援 「 系統資料表 」 *szTableType*附加的資料表，用於系統資料表支援 「 同義字 」 和 「 檢視 」，支援傳回資料列的查詢。|  
  
## <a name="see-also"></a>請參閱＜  
 [SQLTables 函式](../../odbc/reference/syntax/sqltables-function.md)
