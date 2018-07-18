---
title: 資料型別 dBASE |Microsoft 文件
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
- Jet-based ODBC drivers [ODBC], DBasedriver
- desktop database drivers [ODBC], DBasedriver
- DBase driver [ODBC], data types
- data types [ODBC], DBase driver
- dbase data types [ODBC]
- ODBC desktop database drivers [ODBC], DBasedriver
ms.assetid: a0e31e6b-d02b-4ee2-9b37-5baf6a11c0a6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60240eb9763d2d0b581765bde3a6d0958567f08e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32901283"
---
# <a name="dbase-data-types"></a>dBASE 資料類型
下表顯示 dBASE 資料類型如何對應至 ODBC SQL 資料類型。 請注意，並非所有的 ODBC SQL 資料類型所支援。  
  
|dBASE 資料類型|ODBC 資料類型|  
|---------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATE|SQL_DATE|  
|FLOAT [1]|SQL_DOUBLE|  
|邏輯|SQL_BIT|  
|附註|SQL_LONGVARCHAR|  
|數值 (BCD)|SQL_DOUBLE|  
|OLEOBJECT [1]|SQL_LONGBINARY|  
  
 僅針對 dBASE 第 5 版的有效 [1]。*x*  
  
 DBASE 的有效位數 III 允許將數字以設定兩位數指數，然後在 dBASE IV 的數字最多三位數指數。 因為數字會儲存為文字，所以會轉換成數字。 如果要轉換的數字不適合在欄位中，可能會發生不明的結果。  
  
 有效位數和小數位數必須指定具有數值資料類型，可讓 dBASE，它不支援 ODBC dBASE 驅動程式。 ODBC dBASE 驅動程式一律會傳回 15 個有效位數和小數位數為 0 的數值資料類型。  
  
 建立與使用 ODBC dBASE 驅動程式對應的 ODBC SQL_DOUBLE 資料類型的數值資料類型的資料行。 因此，此資料行中的資料是受制於捨入。 此行為不相同也就是 Binary Coded Decimal (BCD) 在 dBASE （類型 N） 中的數值資料輸入。  
  
> [!NOTE]  
>  **SQLGetTypeInfo**傳回 ODBC SQL 資料類型。 所有的轉換中的 < 附錄 D *ODBC 程式設計人員參考*支援本主題稍早所列的 ODBC SQL 資料類型。  
  
 下表顯示限制在 dBASE 資料類型。  
  
|資料類型|Description|  
|---------------|-----------------|  
|CHAR|建立 CHAR 資料行的零或未指定的長度實際上會傳回 254 個位元組的資料行。|  
|加密的資料|DBASE 驅動程式不支援加密的 dBASE 資料表。|  
|邏輯|DBASE 驅動程式無法建立索引的邏輯資料行上。|  
|附註|備忘資料行的最大長度為 65500 位元組。|  
  
 資料類型的多個限制可以在[資料型別限制](../../odbc/microsoft/data-type-limitations.md)。
