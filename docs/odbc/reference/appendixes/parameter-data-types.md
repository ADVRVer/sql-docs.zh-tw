---
title: "參數資料類型 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], parameters
- parameter data type [ODBC]
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: fd7e99d8-d26a-408c-9733-6ffccde99f75
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5dcd41f599a6e57a55d05a8a869363ec70c5f756
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="parameter-data-types"></a>參數資料類型
即使每個參數指定**SQLBindParameter**會定義使用 SQL 資料類型，SQL 陳述式的參數有任何內建資料類型。 因此，參數標記可以包含在 SQL 陳述式才可以從另一個陳述式中運算元推斷其資料類型。 例如，在算術運算式嗎？ + 從具名資料行 COLUMN1 所代表的資料類型可以推斷 COLUMN1，參數的資料類型。 如果無法判別資料類型，應用程式無法使用參數標記。  
  
 下表說明針對數種類型的參數，根據 sql-92 決定資料類型的方式。 在推斷更廣泛規格的參數型別時使用其他 SQL 子句時，請參閱 sql-92 規格。  
  
|參數的位置|假設資料類型|  
|---------------------------|-----------------------|  
|一個二進位算術或比較運算子的運算元|與另一個運算元相同|  
|中的第一個運算元**BETWEEN**子句|第二個運算元相同|  
|中的第二個或第三個運算元**BETWEEN**子句|第一個運算元與相同|  
|搭配使用的運算式**IN**|第一個值或子查詢的結果資料行相同|  
|搭配使用的值**IN**|運算式或運算式中的參數標記時的第一個值相同|  
|模式值搭配使用**像**|VARCHAR|  
|搭配使用的更新值**更新**|更新資料行相同|
