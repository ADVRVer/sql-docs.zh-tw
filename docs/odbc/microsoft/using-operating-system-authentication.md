---
title: 使用作業系統驗證 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], authentication
- authentication [ODBC]
ms.assetid: 613daef7-3171-42d0-b7e3-3879280f864d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 56f09a82c2e67ee74ce140f4742bfaf0bcce247f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088119"
---
# <a name="using-operating-system-authentication"></a>使用作業系統驗證
> [!IMPORTANT]  
>  這項功能將會在未來的 Windows 版本中移除。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 請改用 Oracle 所提供的 ODBC 驅動程式。  
  
 Oracle 作業系統驗證依賴基礎作業系統來控制資料庫帳戶的存取。 使用者在使用此類型的登入時不需要輸入密碼。  
  
 若要利用這項功能，請指定 "/" 做為使用者識別碼，並在使用下列任何連線 Api 連接時不要指定密碼： [SQLBrowseConnect](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md)、 [SQLConnect](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md)或[SQLDriverConnect](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md)。  
  
 Oracle 資料庫使用 SQL * Net 驗證服務來驗證已登入的使用者。 如果使用者透過 SQLPlus 登入 Oracle，此服務就會正常運作;不過，當登入的使用者是服務（例如 Internet Information Services）時，驗證會失敗。 這是已知的 SQL\*Net 驗證限制，並會產生下列錯誤：「[Microsoft] [ODBC Driver for Oracle] [ORACLE] tnsnames.ora-12641： TNS：驗證服務無法初始化」。  
  
 您可以藉由編輯 Sqlnet.ora. tnsnames.ora 檔案來更正這個問題。 這個設定檔通常會儲存在 Oracle 主目錄的 Network\Admin 子目錄中。 將下列程式程式碼新增至 Sqlnet.ora。 tnsnames.ora：  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```
