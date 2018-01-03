---
title: "SQLPrepare （Visual FoxPro ODBC 驅動程式） |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLPrepare function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 0c4cb5a4-9729-4b2e-a0c6-52027b92e8fc
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b810cd3adff4e5903a3ce515eb501b4a8f202c14
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="sqlprepare-visual-foxpro-odbc-driver"></a>SQLPrepare （Visual FoxPro ODBC 驅動程式）
> [!NOTE]  
>  本主題包含 Visual FoxPro ODBC 驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC 應用程式開發介面參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 支援： 完整  
  
 ODBC 應用程式開發介面相容性： 核心層級  
  
 您可以規劃如何最佳化及執行陳述式準備的 SQL 陳述式。 SQL 陳述式會編譯執行[SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)。  
  
 如果您的資料表、 檢視或欄位名稱包含空格，括住名稱後方引號 （'） 標記。 例如，如果您的資料庫包含名為 我的資料表和欄位 My Field 的資料表，括住的識別項的每個項目，如下所示：  
  
```  
SELECT * FROM `My Table`.`My Field`  
```  
  
 如需詳細資訊，請參閱[SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md)中*ODBC 程式設計人員參考*。
