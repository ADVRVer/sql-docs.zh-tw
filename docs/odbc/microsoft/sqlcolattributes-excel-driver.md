---
title: SQLColAttributes （Excel 驅動程式） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], Excel Driver
ms.assetid: 7c4833e3-ff0c-4313-9ab8-21379ceab656
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cd3076ba19b9f5372074a9256e20d73858f69c09
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68132669"
---
# <a name="sqlcolattributes-excel-driver"></a>SQLColAttributes (Excel 驅動程式)
> [!NOTE]  
>  本主題提供 Excel 驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC API 參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
|屬性|註解|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|SQL_COLUMN_DISPLAY_SIZE LONGVARBINARY 資料是資料行，而不 2 次的資料行的最大長度的最大長度。|  
|SQL_OWNER_NAME|空字串 ("") 會傳回此資料行中，因為不支援擁有者名稱。|  
|SQL_QUALIFIER_NAME|會傳回目錄的路徑。|  
|SQL_COLUMN_SEARCHABLE|LONGVARBINARY 和 LONGVARCHAR 資料行報告為 SQL_UNSEARCHABLE。<br /><br /> 即使 LONGVARBINARY 和 LONGVARCHAR 不是，仍可供搜尋，固定長度和可變長度的二進位和字元資料類型。|  
  
> [!NOTE]  
>  上述不是所傳回的屬性完整清單**SQLColAttributes**。
