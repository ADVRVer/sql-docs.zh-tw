---
title: "SQLStatistics （Excel 驅動程式） |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Excel Driver
ms.assetid: 02506664-8dcc-4bd0-a8bb-d49fcbdd5722
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5544a2932f4a05f5452d04f3113a3e5d25c68c2c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2017
---
# <a name="sqlstatistics-excel-driver"></a>SQLStatistics （Excel 驅動程式）
> [!NOTE]  
>  本主題提供 Excel 驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC 應用程式開發介面參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
|資料行|註解|  
|------------|--------------|  
|TABLE_QUALIFIER|目錄的路徑。<br /><br /> 模式比對中不支援*szTableQualifier*引數。|  
|TABLE_OWNER|因為擁有者名稱不支援此資料行就會傳回 NULL。|  
|TABLE_NAME|未分隔的資料表名稱。<br /><br /> 模式比對中不支援*szTableName*引數。|  
|INDEX_QUALIFIER|一律傳回 NULL。|  
|INDEX_NAME|索引而定。|  
|TYPE|只有 SQL_TABLE_STAT 或 SQL_INDEX_OTHER 就會傳回型別。|  
|SEQ_IN_INDEX|索引而定。|  
|COLUMN_NAME|索引而定。|  
|COLLATION|索引而定。|  
|PAGES|一律傳回 NULL。|  
  
 篩選根據唯一性 ( *fUnique*引數)。 *FAccuracy*參數已忽略。
