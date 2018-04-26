---
title: 有效位數、小數位數和長度 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- data types [SQL Server], length
- data types [SQL Server], scale
- precision [SQL Server], data types
- lengths [SQL Server], data types
- number of digits
- scale [SQL Server]
- scale [SQL Server], data types
- data types [SQL Server], precision
ms.assetid: fbc9ad2c-0d3b-4e98-8fdd-4d912328e40a
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 04fd1c983a9c580e021de51cd93fff69800e5c9f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="precision-scale-and-length-transact-sql"></a>有效位數、小數位數和長度 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

位數 (Precision) 是指數字中總共的位數。 小數位數 (Scale) 則是指數字中小數點右方的位數。 例如 123.45 的位數是 5，小數位數是 2。
  
在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，**numeric** 和 **decimal** 資料類型的預設最大有效位數為 38。 在舊版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，預設的最大值是 28。
  
數值資料類型的長度是用來儲存數字的位元組數目。 字元字串或 Unicode 資料類型的長度是字元的數目。 **binary**、**varbinary** 及 **image** 資料類型的長度為位元組的數目。 例如，**int** 資料類型可以保留 10 位數，儲存在 4 位元組中且不接受小數點。 **int** 資料類型的有效位數是 10，長度是 4，小數位數是 0。
  
當串連兩個 **char**、**varchar**、**binary** 或 **varbinary** 運算式時，產生的運算式長度是兩個來源運算式長度的總和，或 8,000 字元，兩者取較小者。
  
當串連兩個 **nchar** 或 **nvarchar** 運算式時，產生的運算式長度是兩個來源運算式長度的總和，或 4,000 字元，兩者取較小者。
  
當利用 UNION、EXCEPT 或 INTERSECT 來比較長度不同之相同資料類型的運算式時，產生的長度是兩個運算式的最大長度。
  
**decimal** 兩旁數值資料類型的有效位數和小數位數是固定的。 如果算術運算子有兩個相同類型的運算式，結果會有相同的資料類型，且會有定義給這個類型的有效位數和小數位數。 如果運算子有兩個含不同數值資料類型的運算式，資料類型優先順序的規則會定義這個結果的資料類型。 結果會有定義給它的資料類型的有效位數和小數位數。
  
下表定義在運算結果是 **decimal** 類型時，如何計算結果的有效位數和小數位數。 當符合下列中的任何條件時，結果便是 **decimal**：
-   兩個運算式都是 **decimal**。  
-   一個運算式為 **decimal**，另一個運算式為優先順序低於 **decimal** 的資料類型。  
  
運算元運算式表示成運算式 e1 (有效位數是 p1，小數位數是 s1) 和運算式 e2 (有效位數是 p2，小數位數是 s2)。 任何不是 **decimal** 之運算式的有效位數和小數位數，都是定義給運算式資料類型的有效位數和小數位數。
  
|作業|結果有效位數|結果小數位數 *|  
|---|---|---|
|e1 + e2|max(s1, s2) + max(p1-s1, p2-s2) + 1|max(s1, s2)|  
|e1 - e2|max(s1, s2) + max(p1-s1, p2-s2) + 1|max(s1, s2)|  
|e1 * e2|p1 + p2 + 1|s1 + s2|  
|e1 / e2|p1 - s1 + s2 + max(6, s1 + p2 + 1)|max(6, s1 + p2 + 1)|  
|e1 { UNION &#124; EXCEPT &#124; INTERSECT } e2|max(s1, s2) + max(p1-s1, p2-s2)|max(s1, s2)|  
|e1 % e2|min(p1-s1, p2 -s2) + max( s1,s2 )|max(s1, s2)|  
  
\* 結果有效位數及小數位數的絕對最大值為 38。 當結果有效位數大於 38 時，會縮小至 38，並會縮減對應的小數位數，以防止截斷結果的整數部分。 在例如乘法或除法等某些案例中，為保持十進位有效位數，將不會縮小比例因素 (雖然可能會引發溢位錯誤)。

在加法跟減法運算中，我們需要 `max(p1 – s1, p2 – s2)` 位置來儲存十進位數字的整數部分。 若沒有足夠的空間儲存它們 (即 `max(p1 – s1, p2 – s2) < min(38, precision) – scale`) 時，便會縮小小數位數，以提供整數部分足夠的空間。 其結果的小數位數便是 `MIN(precision, 38) - max(p1 – s1, p2 – s2)`，因此小數部分可能會四捨五入以調整至符合結果的小數位數。

在乘法及除法運算中，我們需要 `precision - scale` 位置來儲存結果的整數部分。 可能會使用下列規則來縮小小數位數：
1.  若整數部分小於 32，則結果的小數位數會縮小至 `min(scale, 38 – (precision-scale))`，因為它不可大於 `38 – (precision-scale)`。 在此案例中，結果可能會四捨五入。
1. 若其小於 6 且整數部分大於 32，則小數位數便不會變更。 在此案例中，若無法調整至符合 decimal(38, scale)，則便可能引發溢位錯誤 
1. 若其大於 6 且整數部分大於 32，則小數位數便會設為 6。 在此案例中，整數部分及小數位數都會縮小，且其結果的類型為 decimal(38, 6)。 結果可能會四捨五入至 6 個小數位數，或是擲回溢位錯誤 (若整數部分無法調整至 32 位數)。

## <a name="examples"></a>範例
下列運算式會傳回結果 `0.00000090000000000` 且不四捨五入，因為結果可調整至符合 `decimal(38,17)`：
```sql
select cast(0.0000009000 as decimal(30,20)) * cast(1.0000000000 as decimal(30,20)) [decimal 38,17]
```
在此案例中，位數 (precision) 為 61，小數位數 (scale) 為 40。
整數部分 (precision-scale = 21) 小於 32，因此這屬於乘法規則中的案例 (1)，小數位數會計算為 `min(scale, 38 – (precision-scale)) = min(40, 38 – (61-40)) = 17`。 結果類型為 `decimal(38,17)`。

下列運算式會傳回結果 `0.000001` 以符合 `decimal(38,6)`：
```sql
select cast(0.0000009000 as decimal(30,10)) * cast(1.0000000000 as decimal(30,10)) [decimal(38, 6)]
```
在此案例中，位數為 61，小數位數為 20。
小數位數大於 6 且整數位數 (`precision-scale = 41`) 大於 32。 這屬於乘法規則中的案例 (3)，其結果類型為 `decimal(38,6)`。

## <a name="see-also"></a>另請參閱
[運算式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[資料類型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  
