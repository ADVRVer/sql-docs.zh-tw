---
title: COMPRESS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/11/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: reference
f1_keywords:
- COMPRESS
- COMPRESS_TSQL
helpviewer_keywords:
- COMPRESS function
ms.assetid: c2bfe9b8-57a4-48b4-b028-e1a3ed5ece88
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6edda04e2520ec915a6c4767751130f091668e85
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87394293"
---
# <a name="compress-transact-sql"></a>COMPRESS (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

此函式會使用 GZIP 演算法壓縮輸入運算式。 此函式會傳回類型 **varbinary(max)** 的位元組陣列。
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>語法  
  
```sql
COMPRESS ( expression )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>引數
*expression*  
A

* **binary(***n***)**
* **char(***n***)**
* **nchar(***n***)**
* **nvarchar(max)**
* **nvarchar(***n***)**
* **varbinary(max)**
* **varbinary(***n***)**
* **varchar(max)**

或

* **varchar(***n***)**

expression： 如需詳細資訊，請參閱[運算式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)。
  
## <a name="return-types"></a>傳回類型
**varbinary(max)** 代表輸入的已壓縮內容。
  
## <a name="remarks"></a>備註  
壓縮的資料無法編製索引。
  
`COMPRESS` 函式會壓縮輸入運算式資料。 您必須叫用此函式才能壓縮各資料區段。 如需有關在資料列或頁面層級儲存期間的自動資料壓縮詳細資訊，請參閱[資料壓縮](../../relational-databases/data-compression/data-compression.md)。
  
## <a name="examples"></a>範例  
  
### <a name="a-compress-data-during-the-table-insert"></a>A. 在資料表插入期間壓縮資料  
此範例示範如何壓縮插入資料表的資料：
  
```sql
INSERT INTO player (name, surname, info )  
VALUES (N'Ovidiu', N'Cracium',   
        COMPRESS(N'{"sport":"Tennis","age": 28,"rank":1,"points":15258, turn":17}'));  
  
INSERT INTO player (name, surname, info )  
VALUES (N'Michael', N'Raheem', compress(@info));  
```  
  
### <a name="b-archive-compressed-version-of-deleted-rows"></a>B. 封存已刪除資料列的壓縮版本  
此陳述式會先從 `player` 資料表將舊的玩家記錄刪除。 為節省空間，陳述式隨後會以壓縮格式將記錄儲存在 `inactivePlayer` 資料表。
  
```sql
DELETE FROM player  
OUTPUT deleted.id, deleted.name, deleted.surname, deleted.datemodifier, COMPRESS(deleted.info)   
INTO dbo.inactivePlayers
WHERE datemodified < @startOfYear; 
```  
  
## <a name="see-also"></a>另請參閱
[字串函數 &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  
[DECOMPRESS &#40;Transact-SQL&#41;](../../t-sql/functions/decompress-transact-sql.md)
  
  
