---
title: sys.periods (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 25e66ed3-2270-4c5c-9f5a-2c0f165a57ca
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6e018e33ffa76fb162fd2020ba8ff043f295aa16
ms.sourcegitcommit: 3cd6068f3baf434a4a8074ba67223899e77a690b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2018
ms.locfileid: "49461924"
---
# <a name="sysperiods-transact-sql"></a>sys.periods & Amp;#40;transact-SQL&AMP;#41
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  傳回針對已定義的期間每個資料表的資料列。  
  
|資料行標頭|資料類型|描述|  
|-------------------|---------------|-----------------|  
|NAME|**sysname**|期間的名稱|  
|period_type|**tinyint**|數字的值，表示期間的類型：<br /><br /> 1 = 系統時段|  
|period_type_desc|**nvarchar(60)**|文字的描述資料行的類型：<br /><br /> SYSTEM_TIME_PERIOD|  
|object_id|**int**|包含 period_type 資料行之資料表的識別碼|  
|start_column_id|**int**|定義的週期範圍下限資料行的識別碼|  
|end_column_id|**int**|定義期間的範圍上限資料行的識別碼|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [系統檢視表&#40;Transact SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [物件目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.all_columns &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.system_columns &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)   
 [查詢 SQL Server 系統目錄常見問題集](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [時態表](../../relational-databases/tables/temporal-tables.md)  
  
  
