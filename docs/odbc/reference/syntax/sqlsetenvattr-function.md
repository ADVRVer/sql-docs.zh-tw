---
title: SQLSetEnvAttr 函數 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLSetEnvAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetEnvAttr
helpviewer_keywords:
- SQLSetEnvAttr function [ODBC]
ms.assetid: 0343241c-4b15-4d4b-aa2b-2e8ab5215cd2
caps.latest.revision: 38
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f0593bf413a9d3341927f8108df4e6a490efa927
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetenvattr-function"></a>SQLSetEnvAttr 函數
**一致性**  
 版本引進了： ODBC 3.0 版的標準相容性： ISO 92  
  
 **摘要**  
 **SQLSetEnvAttr**設定管理環境的層面的屬性。  
  
## <a name="syntax"></a>語法  
  
```  
  
SQLRETURN SQLSetEnvAttr(  
     SQLHENV      EnvironmentHandle,  
     SQLINTEGER   Attribute,  
     SQLPOINTER   ValuePtr,  
     SQLINTEGER   StringLength);  
```  
  
## <a name="arguments"></a>引數  
 *EnvironmentHandle*  
 [輸入]環境控制代碼。  
  
 *屬性*  
 [輸入]若要設定，屬性列在 [意見]。  
  
 *ValuePtr*  
 [輸入]要與相關聯的值指標*屬性*。 值而定*屬性*， *ValuePtr*會是 32 位元整數值，或指向以 null 結束的字元字串。  
  
 *stringLength*  
 [輸入]如果*ValuePtr*指向字元字串或二進位的緩衝區，這個引數應該是長度 **ValuePtr*。 字元字串資料，這個引數應該包含在字串中的位元組數目。  
  
 如果*ValuePtr*是整數， *StringLength*會被忽略。  
  
## <a name="returns"></a>傳回值  
 SQL_SUCCESS、 SQL_SUCCESS_WITH_INFO、 SQL_ERROR 或 SQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診斷  
 當**SQLSetEnvAttr**會傳回 SQL_ERROR 或 SQL_SUCCESS_WITH_INFO，相關聯的 SQLSTATE 值可以藉由呼叫取得**SQLGetDiagRec**與*HandleType* SQL_ 的HANDLE_ENV 和*處理*的*EnvironmentHandle*。 下表列出通常所傳回的 SQLSTATE 值**SQLSetEnvAttr** ，並說明這個函式; 每個內容中的標記法 」 (DM) 」 之前描述的驅動程式管理員傳回的 Sqlstate。 每個 SQLSTATE 值相關聯的傳回碼是 SQL_ERROR，除非有說明，否則為。 如果驅動程式不支援的環境屬性，則可以傳回的錯誤，只在連接時間。  
  
|SQLSTATE|錯誤|Description|  
|--------------|-----------|-----------------|  
|01000|一般警告|特定驅動程式告知性訊息。 （函式會傳回 SQL_SUCCESS_WITH_INFO）。|  
|01S02|選項值已變更|驅動程式不支援指定的值*ValuePtr*置換相似的值。 （函式會傳回 SQL_SUCCESS_WITH_INFO）。|  
|HY000|一般錯誤|發生錯誤，其中沒有任何特定的 SQLSTATE 和定義沒有實作特定的 SQLSTATE。 所傳回的錯誤訊息**SQLGetDiagRec**中 *\*MessageText*緩衝區描述錯誤和其原因。|  
|HY001|記憶體配置錯誤|驅動程式無法配置記憶體，才能支援執行或完成的函式。|  
|HY009|無效的 null 指標使用|屬性引數所識別的環境屬性需要字串值，而*ValuePtr*引數為 null 指標。|  
|HY010|函數順序錯誤|(DM) 上已配置連接控制代碼*EnvironmentHandle*。<br /><br /> (DM) **SQL_ATTR_ODBC_VERSION**尚未設定與**SQLSetEnvAttr**和*屬性*不等於**SQL_ATTR_ODBC_VERSION**。 您不需要設定**SQL_ATTR_ODBC_VERSION**明確如果您使用**SQLAllocHandleStd**。|  
|HY013|記憶體管理錯誤|無法處理函式呼叫，因為基礎記憶體的物件無法存取，可能是因為記憶體不足。|  
|HY024|屬性值無效|提供給指定*屬性*值，指定了無效的值中*ValuePtr*。|  
|HY090|字串或緩衝區長度無效|*StringLength*引數為小於 0，但不是 SQL_NTS。|  
|HY092|屬性/選項識別碼無效|(DM) 指定的引數的值*屬性*對 ODBC 驅動程式支援的版本無效。|  
|HY117|連接已暫止原因未知的交易狀態。 只有中斷連線，並允許唯讀函式。|(DM) 如需暫停狀態的詳細資訊，請參閱[SQLEndTran 函數](../../../odbc/reference/syntax/sqlendtran-function.md)。|  
|HYC00|未實作選擇性功能|指定的引數的值*屬性*的 ODBC 版本支援的驅動程式，但不支援此驅動程式是有效的 ODBC 環境屬性。<br /><br /> (DM)*屬性*引數以前是 SQL_ATTR_OUTPUT_NTS，和*ValuePtr*已 SQL_FALSE。|  
  
## <a name="comments"></a>註解  
 應用程式可以呼叫**SQLSetEnvAttr**只有當沒有連接控制代碼會在環境上配置。 已成功設定應用程式環境的所有環境屬性會一直都保存到**SQLFreeHandle**環境上呼叫。 可以同時配置一個以上的環境控制代碼，在 ODBC 3 *.x*。  
  
 透過設定資訊的格式*ValuePtr*取決於指定*屬性*。 **SQLSetEnvAttr**會接受屬性中有兩種不同格式的資訊： null 結尾字元字串或 32 位元整數值。 每個格式註屬性的描述中。  
  
 沒有驅動程式專屬環境屬性。  
  
 無法呼叫所設定的連接屬性**SQLSetEnvAttr**。 嘗試執行這項操作會傳回 SQLSTATE HY092 （無效的屬性/選項識別碼）。  
  
|*屬性*|*ValuePtr*內容|  
|-----------------|-------------------------|  
|SQL_ATTR_CONNECTION_POOLING (ODBC 3.8)|啟用或停用連接共用環境層級的 32 位元 SQLUINTEGER 值。 使用下列值：<br /><br /> SQL_CP_OFF = 連接共用已關閉。 這是預設值。<br /><br /> SQL_CP_ONE_PER_DRIVER = 單一連接集區支援每個驅動程式。 集區中的每個連接都與一個驅動程式。<br /><br /> SQL_CP_ONE_PER_HENV = 單一連接集區支援的每個環境。 集區中的每個連接都與一個環境。<br /><br /> SQL_CP_DRIVER_AWARE = 使用連接集區感知功能的驅動程式時，如果有的話。 如果驅動程式不支援連接集區感知，SQL_CP_DRIVER_AWARE 會被忽略，且 SQL_CP_ONE_PER_HENV。 如需詳細資訊，請參閱[感知驅動程式的連接共用](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)。 其中有些驅動程式支援，而且有些驅動程式不支援連接集區感知的環境中 SQL_CP_DRIVER_AWARE 可以連接集區認知上啟用功能是支援的驅動程式，但它相當於 SQL_CP_ONE_PER_HENV 上的設定不支援連接集區感知功能的驅動程式。<br /><br /> 藉由呼叫會啟用連接共用**SQLSetEnvAttr** SQL_CP_ONE_PER_DRIVER 或 SQL_CP_ONE_PER_HENV 設定 SQL_ATTR_CONNECTION_POOLING 屬性。 應用程式配置共用的連接共用是啟用的環境之前，必須進行這個呼叫。 環境中的控制代碼呼叫**SQLSetEnvAttr**設為 null，讓 SQL_ATTR_CONNECTION_POOLING 處理序層級屬性。 接著，應用程式會啟用連接共用之後，會將隱含的共用的環境配置藉由呼叫**SQLAllocHandle**與*InputHandle*引數設定為 SQL_HANDLE_ENV。<br /><br /> 已啟用連接共用，而且共用的環境中已選取的應用程式之後，SQL_ATTR_CONNECTION_POOLING 無法重設為該環境中，因為**SQLSetEnvAttr**稱為 null 環境設定此屬性時的控制代碼。 如果這個屬性設定在共用環境中已啟用連接共用時，這個屬性會影響後續配置只共用的環境。<br /><br /> 它也可啟用連接共用的環境。 請注意下列有關環境連接共用的資訊：<br /><br /> -啟用連接共用上的 NULL 控制代碼是處理序層級屬性。 後續配置的環境將共用的環境中，而且將會繼承處理序層級連接共用設定。<br />-配置環境之後，應用程式仍然可以變更其連接集區設定。<br />-如果環境連接共用已啟用，連線的驅動程式使用驅動程式共用環境共用接受喜好設定。<br /><br /> SQL_ATTR_CONNECTION_POOLING 被實作在驅動程式管理員。 驅動程式不需要實作 SQL_ATTR_CONNECTION_POOLING。 ODBC 2.0 和 3.0 版的應用程式可以將此環境屬性。<br /><br /> 如需詳細資訊，請參閱[ODBC 連接共用](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)。|  
|SQL_ATTR_CP_MATCH (ODBC 3.0)|32 位元 SQLUINTEGER 值會決定如何從連接集區中選擇連接。 當**SQLConnect**或**SQLDriverConnect**是呼叫，驅動程式管理員會決定哪一個連接從集區中重複使用。 驅動程式管理員嘗試比對呼叫和集區中的關鍵字和連接屬性連接的應用程式時所設定的連接屬性中的連接選項。 這個屬性的值決定比對準則的有效位數層的級。<br /><br /> 下列的值可用來設定這個屬性的值：<br /><br /> SQL_CP_STRICT_MATCH = 只有完全符合連接選項，在呼叫中的連接和應用程式所設定的屬性會重複使用的連接。 這是預設值。<br /><br /> SQL_CP_RELAXED_MATCH = 符合連接字串關鍵字可用的連線。 關鍵字必須相符，但並非所有的連接屬性都必須相符。<br /><br /> 如需驅動程式管理員連接到共用的連接所執行的比對的詳細資訊，請參閱[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)。 如需連接共用的詳細資訊，請參閱[ODBC 連接共用](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)。|  
|SQL_ATTR_ODBC_VERSION (ODBC 3.0)|32 位元的整數會決定特定的功能是否表現 ODBC 2 *.x*行為或 ODBC 3 *.x*行為。 下列的值可用來設定這個屬性的值：<br /><br /> SQL_OV_ODBC3_80 = 驅動程式管理員和驅動程式展示下列 ODBC 3.8 行為：<br /><br /> -驅動程式傳回，而且預期 ODBC 3。*x*日期、 時間和時間戳記的代碼。<br />-驅動程式會傳回 ODBC 3。*x* SQLSTATE 代碼時**SQLError**， **SQLGetDiagField**，或**SQLGetDiagRec**呼叫。<br />- *CatalogName*呼叫中的引數**SQLTables**接受之搜尋模式。<br />-驅動程式管理員支援 C 資料類型擴充性。 如需 C 資料類型擴充性的詳細資訊，請參閱[ODBC 中的 C 資料類型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)。<br /><br /> 如需詳細資訊，請參閱[What's New in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)。<br /><br /> SQL_OV_ODBC3 = 驅動程式管理員和驅動程式展示下列 ODBC 3 *.x*行為：<br /><br /> 的傳回驅動程式，並且預期會 ODBC 3 *.x*日期、 時間和時間戳記的代碼。<br />-驅動程式會傳回 ODBC 3 *.x* SQLSTATE 代碼時**SQLError**， **SQLGetDiagField**，或**SQLGetDiagRec**呼叫。<br />- *CatalogName*呼叫中的引數**SQLTables**接受之搜尋模式。<br />-驅動程式管理員不支援 C 資料類型擴充性。<br /><br /> SQL_OV_ODBC2 = 驅動程式管理員和驅動程式展示下列 ODBC 2 *.x*行為。 這是特別適用於 ODBC 2 *.x*應用程式使用 ODBC 3 *.x*驅動程式。<br /><br /> 的傳回驅動程式，並且預期會 ODBC 2 *.x*日期、 時間和時間戳記的代碼。<br />-驅動程式會傳回 ODBC 2 *.x* SQLSTATE 代碼時**SQLError**， **SQLGetDiagField**，或**SQLGetDiagRec**呼叫。<br />- *CatalogName*呼叫中的引數**SQLTables**不接受之搜尋模式。<br />-驅動程式管理員不支援 C 資料類型擴充性。<br /><br /> 應用程式必須設定此環境的屬性，然後呼叫任何函式具有 SQLHENV 引數，或呼叫會傳回 SQLSTATE HY010 （函數順序錯誤）。 它是驅動程式特有的其他行為是否存在這些環境的旗標。<br /><br /> -如需詳細資訊，請參閱[宣告應用程式的 ODBC 版本](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md)和[的行為變更](../../../odbc/reference/develop-app/behavioral-changes.md)。|  
|SQL_ATTR_OUTPUT_NTS (ODBC 3.0)|32 位元整數，決定如何將驅動程式傳回字串資料。 如果 SQL_TRUE，驅動程式會傳回 null 結束的字串資料。 如果 SQL_FALSE，驅動程式不會傳回 null 結束的字串資料。<br /><br /> 這個屬性預設為 SQL_TRUE。 呼叫**SQLSetEnvAttr**將它設定為 SQL_TRUE 都會傳回 SQL_SUCCESS。 呼叫**SQLSetEnvAttr**將它設定為 SQL_FALSE 傳回 SQL_ERROR 並 SQLSTATE HYC00 （未實作的選擇性功能）。|  
  
## <a name="related-functions"></a>相關函數  
  
|如需詳細資訊|請參閱|  
|---------------------------|---------|  
|配置控制代碼|[SQLAllocHandle 函式](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|傳回環境屬性的設定|[SQLGetEnvAttr 函式](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|  
  
## <a name="see-also"></a>另請參閱  
 [ODBC 應用程式開發介面參考](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC 標頭檔](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC 3.8 的新功能](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
