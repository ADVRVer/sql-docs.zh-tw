---
title: 針對 Oracle 的 ODBC 驅動程式所傳回的訊息 |Microsoft 文件
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
- error messages [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], error messages
ms.assetid: 150bde1d-adb6-4e77-90e9-4dc93499a746
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 067300b35282b39c63504f6f8e3a16fd3e1a8c00
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="messages-returned-by-the-odbc-driver-for-oracle"></a>針對 Oracle 的 ODBC 驅動程式所傳回的訊息
> [!IMPORTANT]  
>  將移除這項功能，在未來的版本的 Windows。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 相反地，使用由 Oracle 提供的 ODBC 驅動程式。  
  
 Oracle 錯誤訊息是否可用，則它會傳回前面 [Microsoft]，加上 [ODBC Driver for Oracle，] 和 [Oracle] 標記。否則，則會傳回訊息沒有 [Oracle] 標記，如下列範例所示：  
  
## <a name="oracle-error-message"></a>Oracle 錯誤訊息：  
  
```  
[Microsoft][ODBC driver for Oracle][Oracle]ORA-nnnnn message-text  
```  
  
## <a name="odbc-driver-for-oracle-error-message"></a>Oracle 錯誤訊息的 ODBC 驅動程式：  
  
```  
[Microsoft][ODBC driver for Oracle]  
```
