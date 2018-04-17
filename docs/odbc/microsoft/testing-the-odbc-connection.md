---
title: 測試 ODBC 連接 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- testing connections [ODBC]
- ODBC driver for Oracle [ODBC], testing connections
ms.assetid: 5e671665-2aba-49a7-8871-70784d8b3cc9
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dee186c832f79c59da23adc48295ef647446711e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="testing-the-odbc-connection"></a>測試 ODBC 連接
> [!IMPORTANT]  
>  將移除這項功能，在未來的版本的 Windows。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 相反地，使用由 Oracle 提供的 ODBC 驅動程式。  
  
 當疑難排解 Oracle ODBC 存取 7.x 及 Oracle8 RDBMS 伺服器，可能需要確認基礎 SQL * Net 與 Oracle 通訊協定介面卡已正確安裝。 若要這樣做，請使用 Oracle 提供公用程式 Nettest.exe Orawin\Bin 目錄中。  
  
 Nettest 是簡單的公用程式，嘗試登入到選取的伺服器使用已安裝的 SQL * Net 屬於的 Oracle 用戶端的軟體。 公用程式會要求登入名稱、 密碼和 TNS 連接字串。 如果已正確安裝 Oracle 用戶端，此公用程式只會顯示 「 Ping 成功。 」 如果登入不成功，您必須洽詢資料庫管理員。
