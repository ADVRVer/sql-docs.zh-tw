---
title: SQLColAttributes （dBASE 驅動程式） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLColAttributes
ms.assetid: ed44de2b-0b01-4dce-a340-f5eb3aac30b7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 66a37f3c9ceccdf3fb226ea423552886d36ed99f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "67903977"
---
# <a name="sqlcolattributes-dbase-driver"></a>SQLColAttributes (dBASE 驅動程式)
> [!NOTE]  
>  本主題提供 dBASE 驅動程式特定的資訊。 如需此函數的一般資訊，請參閱[ODBC API 參考](../../odbc/reference/syntax/odbc-api-reference.md)底下的適當主題。  
  
|屬性|註解|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|若為 LONGVARBINARY 資料，SQL_COLUMN_DISPLAY_SIZE 是資料行的最大長度，而不是資料行次的最大長度2。|  
|SQL_OWNER_NAME|此資料行中會傳回空字串（""），因為不支援擁有者名稱。|  
|SQL_QUALIFIER_NAME|會傳回目錄的路徑。|  
|SQL_COLUMN_SEARCHABLE|LONGVARBINARY 和 LONGVARCHAR 資料行會回報為 SQL_UNSEARCHABLE。<br /><br /> 固定長度和可變長度的二進位和字元資料類型是可搜尋的，即使 LONGVARBINARY 和 LONGVARCHAR 不是也一樣。|  
  
> [!NOTE]  
>  上述不是**SQLColAttributes**所傳回之屬性的完整清單。
