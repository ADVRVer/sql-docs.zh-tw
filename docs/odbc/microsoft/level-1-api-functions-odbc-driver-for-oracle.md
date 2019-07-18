---
title: 層級 1 API 函式 (ODBC Driver for Oracle) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], ODBC driver for Oracle
- ODBC level 1 API functions [ODBC]
- ODBC driver for Oracle [ODBC], functions
- level 1 API functions [ODBC]
- API functions [ODBC]
ms.assetid: 98cced6f-41b8-43c1-a3cd-f4ea1615c0af
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cb1771f88987073b1ef0bcc106f8de28549affe6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085467"
---
# <a name="level-1-api-functions-odbc-driver-for-oracle"></a>層級 1 API 函式 (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  Windows 的未來版本將移除這項功能。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 相反地，使用所提供的 ODBC 驅動程式。  
  
 在此層級提供核心介面一致性的函式，再加上額外的功能，例如交易支援。  
  
|API 函式|注意|  
|------------------|-----------|  
|**SQLColumns**|建立結果集的資料表，也就是指定之資料表的資料行清單或資料表。 當您要求的公用同義字的資料行時，您必須設定 SYNONYMCOLUMNS 連接屬性，而且指定為空字串*szTableOwner*引數。 在傳回的公用同義字的資料行時，驅動程式會設定資料表名稱 資料行設為空字串。 結果集包含額外的資料行序數位置，每個資料列的結尾。 這個值是資料表中的資料行的序數位置。|  
|**SQLDriverConnect**|連接到現有的資料來源。 如需詳細資訊，請參閱 <<c0> [ 連接字串格式和屬性](../../odbc/microsoft/connection-string-format-and-attributes.md)。|  
|**SQLGetConnectOption**|傳回目前連接選項的設定。 此函式僅部分支援。 此驅動程式支援的所有值*fOption*引數，但不支援部分*vParam*值*fOption*引數[SQL_TXN_ISOLATION](../../odbc/microsoft/connect-options.md). 如需詳細資訊，請參閱 <<c0> [ 連接選項](../../odbc/microsoft/connect-options.md)。|  
|**SQLGetData**|擷取指定的結果集的目前記錄中的單一欄位的值。|  
|**SQLGetFunctions**|傳回所有支援的函式，則為 TRUE。 實作由驅動程式管理員。|  
|**SQLGetInfo**|傳回資訊，包括 SQLHDBC、 SQLUSMALLINT、 SQLPOINTER、 SQLSMALLINT 和 SQLSMALLINT \*，有關 ODBC Driver for Oracle 和資料來源連接控制代碼相關聯*hdbc*。|  
|**SQLGetStmtOption**|傳回目前的陳述式選項的設定。 如需詳細資訊，請參閱 <<c0> [ 陳述式選項](../../odbc/microsoft/statement-options.md)。|  
|**SQLGetTypeInfo**|傳回資料來源所支援的資料類型的相關資訊。 驅動程式中的 SQL 結果集傳回的資訊。|  
|**SQLParamData**|用於搭配**SQLPutData**來指定參數資料在陳述式執行階段。|  
|**SQLPutData**|允許應用程式將參數或資料行的資料傳送到在陳述式執行階段的驅動程式。|  
|**SQLSetConnectOption**|提供存取權管理許多層面之連接的選項。 此函式僅部分支援：此驅動程式支援的所有值*fOption*引數，但不支援部分*vParam*值*fOption*引數[SQL_TXN_ISOLATION](../../odbc/microsoft/connect-options.md). 如需詳細資訊，請參閱 <<c0> [ 連接選項](../../odbc/microsoft/connect-options.md)。|  
|**SQLSetStmtOption**|設定與陳述式控制代碼相關的選項*hstmt*。 如需詳細資訊，請參閱 <<c0> [ 陳述式選項](../../odbc/microsoft/statement-options.md)。|  
|**SQLSpecialColumns**|擷取一組最佳的資料行可唯一識別資料表中的資料列。|  
|**SQLStatistics**|擷取單一的資料表和索引或與資料表相關聯的標記名稱相關的統計資料的清單。 驅動程式會傳回資訊當作結果集。|  
|**SQLTables**|傳回清單中的參數所指定的資料表名稱**SQLTables**陳述式。 如果未不指定任何參數，會傳回儲存在目前的資料來源中的資料表名稱。 驅動程式會傳回資訊當作結果集。<br /><br /> 列舉型別呼叫將不會收到遠端檢視或本機的參數化的檢視的結果集項目。 不過，呼叫**SQLTables**與唯一的資料表名稱規範會找不到這類檢視中，如果有的話，具有該名稱，這可讓 API 來檢查是否有名稱衝突，再建立新的資料表。<br /><br /> 公用的同義字會傳回 TABLE_OWNER 值為""。<br /><br /> SYS 或系統所擁有的檢視表會識別為系統檢視表。|
