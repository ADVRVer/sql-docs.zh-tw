---
title: "ISDATE (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ISDATETIME
- ISDATE_TSQL
- ISDATE
- ISDATETIME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- date and time [SQL Server], ISDATE
- validate dates times [SQL Server]
- formats [SQL Server], time
- dates [SQL Server], validate
- verify dates times [SQL Server]
- functions [SQL Server], time
- formats [SQL Server], dates
- functions [SQL Server], date and time
- time [SQL Server], functions
- time [SQL Server], validate
- ISDATE function [SQL Server]
ms.assetid: 8e2c9ee7-388a-432f-b2c9-7b398f26bf85
caps.latest.revision: 54
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0e005b11ad15170dcc2f6f45441d62e6ccc29570
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="isdate-transact-sql"></a>ISDATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回 1，如果*運算式*有效**日期**，**時間**，或**datetime**值; 否則為 0。  
  
 ISDATE 會傳回 0，如果*運算式*是**datetime2**值。  
  
 如需所有[!INCLUDE[tsql](../../includes/tsql-md.md)]日期和時間資料型別和函式，請參閱[日期和時間資料型別和函數 &#40;TRANSACT-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md). 請注意，datetime 資料範圍為 1753-01-01 到 9999-12-31，而 date 資料範圍是 0001-01-01 到 9999-12-31。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
ISDATE ( expression )  
```  
  
## <a name="arguments"></a>引數  
 *expression*  
 這是字元字串或[運算式](../../t-sql/language-elements/expressions-transact-sql.md)，可以轉換成字元字串。 此運算式的長度必須少於 4,000 個字元。 日期和時間資料類型 (但不包括 datetime 和 smalldatetime) 不允許做為 ISDATE 的引數。  
  
## <a name="return-type"></a>傳回類型  
 **int**  
  
## <a name="remarks"></a>備註  
 您搭配使用時，才是具決定性，ISDATE 才[轉換](../../t-sql/functions/cast-and-convert-transact-sql.md)函式中，如果已指定 CONVERT 樣式參數，且樣式不等於 0、 100、 9 或 109。  
  
 ISDATE 的傳回值取決於所設定的設定[SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md)， [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md)和[設定 default language 伺服器組態選項](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md)。  
  
## <a name="isdate-expression-formats"></a>ISDATE 運算式格式  
 如需 ISDATE 會傳回 1，有效格式的範例，請參閱 > 一節 「 支援字串常值格式的日期時間 」 中[datetime](../../t-sql/data-types/datetime-transact-sql.md)和[smalldatetime](../../t-sql/data-types/smalldatetime-transact-sql.md)主題。 如需其他範例，請參閱 「 引數 」 一節的輸入/輸出資料行[CAST 和 CONVERT](../../t-sql/functions/cast-and-convert-transact-sql.md)。  
  
 下表將摘要列出無效而且會傳回 0 或錯誤的輸入運算式格式。  
  
|ISDATE 運算式|ISDATE 傳回值|  
|-----------------------|-------------------------|  
|NULL|0|  
|資料類型的值列在[資料型別](../../t-sql/data-types/data-types-transact-sql.md)字元字串、 Unicode 字元字串或日期和時間以外的任何資料類型類別目錄中。|0|  
|值的**文字**， **ntext**，或**映像**資料型別。|0|  
|秒數有效位數超過 3 的任何值 (.0000 到 .0000000...n)。 ISDATE 會傳回 0，如果*運算式*是**datetime2** ，但是會傳回 1，如果*運算式*有效**datetime**值。|0|  
|混合有效日期與無效值的任何值，例如 1995-10-1a。|0|  
  
## <a name="examples"></a>範例  
  
### <a name="a-using-isdate-to-test-for-a-valid-datetime-expression"></a>A. 使用 ISDATE 測試有效的 datetime 運算式  
 下列範例會示範如何使用`ISDATE`來測試是否為有效的字元字串**datetime**。  
  
```  
IF ISDATE('2009-05-12 10:19:41.177') = 1  
    PRINT 'VALID'  
ELSE  
    PRINT 'INVALID';  
```  
  
### <a name="b-showing-the-effects-of-the-set-dateformat-and-set-language-settings-on-return-values"></a>B. 說明 SET DATEFORMAT 和 SET LANGUAGE 設定對傳回值的影響  
 下列陳述式會說明傳回成為 `SET DATEFORMAT` 和 `SET LANGUAGE` 設定結果的值。  
  
```  
/* Use these sessions settings. */  
SET LANGUAGE us_english;  
SET DATEFORMAT mdy;  
/* Expression in mdy dateformat */  
SELECT ISDATE('04/15/2008'); --Returns 1.  
/* Expression in mdy dateformat */  
SELECT ISDATE('04-15-2008'); --Returns 1.   
/* Expression in mdy dateformat */  
SELECT ISDATE('04.15.2008'); --Returns 1.   
/* Expression in myd  dateformat */  
SELECT ISDATE('04/2008/15'); --Returns 1.  
  
SET DATEFORMAT mdy;  
SELECT ISDATE('15/04/2008'); --Returns 0.  
SET DATEFORMAT mdy;  
SELECT ISDATE('15/2008/04'); --Returns 0.  
SET DATEFORMAT mdy;  
SELECT ISDATE('2008/15/04'); --Returns 0.  
SET DATEFORMAT mdy;  
SELECT ISDATE('2008/04/15'); --Returns 1.  
  
SET DATEFORMAT dmy;  
SELECT ISDATE('15/04/2008'); --Returns 1.  
SET DATEFORMAT dym;  
SELECT ISDATE('15/2008/04'); --Returns 1.  
SET DATEFORMAT ydm;  
SELECT ISDATE('2008/15/04'); --Returns 1.  
SET DATEFORMAT ymd;  
SELECT ISDATE('2008/04/15'); --Returns 1.  
  
SET LANGUAGE English;  
SELECT ISDATE('15/04/2008'); --Returns 0.  
SET LANGUAGE Hungarian;  
SELECT ISDATE('15/2008/04'); --Returns 0.  
SET LANGUAGE Swedish;  
SELECT ISDATE('2008/15/04'); --Returns 0.  
SET LANGUAGE Italian;  
SELECT ISDATE('2008/04/15'); --Returns 1.  
  
/* Return to these sessions settings. */  
SET LANGUAGE us_english;  
SET DATEFORMAT mdy;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-isdate-to-test-for-a-valid-datetime-expression"></a>C. 使用 ISDATE 測試有效的 datetime 運算式  
 下列範例會示範如何使用`ISDATE`來測試是否為有效的字元字串**datetime**。  
  
```  
IF ISDATE('2009-05-12 10:19:41.177') = 1  
    SELECT 'VALID';  
ELSE  
    SELECT 'INVALID';  
```  
  
## <a name="see-also"></a>另請參閱  
 [CAST 和 CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  


