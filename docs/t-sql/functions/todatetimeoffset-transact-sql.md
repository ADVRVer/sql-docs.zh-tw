---
title: "TODATETIMEOFFSET (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TO_DATETIMEOFFSET_TSQL
- SWITCH_TZ_TSQL
- SWITCH_TZ
- TO_DATETIMEOFFSET
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], TODATETIMEOFFSET
- TODATETIMEOFFSET function
- functions [SQL Server], time
- functions [SQL Server], date and time
- time [SQL Server], functions
ms.assetid: b5fafc08-efd4-4a3b-a0b3-068981a0a685
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 6c0ff45ae5842950d9f15d7b131ad107fba351b5
ms.contentlocale: zh-tw
ms.lasthandoff: 10/24/2017

---
# <a name="todatetimeoffset-transact-sql"></a>TODATETIMEOFFSET (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回**datetimeoffset**值，從轉譯**datetime2**運算式。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
TODATETIMEOFFSET ( expression , time_zone )  
```  
  
## <a name="arguments"></a>引數  
 *expression*  
 是[運算式](../../t-sql/language-elements/expressions-transact-sql.md)解析為[datetime2](../../t-sql/data-types/datetime2-transact-sql.md)值。  
  
> [!NOTE]  
>  運算式不能屬於類型**文字**， **ntext**，或**映像**因為這些類型無法隱含地轉換成**varchar**或**nvarchar**。  
  
 *time_zone*  
 這是代表時區時差的運算式，以分鐘為單位 (若為整數)，例如 -120，或以小時和分鐘為單位 (若為字串)，例如 ‘+13.00’。 範圍是 +14 到 -14 (以小時為單位)。 此運算式會針對指定的 time_zone 以當地時間解譯。  
  
> [!NOTE]  
>  如果運算式為字元字串，它的格式必須為 {+|-}TZH:THM。  
  
## <a name="return-type"></a>傳回類型  
 **datetimeoffset**。 小數有效位數是相同*datetime*引數。  
  
## <a name="examples"></a>範例  
  
### <a name="a-changing-the-time-zone-offset-of-the-current-date-and-time"></a>A. 變更目前日期和時間的時區時差  
 下列範例會將目前日期和時間的時區時差變更為 `-07:00` 時區。  
  
```  
DECLARE @todaysDateTime datetime2;  
SET @todaysDateTime = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDateTime, '-07:00');  
-- RETURNS 2007-08-30 15:51:34.7030000 -07:00  
```  
  
### <a name="b-changing-the-time-zone-offset-in-minutes"></a>B. 變更時區時差 (以分鐘為單位)  
 下列範例會將目前的時區變更為 `-120` 分鐘。  
  
```  
DECLARE @todaysDate datetime2;  
SET @todaysDate = GETDATE();  
SELECT TODATETIMEOFFSET (@todaysDate, -120);  
-- RETURNS 2007-08-30 15:52:37.8770000 -02:00  
```  
  
### <a name="c-adding-a-13-hour-time-zone-offset"></a>C. 在時區時差中增加 13 小時的時間  
 下列範例會在日期和時間中加入 13 小時的時區時差。  
  
```  
DECLARE @dateTime datetimeoffset(7)= '2007-08-28 18:00:30';  
SELECT TODATETIMEOFFSET (@dateTime, '+13:00');  
-- RETURNS 2007-08-28 18:00:30.0000000 +13:00  
```  
  
## <a name="see-also"></a>另請參閱  
 [CAST 和 CONVERT &#40;TRANSACT-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [日期和時間資料類型和函數 &#40;TRANSACT-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [TIME ZONE &AMP;#40;TRANSACT-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  


