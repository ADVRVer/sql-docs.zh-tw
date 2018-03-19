---
title: SET DATEFORMAT (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATEFORMAT
- SET DATEFORMAT
- SET_DATEFORMAT_TSQL
- DATEFORMAT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], formats
- dates [SQL Server], ordering date parts
- SET DATEFORMAT option [SQL Server]
- DATEFORMAT option [SQL Server]
- date and time [SQL Server], SET DATEFORMAT
- options [SQL Server], date
- date and time [SQL Server], DATEFORMAT
- dateparts [SQL Server], dateformat
ms.assetid: da217878-7ec4-477e-aa13-604073c948f8
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 3b1e233508eaedab627b57a3ce6938b90a9e196d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="set-dateformat-transact-sql"></a>SET DATEFORMAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  設定月份、日期與年份日期部分的順序，以解譯 **date**、**smalldatetime**、**datetime**、**datetime2** 和 **datetimeoffset** 字元字串。  
  
 如需所有 [!INCLUDE[tsql](../../includes/tsql-md.md)] 日期和時間資料類型與函式的概觀，請參閱[日期和時間資料類型與函式 &#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
SET DATEFORMAT { format | @format_var }   
```  
  
## <a name="arguments"></a>引數  
 *format* | **@***format_var*  
 這是日期部分的順序。 有效的參數為 **mdy**、**dmy**、**ymd**、**ydm**、**myd** 和 **dym**。 這個引數可以是 Unicode 或轉換成 Unicode 的雙位元組字集 (DBCS)。 U.S.美國英文的預設值是 **mdy**。 如需所有支援語言的預設 DATEFORMAT，請參閱 [sp_helplanguage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)。  
  
## <a name="remarks"></a>Remarks  
 DATEFORMAT **ydm** 不支援 **date**、**datetime2** 和 **datetimeoffset** 資料類型。  
  
 相較於 **datetime** 和 **smalldatetime** 值，DATEFORMAT 設定在解譯字元字串的作用方面可能會不同於 **date**、**datetime2** 和 **datetimeoffset** 值，端視字串格式而定。 這個設定會影響字元字串轉換成日期值以便儲存在資料庫中的解譯方式。 但是，它並不會影響儲存在資料庫中之日期資料類型值的顯示或儲存格式。  
  
 某些字元字串格式 (例如 ISO 8601) 的解譯就與 DATEFORMAT 設定無關。  
  
 SET DATEFORMAT 的設定是在執行階段進行設定，而不是在剖析階段進行設定。  
  
 SET DATEFORMAT 會覆寫 [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) 的隱含日期格式設定。  
  
## <a name="permissions"></a>Permissions  
 需要 **public** 角色的成員資格。  
  
## <a name="examples"></a>範例  
 下列範例會使用不同的日期字串當做工作階段的輸入，並搭配相同的 `DATEFORMAT` 設定。  
  
```  
-- Set date format to day/month/year.  
SET DATEFORMAT dmy;  
GO  
DECLARE @datevar datetime2 = '31/12/2008 09:01:01.1234567';  
SELECT @datevar;  
GO  
-- Result: 2008-12-31 09:01:01.123  
SET DATEFORMAT dmy;  
GO  
DECLARE @datevar datetime2 = '12/31/2008 09:01:01.1234567';  
SELECT @datevar;  
GO  
-- Result: Msg 241: Conversion failed when converting date and/or time -- from character string.  
  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [SET 陳述式 &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

