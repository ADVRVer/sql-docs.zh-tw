---
description: SQLDriverToDataSource 函式
title: SQLDriverToDataSource 函式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDriverToDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDriverToDataSource
helpviewer_keywords:
- SQLDriverToDataSource function [ODBC]
ms.assetid: 0de28eb5-8aa9-43e4-a87f-7dbcafe800dc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: da885e3be81a7a7de04a58bbb92725317477e80e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461139"
---
# <a name="sqldrivertodatasource-function"></a>SQLDriverToDataSource 函式
**SQLDriverToDataSource** 支援 ODBC 驅動程式的翻譯。 此函式不是由具有 ODBC 功能的應用程式所呼叫;應用程式透過 **SQLSetConnectAttr**要求翻譯。 與**SQLSetConnectAttr**中指定的*ConnectionHandle*相關聯的驅動程式會呼叫指定的 DLL，以執行從驅動程式流向資料來源之所有資料的翻譯。 您可以在 ODBC 初始化檔中指定預設轉譯 DLL。  
  
## <a name="syntax"></a>語法  
  
```cpp  
  
BOOL SQLDriverToDataSource(  
     UDWORD     fOption,  
     SWORD      fSqlType,  
     PTR        rgbValueIn,  
     SDWORD     cbValueIn,  
     PTR        rgbValueOut,  
     SDWORD     cbValueOutMax,  
     SDWORD *   pcbValueOut,  
     UCHAR *    szErrorMsg,  
     SWORD      cbErrorMsgMax,  
     SWORD *    pcbErrorMsg);  
```  
  
## <a name="arguments"></a>引數  
 *fOption*  
 輸出選項值。  
  
 *fSqlType*  
 輸出ODBC SQL 資料類型。 此引數會告知驅動程式如何將 *rgbValueIn* 轉換為數據源可接受的表單。 如需有效 SQL 資料類型的清單，請參閱 [Sql 資料類型](../../../odbc/reference/appendixes/sql-data-types.md)。  
  
 *rgbValueIn*  
 輸出要轉譯的值。  
  
 *cbValueIn*  
 輸出 *RgbValueIn*的長度。  
  
 *rgbValueOut*  
 出轉譯結果。  
  
> [!NOTE]  
>  轉譯 DLL 不會為 null 終止此值。  
  
 *cbValueOutMax*  
 輸出 *RgbValueOut*的長度。  
  
 *pcbValueOut*  
 出 (不包括 null 終止位元組的總位元組數) 可在 *rgbValueOut*中傳回。  
  
 若為字元或二進位資料，如果這大於或等於 *cbValueOutMax*， *rgbValueOut* 中的資料會被截斷為 *cbValueOutMax* 的位元組。  
  
 對於所有其他資料類型，會忽略 *cbValueOutMax* 的值，而轉譯 DLL 會假設 *rgbValueOut* 的大小是以 *fSqlType*指定的 SQL 資料類型之預設 C 資料類型的大小。  
  
 *PcbValueOut*引數可以是 null 指標。  
  
 *szErrorMsg*  
 出錯誤訊息的儲存體指標。 除非轉譯失敗，否則這是空字串。  
  
 *cbErrorMsgMax*  
 輸出 *SzErrorMsg*的長度。  
  
 *pcbErrorMsg*  
 出位元組總數的指標 (不包括 null 終止位元組) 可在 *szErrorMsg*中傳回。 如果這個值大於或等於 *cbErrorMsg*， *szErrorMsg* 中的資料會被截斷為 *cbErrorMsgMax* 減去 null 終止字元。 *PcbErrorMsg*引數可以是 null 指標。  
  
## <a name="returns"></a>傳回  
 如果轉譯成功，則為 TRUE，如果翻譯失敗，則為 FALSE。  
  
## <a name="comments"></a>註解  
 驅動程式會呼叫 **SQLDriverToDataSource** ，以將所有資料轉譯 (SQL 語句、參數等等，) 從驅動程式傳遞至資料來源。 根據資料的類型和轉譯 DLL 的目的，轉譯 DLL 可能無法轉譯一些資料。 例如，將字元資料從某個字碼頁轉譯成另一個字碼頁的 DLL 會忽略所有數值和二進位資料。  
  
 *FOption*的值會設定為使用 SQL_ATTR_TRANSLATE_OPTION 屬性呼叫**SQLSetConnectAttr**所指定的*vParam*值。 它是一個32位值，對指定的轉譯 DLL 具有特定意義。 例如，它可以指定特定字元集轉譯。  
  
 如果為 *rgbValueIn* 和 *rgbValueOut*指定相同的緩衝區，就會就地執行緩衝區中的資料轉譯。  
  
 雖然 *cbValueIn*、 *cbValueOutMax*和 *PCBVALUEOUT* 的型別為 SDWORD，但是 **SQLDriverToDataSource** 不一定支援大型指標。  
  
 如果 **SQLDriverToDataSource** 傳回 FALSE，轉譯期間可能會發生資料截斷。 如果 *pcbValueOut* (可在輸出緩衝區中傳回的位元組數目) 大於 *cbValueOutMax* (輸出緩衝區) 的長度，則會發生截斷。 驅動程式必須判斷截斷是否可接受。 如果未進行截斷， **SQLDriverToDataSource** 會傳回 FALSE，因為另一個錯誤。 無論是哪一種情況， *szErrorMsg*中都會傳回特定的錯誤訊息。  
  
 如需有關翻譯資料的詳細資訊，請參閱 [轉譯 dll](../../../odbc/reference/develop-app/translation-dlls.md)。  
  
## <a name="related-functions"></a>相關函數  
  
|如需下列資訊|請參閱|  
|---------------------------|---------|  
|轉譯從資料來源傳回的資料|[SQLDataSourceToDriver](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|  
|傳回連接屬性的設定|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|設定連接屬性|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
