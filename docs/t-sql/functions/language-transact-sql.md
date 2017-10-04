---
title: "@@LANGUAGE (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@LANGUAGE_TSQL'
- '@@LANGUAGE'
dev_langs:
- TSQL
helpviewer_keywords:
- languages [SQL Server], current in use
- '@@LANGUAGE function'
- current language in use
- names [SQL Server], language in use
ms.assetid: 3e13b477-7dfa-4da6-9948-da2050d42527
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: cd64185b31ad5aba9496e55031eae15ae46d5180
ms.contentlocale: zh-tw
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40language-transact-sql"></a>&#x40;&#x40;語言 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回目前所用的語言名稱。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
@@LANGUAGE  
```  
  
## <a name="return-types"></a>傳回類型  
 **nvarchar**  
  
## <a name="remarks"></a>備註  
 若要檢視有關語言設定，包括有效的官方語言名稱的資訊執行**sp_helplanguage**指定參數。  
  
## <a name="examples"></a>範例  
 下列範例會傳回目前工作階段的語言。  
  
```  
SELECT @@LANGUAGE AS 'Language Name';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Language Name                   
------------------------------  
us_english                      
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 下列範例會傳回目前工作階段的語言。  
  
```  
SELECT @@LANGUAGE AS 'Language Name';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Language Name                   
------------------------------  
us_english                      
```  
  
## <a name="see-also"></a>另請參閱  
 [組態函式 &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [設定語言 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/set-language-transact-sql.md)   
 [sp_helplanguage &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)  
  
  


