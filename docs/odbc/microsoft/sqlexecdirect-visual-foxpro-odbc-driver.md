---
title: SQLExecDirect (Visual FoxPro ODBC Driver) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExecDirect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 808d7890c18839c0e9059cdc3181a4579eb2ec4f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "63313304"
---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect (Visual FoxPro ODBC Driver)
> [!NOTE]  
>  本主題包含 Visual FoxPro ODBC 驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC API 參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 支援：完整  
  
 ODBC API 相容性：核心層級  
  
 執行全新[preparable 的 SQL 陳述式](../../odbc/microsoft/visual-foxpro-terminology.md)。 Visual FoxPro ODBC 驅動程式會使用參數標記變數的目前值，如果陳述式中存在的任何參數。  
  
 若要建立批次命令提交多個 SQL 陳述式，一次，請使用分號 （;） 來分隔每個批次中的 SQL 陳述式。  
  
 如果您的資料表、 檢視或欄位名稱包含空格，括住名稱後引號標記。 例如，如果您的資料庫包含名為我的資料表和欄位的 我的欄位的資料表，括住識別項的每個項目，如下所示：  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 如需詳細資訊，請參閱 < [SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md)中*ODBC 程式設計人員參考*。
