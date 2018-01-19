---
title: "[^]（萬用字元-不相符的字元）(TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 12/06/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- wildcard
- '[^]_TSQL'
- '[^]'
- Not Match
dev_langs: TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- '[^] (wildcard - character(s) not to match)'
ms.assetid: b970038f-f4e7-4a5d-96f6-51e3248c6aef
caps.latest.revision: "36"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 44226e92dafa4578a0aceac8403d2ef3624ef41d
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="-wildcard---characters-not-to-match-transact-sql"></a>\[^\]（萬用字元-不相符的字元）(TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  比對不在方括號指定範圍或集合內的任何單一字元。  
  
## <a name="examples"></a>範例  
 下列範例會利用 [^] 運算子來尋找 `Contact` 資料表中，所有名字的開頭都是 `Al`，而且名字第三個字母不是 `a` 的人。  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE 'Al[^a]%'  
ORDER BY FirstName;  
```  
  
## <a name="see-also"></a>另請參閱  
 [LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [PATINDEX &#40;TRANSACT-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)   
 [%&#40;萬用字元-字元 &#40; s &#41;若要比對 &#41;&#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
  [&#91;&#93;&#40;萬用字元-字元 &#40; s &#41;若要比對 &#41;&#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [\_&#40;萬用字元-符合一個字元 &#41;&#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
  
  
