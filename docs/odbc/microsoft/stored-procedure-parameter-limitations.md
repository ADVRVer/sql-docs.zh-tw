---
title: 預存程序參數限制 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 8b804bcf-4cce-4e6f-aa45-00bab9ef9921
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 34f3bc435a0bbd514eed4f9ce6100a9cca6b6cb7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32903513"
---
# <a name="stored-procedure-parameter-limitations"></a>預存程序參數的限制
> [!IMPORTANT]  
>  將移除這項功能，在未來的版本的 Windows。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 相反地，使用由 Oracle 提供的 ODBC 驅動程式。  
  
 當執行 Oracle 預存程序，以便利用 10 或多個輸出參數時，預存程序呼叫將會失敗，造成存取違規或 ActiveX Data Objects (ADO) 錯誤。 當使用 oracle 的 Microsoft ODBC Driver 8.0.4.0.0 和 8.0.4.0.4 Oracle 用戶端軟體的版本，此狀況發生。  
  
 若要修正這個問題，Oracle 用戶端軟體必須升級為版本 8.0.4.2.0 或更高版本。 如需詳細資訊，請連絡 Oracle Corporation[修補程式](../../odbc/microsoft/oracle-software-patches.md)。  
  
> [!NOTE]  
>  Oracle 用戶端軟體版本 8.0.3.0.0 早期版本，不會發生這個問題。
