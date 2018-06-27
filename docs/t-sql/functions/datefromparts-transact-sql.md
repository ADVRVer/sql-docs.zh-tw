---
title: DATEFROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATEFROMPARTS_TSQL
- DATEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATEFROMPARTS function
ms.assetid: 5b885376-87aa-41f1-9e18-04987aead250
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 45446ffcf04092574737640fd338a35f04497181
ms.sourcegitcommit: 6e55a0a7b7eb6d455006916bc63f93ed2218eae1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2018
ms.locfileid: "35239028"
---
# <a name="datefromparts-transact-sql"></a>DATEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

此函式會傳回對應至指定年份、月份和日期值的 **date** 值。
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>語法  
  
```sql
DATEFROMPARTS ( year, month, day )  
```  
  
## <a name="arguments"></a>引數  
*year*  
指定年份的整數運算式。
  
*month*  
指定月份的整數運算式，從 1 到 12。
  
*day*  
指定日期的整數運算式。
  
## <a name="return-types"></a>傳回類型
**date**
  
## <a name="remarks"></a>Remarks  
`DATEFROMPARTS` 會傳回 **date** 值，其中日期部分會設為指定的年、月、日，而時間部分則會設為預設值。 若引數無效，`DATEFROMPARTS` 會引發錯誤。 如果至少一個必要引數具有 Null 值，則 `DATEFROMPARTS` 會傳回 Null。
  
此函式可以遠端處理到 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 伺服器及更新版本。 它無法遠端處理到版本低於 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 的伺服器。
  
## <a name="examples"></a>範例  
此範例示範 `DATEFROMPARTS` 函式的運作。
  
```sql
SELECT DATEFROMPARTS ( 2010, 12, 31 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
----------------------------------  
2010-12-31  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>另請參閱
[日期 &#40;Transact-SQL&#41;](../../t-sql/data-types/date-transact-sql.md)
  
  

