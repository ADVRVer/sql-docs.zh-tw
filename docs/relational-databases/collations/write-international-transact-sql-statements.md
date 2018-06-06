---
title: 撰寫國際通用的 Transact-SQL 陳述式 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: collations
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- writing international statements
- Transact-SQL international considerations
- international considerations [SQL Server], Transact-SQL
- Database Engine international considerations [SQL Server], Transact-SQL
- statements [SQL Server], international
- database international considerations [SQL Server], Transact-SQL
- dates [SQL Server], international considerations
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
caps.latest.revision: 35
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e6a26cdde92df6b1d08a445f195e3e5f9ebc4d2b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="write-international-transact-sql-statements"></a>撰寫國際通用的 Transact-SQL 陳述式
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  如果遵循下列的指導方針，使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的資料庫與資料庫應用程式將更能從一個語言移植至另一個語言，或可支援多種語言：  
  
-   使用 **nchar**、 **nvarchar**，和 **nvarchar(max)** 來取代所有 **char**、 **varchar**，和 **text**資料類型。 如此一來您就不需要考慮字碼頁轉換的問題。 如需詳細資訊，請參閱 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)。  
  
-   當您執行月份和週中日的比較和運算時，請使用數值的日期部分，而不要使用名稱字串。 不同的語言設定會傳回不同的月份和週中日名稱。 例如，語言設定為「英文 (美國)」時，DATENAME(MONTH,GETDATE()) 會傳回 May；當語言設定為「德文」時，會傳回 Mai；而當語言設定為「法文」時，會傳回 mai。 請改用如 DATEPART 的函數，使用數字月份而不用名稱。 當您要將結果集顯示給使用者時，請使用 DATEPART 名稱，因為日期名稱通常比數值表示法來得有意義。 但是，不要根據特定語言的顯示名稱來撰寫程式碼邏輯。  
  
-   當您在比較或輸入至 INSERT 或 UPDATE 陳述式中指定日期時，請使用所有語言設定都作相同解譯的常數：  
  
    -   ADO、OLE DB 和 ODBC 應用程式應該使用以下形式的 ODBC 時間戳記、日期和時間逸出子句：  
  
         **{ ts'** yyyy**-***mm***-***dd**hh ***:*** mm ***:*** ss *[**.***fff*] **'}** 例如：**{ ts'** 1998**-** 09**-** 24 10 **:** 02 **:** 20 **' }**  
  
         **{ d'** *yyyy* **-** *mm* **-** *dd* **'}** 例如： **{ d'** 1998**-** 09**-** 24 **'}**  
  
         **{ t'** *hh* **:** *mm* **:** *ss* **'}** 例如： **{ t'** 10:02:20 **'}**  
  
    -   使用其他 API 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼、預存程序和觸發程序的應用程式，應該使用未分隔的數值字串。 例如 *yyyymmdd* 為 19980924。  
  
    -   使用其他 API 的應用程式，或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼、預存程序和觸發程序，都應該針對 **time**、 **date**、 **smalldate**、 **datetime**、 **datetime2**，和 **datetimeoffset** 資料類型以及字元字串資料類型之間的所有轉換使用明確樣式參數的 CONVERT 陳述式。 例如，下列陳述式在所有日期格式連接設定下的解譯都是一樣的：  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         如需詳細資訊，請參閱 [CAST 和 CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)。  
  
  
