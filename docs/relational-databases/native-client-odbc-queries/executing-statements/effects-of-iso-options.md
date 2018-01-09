---
title: "ISO 選項的效果 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-queries
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ISO options (ODBC)
- ODBC applications, ISO options
- ODBC applications, statements
- SQL Server Native Client ODBC driver, ISO options
- statements [ODBC], ISO options
ms.assetid: 813f1397-fa0b-45ec-a718-e13fe2fb88ac
caps.latest.revision: "36"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: affd89006366a2994ee2a420b6a2a789f4e3dc6d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="effects-of-iso-options"></a>ISO 選項的作用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  ODBC 標準與 ISO 標準相當接近，而且 ODBC 應用程式應該是來自 ODBC 驅動程式的標準行為。 若要使其行為更為符合中所定義的 ODBC 標準， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式一律會使用所連接的 SQL Server 版本中提供的任何 ISO 選項。  
  
 當[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式連接到的執行個體[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，伺服器就會偵測用戶端使用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式和幾個選項的集合。  
  
 驅動程式本身會發出這些陳述式；ODBC 應用程式不用做任何事情就可以要求它們。 設定這些選項可以使用驅動程式，讓 ODBC 應用程式更容易攜帶，因為伺服器行為會符合 ISO 標準。  
  
 以 DB-Library 為基礎的應用程式一般不會開啟這些選項。 觀察不同的網站之間 ODBC 或 Db-library 用戶端時執行相同的 SQL 陳述式不應該假設這行為指向問題[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式。 它們應該先傳回陳述式中使用的相同 SET 選項，在 Db-library 環境會使用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式。  
  
 由於使用者和應用程式可以隨時開啟和關閉 SET 選項，因此，預存程序和觸發程序的開發人員也應該在開啟和關閉以上列出的 SET 選項時，小心測試其程序和觸發程序。 無論特定連接叫用程序或觸發程序時已經設定哪些選項，這都可以確保程序和觸發程序能正常運作。 對於需要為這些選項的其中之一進行特定設定的觸發程序或預存程序，應該在觸發程序或預存程序開始時發出 SET 陳述式。 此 SET 陳述式只有在執行觸發程序或預存程序時才有效，當程序或觸發程序結束時，就會還原原始的設定。  
  
 連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體時，也會將第四個 SET 選項，也就是 CONCAT_NULL_YIELDS_NULL，設定為開啟。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式不會設定這些選項則 AnsiNPW = NO 在資料來源，或在指定[SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)或[SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)。  
  
 喜歡前文所述，ISO 選項[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式不會開啟 QUOTED_IDENTIFIER 選項，則 QuotedID = NO 在資料來源，或在指定**SQLDriverConnect**或**SQLBrowseConnect**。  
  
 為了讓驅動程式知道 SET 選項的目前狀態，ODBC 應用程式應該不會使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] SET 陳述式來設定這些選項。 它們應該只會使用資料來源或連接選項設定這些選項。 如果應用程式發出 SET 陳述式，此驅動程式可能會產生不正確的 SQL 陳述式。  
  
## <a name="see-also"></a>請參閱  
 [執行陳述式 &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)   
 [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md)   
 [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)  
  
  
