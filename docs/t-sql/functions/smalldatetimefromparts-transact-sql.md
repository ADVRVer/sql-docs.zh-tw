---
title: SMALLDATETIMEFROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
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
- SMALLDATETIMEFROMPARTS
- SMALLDATETIMEFROMPARTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SMALLDATETIMEFROMPARTS function
ms.assetid: 7467fdab-e588-419c-9e29-42caec34a9ea
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 07eaaf385e0227f3e5ddf7d0c1ee506aecca211a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="smalldatetimefromparts-transact-sql"></a>SMALLDATETIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  傳回指定日期和時間的 **smlldatetime** 值。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
SMALLDATETIMEFROMPARTS ( year, month, day, hour, minute )  
```  
  
## <a name="arguments"></a>引數  
 *year*  
 指定年份的整數運算式。  
  
 *month*  
 指定月份的整數運算式。  
  
 *day*  
 指定日期的整數運算式。  
  
 *hour*  
 指定小時的整數運算式。  
  
 *minute*  
 指定分鐘的整數運算式。  
  
## <a name="return-types"></a>傳回類型  
 **smalldatetime**  
  
## <a name="remarks"></a>Remarks  
 此函式的功能與完全初始化之 **smalldatetime** 值的建構函式類似。 如果引數無效，將會引發錯誤。 如果要求的引數為 null，即會傳回 null。  
  
 函數可以在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 伺服器和更新版伺服器上以遠端方式進行。 它在版本低於 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的伺服器上無法以遠端方式運作。  
  
## <a name="examples"></a>範例  
  
```  
SELECT SMALLDATETIMEFROMPARTS ( 2010, 12, 31, 23, 59 ) AS Result  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------------------  
2011-01-01 00:00:00  
  
(1 row(s) affected)  
```  
  

