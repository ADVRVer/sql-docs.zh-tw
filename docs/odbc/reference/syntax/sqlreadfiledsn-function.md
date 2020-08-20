---
description: SQLReadFileDSN 函式
title: SQLReadFileDSN 函式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLReadFileDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLReadFileDSN
helpviewer_keywords:
- SQLReadFileDSN function [ODBC]
ms.assetid: ead464aa-cdc3-47dd-a0c0-997711205d31
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 76f6cdb3dfc423cba4eed6981ce540b5192288e3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487100"
---
# <a name="sqlreadfiledsn-function"></a>SQLReadFileDSN 函式
**一致性**  
 引進的版本： ODBC 3。0  
  
 **總結**  
 **SQLReadFileDSN** 會從檔案 DSN 讀取資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
  
BOOL SQLReadFileDSN(  
     LPCSTR   lpszFileName,  
     LPCSTR   lpszAppName,  
     LPCSTR   lpszKeyName,  
     LPSTR    lpszString,  
     WORD     cbString,  
     WORD *   pcbString);  
```  
  
## <a name="arguments"></a>引數  
 *lpszFileName*  
 輸出資料緩衝區的指標，其中包含該 dsn 檔案的名稱。 .Dsn 副檔名會附加到所有檔案名，而這些檔案名還沒有 .dsn 副檔名。 * \* LpszFileName*中的值必須是以 null 結束的字串。  
  
 *lpszAppName*  
 輸出包含應用程式名稱之資料緩衝區的指標。 這是 ODBC 區段的 "ODBC"。 * \* LpszAppName*中的值必須是以 null 結束的字串。  
  
 *lpszKeyName*  
 輸出資料緩衝區的指標，其中包含要讀取之索引鍵的名稱。 請參閱保留關鍵字的「批註」。 * \* LpszAppName*中的值必須是以 null 結束的字串。  
  
 *lpszString*  
 出資料緩衝區的指標，其中包含與要讀取的索引鍵相關聯的字串。  
  
 如果* \* lpszFileName*是有效的 .dsn 檔案名，但*lpszAppName*引數為 null 指標，且*lpszKeyName*引數為 null 指標，則* \* lpszString*包含有效應用程式的清單。 如果* \* lpszFileName*是有效的 dsn 檔案名，而* \* lpszAppName*是有效的應用程式名稱，但*lpszKeyName*引數為 null 指標，則* \* lpszString*會在 dsn 檔案的適當區段中包含有效的保留關鍵字清單（以分號分隔）。 如果* \* lpszFileName*是有效的 .dsn 檔案名，但* \* lpszAppName*是 null 指標，且*lpszKeyName*引數為 null 指標，則* \* lpszString*會包含 dsn 檔案中的區段清單（以分號分隔）。  
  
 *cbString*  
 輸出* \* LpszString*緩衝區的長度。  
  
 *pcbString*  
 出可在* \* lpszString*中傳回的總位元組數。 如果可傳回的位元組數目大於或等於*cbString*， * \* lpszString*中的輸出字串會截斷為*cbString*減去 null 終止字元。 *PcbString*引數可以是 null 指標。  
  
## <a name="returns"></a>傳回  
 如果成功，函數會傳回 TRUE，否則會傳回 FALSE。  
  
## <a name="diagnostics"></a>診斷  
 當**SQLReadFileDSN**傳回 FALSE 時，可以藉由呼叫**SQLInstallerError**來取得相關聯的* \* pfErrorCode*值。 下表列出可由**SQLInstallerError**傳回的* \* pfErrorCode*值，並在此函式的內容中說明每一個值。  
  
|*\*pfErrorCode*|錯誤|描述|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|一般安裝程式錯誤|發生沒有特定安裝程式錯誤的錯誤。|  
|ODBC_ERROR_INVALID_BUFF_LEN|緩衝區長度無效|*LpszString*引數為 Null。<br /><br /> *CbString*引數小於或等於0。|  
|ODBC_ERROR_INVALID_PATH|不正確安裝路徑|*LpszFileName*引數中指定之檔案名的路徑無效。|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|要求的類型無效|*LpszAppName*引數為 Null，而*lpszKeyName*引數有效。|  
|ODBC_ERROR_OUT_OF_MEM|記憶體不足|因為記憶體不足，所以安裝程式無法執行函數。|  
|ODBC_ERROR_OUTPUT_STRING_TRUNCATED|輸出字串已截斷|* \* LpszString*中傳回的字串已被截斷，因為*cbString*中的值小於或等於* \* pcbString*中的值。|  
|ODBC_ERROR_REQUEST_FAILED|要求失敗|關鍵字不存在於 file DSN 中。|  
  
## <a name="comments"></a>註解  
 ODBC 會保留區段名稱 [ODBC] 以儲存連接資訊。 此區段的保留關鍵字與針對 **SQLDriverConnect**中的連接字串保留的關鍵字相同。  (需詳細資訊，請參閱 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) 函數描述。 )   
  
 應用程式可以使用這些保留的關鍵字來讀取檔案 DSN 中的資訊。 如果應用程式想要找出與檔案 DSN 相關聯的無 DSN 連接字串，它可以針對 [ODBC] 區段中任何保留的連接字串關鍵字呼叫 **SQLReadFileDSN** 。 以無 DSN 連接傳遞的完整連接字串，是 [ODBC] 區段中所有關鍵詞 (保留和驅動程式專用) 的組合。  
  
## <a name="related-functions"></a>相關函數  
  
|如需下列資訊|請參閱|  
|---------------------------|---------|  
|將資訊寫入檔案 DSN|[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|
