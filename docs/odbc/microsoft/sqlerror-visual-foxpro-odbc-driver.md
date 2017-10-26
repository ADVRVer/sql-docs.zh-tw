---
title: "SQLError （Visual FoxPro ODBC 驅動程式） |Microsoft 文件"
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
- SQLError function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8315ec16-1c22-447a-a577-39bd94f61070
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 46696509f9276ac4974604c931c4d77acbaae15b
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError （Visual FoxPro ODBC 驅動程式）
> [!NOTE]  
>  本主題包含 Visual FoxPro ODBC 驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC 應用程式開發介面參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 支援： 完整  
  
 ODBC 應用程式開發介面相容性： 核心層級  
  
 傳回最後一個錯誤的錯誤或狀態資訊。 驅動程式會維護堆疊或在傳回的錯誤清單*hstmt*， *hdbc*，和*henv*引數，根據如何呼叫**SQLError**進行。 錯誤佇列會排清，每個陳述式之後。  
  
 下表描述**SQLError**引數和傳回值，驅動程式所使用。  
  
|SQLError 引數|傳回值的描述|  
|-----------------------|------------------------------|  
|*szSQLState*|表示錯誤的 SQLSTATE 值。|  
|*pfNativeError*|非零值表示[Visual FoxPro ODBC 驅動程式原生錯誤訊息](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md)。 值為零表示已偵測到的驅動程式並對應至適當錯誤[ODBC 錯誤碼](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md)。|  
|*szErrorMsg*|原生錯誤或 ODBC 錯誤文字。|  
|*pcbErrorMsg*|訊息文字加上一個識別項長度的長度。|  
  
 如需有關驅動程式的錯誤訊息的詳細資訊，請參閱[錯誤訊息概觀](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md)。 如需此函式的詳細資訊，請參閱[SQLError](../../odbc/reference/syntax/sqlerror-function.md)中*ODBC 程式設計人員參考*。

