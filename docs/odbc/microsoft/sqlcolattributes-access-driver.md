---
title: "SQLColAttributes （存取驅動程式） |Microsoft 文件"
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
- SQLColAttribute function [ODBC], Access Driver
- Access driver [ODBC], SQLColAttributes
ms.assetid: adb6f81d-e8c7-4748-9b1d-f7a053788bbc
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 16542092f4c3d615374eba37beb4b0820277ad02
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2017
---
# <a name="sqlcolattributes-access-driver"></a>SQLColAttributes （存取驅動程式）
> [!NOTE]  
>  本主題提供存取驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC 應用程式開發介面參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
|Attribute|註解|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|SQL_COLUMN_DISPLAY_SIZE LONGVARBINARY 資料是資料行，而不時間 2 的資料行的最大長度的最大長度。|  
|SQL_OWNER_NAME|空字串 ("") 不支援擁有者名稱，因此，會傳回此資料行中。|  
|SQL_QUALIFIER_NAME|會傳回資料庫檔案的路徑。|  
|SQL_COLUMN_SEARCHABLE|LONGVARBINARY 和 LONGVARCHAR 資料行報告為 SQL_UNSEARCHABLE。<br /><br /> 雖然 LONGVARBINARY 和 LONGVARCHAR 不是，仍可搜尋，固定長度和可變長度的二進位和字元資料類型。|  
  
> [!NOTE]  
>  上述內容並非完整清單屬性所傳回的**SQLColAttributes**。
