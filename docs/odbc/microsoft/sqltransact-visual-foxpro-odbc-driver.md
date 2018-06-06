---
title: SQLTransact （Visual FoxPro ODBC 驅動程式） |Microsoft 文件
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
- SQLTransact function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 92cf86c0-f7a8-44d7-b59f-a1342677440b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d55151795d4f25edf08c5f1b3efa02499996c510
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact （Visual FoxPro ODBC 驅動程式）
> [!NOTE]  
>  本主題包含 Visual FoxPro ODBC 驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC 應用程式開發介面參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 支援： 完整  
  
 ODBC 應用程式開發介面相容性： 核心層級  
  
 要求認可或復原作業的所有陳述式控制代碼上的所有作用中的作業 (*hstmt*s) 相關聯的連接，或環境控制代碼相關聯的所有連線*henv*。 **SQLTransact**只適用於屬於資料來源[資料庫](../../odbc/microsoft/visual-foxpro-terminology.md)。  
  
 如果認可失敗，在手動模式中，交易會維持使用中。您可以選擇要回復交易，或重試認可操作。 如果在自動交易模式中，認可作業失敗，異動會自動回復;無法非使用中交易。  
  
 如需詳細資訊，請參閱[SQLTransact](../../odbc/reference/syntax/sqltransact-function.md)中*ODBC 程式設計人員參考*。
