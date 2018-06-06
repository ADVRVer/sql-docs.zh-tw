---
title: 文字檔案資料型別 |Microsoft 文件
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
- text file driver [ODBC], data types
- ODBC desktop database drivers [ODBC], text file driver
- desktop database drivers [ODBC], text file driver
- text file data types [ODBC]
- Jet-based ODBC drivers [ODBC], text file driver
ms.assetid: e113112e-ae42-469e-8e4b-a365a10d9071
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14b808ff5d2cdc22afa050e2c7e0b760532b880d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="text-file-data-types"></a>文字檔案資料類型
下表顯示如何將文字資料型別對應至 ODBC SQL 資料類型。 請注意，並非所有的 ODBC SQL 資料類型都受到 ODBC 文字驅動程式。  
  
|文字資料類型|ODBC 資料類型|  
|--------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATETIME|SQL_TIMESTAMP|  
|FLOAT|SQL_DOUBLE|  
|INTEGER|SQL_INTEGER|  
|LONGCHAR|SQL_LONGVARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo**傳回 ODBC 資料類型。 所有的轉換中的 < 附錄 D *ODBC 程式設計人員參考*支援上表中列出的 SQL 資料類型。  
  
 下表顯示文字資料類型的限制。  
  
|資料類型|Description|  
|---------------|-----------------|  
|CHAR|建立 CHAR 資料行的零或未指定的長度實際上會傳回 255 位元資料行。<br /><br /> CHAR 資料行可能會或可能沒有雙引號分隔符號的開頭和結尾; 分隔的檔案中在固定長度的檔案，不會使用雙引號做為分隔符號。|  
|DATETIME|MM-DD-YY （例如，01-17-92）<br /><br /> MMM DD YY (例如，年 1 月-17-92)<br /><br /> DD-MMM-YY (例如，17-年 1 月-92)<br /><br /> YYYY-MM-DD （例如 1992年-01-17）<br /><br /> YYYY-MMM-DD （例如 1992年-年 1 月-17）<br /><br /> 在資料表中不允許混合的日期分隔符號。<br /><br /> 文字 ISAM 格式化 DATETIME 欄位是美國和歐洲的格式，在 Windows 控制台中的國際設定而定。|  
|FLOAT|最大寬度包括正負號和小數點。 在 Schema.ini，寬度被表示，如下所示：<br /><br /> 14.083 為 FLOAT 寬度 6<br /><br /> -14.083 為 FLOAT 寬度 7<br /><br /> +14.083 為 FLOAT 寬度 7<br /><br /> 14083。 是 FLOAT 寬度為 6<br /><br /> ODBC 一律會傳回 8 浮點數資料行。<br /><br /> 浮點數資料行也可以是以科學記號標記法，例如：<br /><br /> -3.04E + 2 是浮動寬度 8<br /><br /> 25E4 為 Float 寬度 4<br /><br /> **請注意**十進位和科學標記法不能混合資料行中。<br /><br /> NULL 值都由固定長度檔案中的空白填補字串和分隔檔案中會省略。<br /><br /> 浮點數資料可以填補開頭空白。|  
|INTEGER|整數資料行的有效值為-32766 至 32767。<br /><br /> 在 Schema.ini，寬度被表示，如下所示：<br /><br /> 14083 為整數寬度 5<br /><br /> 0 為整數寬度 1<br /><br /> ODBC 一律會傳回整數資料行的 4。<br /><br /> 最大寬度包括正負號。 整數資料行的最大寬度為 11，雖然可能更大，因為可固定格式的資料表中的空白寬度。|  
|LONGCHAR|理論上限制在 LONGCHAR 資料行的寬度固定長度或分隔的資料表是 65500 K。 文字 ISAM 很容易提供可靠的支援，最多約 32k。|  
  
 資料類型的多個限制可以在[資料型別限制](../../odbc/microsoft/data-type-limitations.md)。
