---
title: "sys.security_predicates (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server 2016 Preview
f1_keywords:
- SYS.SECURITY_PREDICATES
- SECURITY_PREDICATES
- SECURITY_PREDICATES_TSQL
- SYS.SECURITY_PREDICATES_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.security_predicates catalog view
- security_predicates catalog view
ms.assetid: c7a2f28c-98da-463d-8b8a-8e5619e2c6a6
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 472c9c6504b010d6abfea0d3161ada98e9e0f5f6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="syssecuritypredicates-transact-sql"></a>sys.security_predicates (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  傳回資料庫中的每個安全性述詞的資料列。  
  
|資料行名稱|資料類型|說明|  
|-----------------|---------------|-----------------|  
|object_id|**int**|包含這個述詞之安全性原則的識別碼。|  
|security_predicate_id|**int**|這個安全性原則內的述詞識別碼。|  
|target_object_id|**int**|安全性述詞所繫結之物件的識別碼。|  
|predicate_definition|**nvarchar(max)**|用來做為安全性述詞之函數的完整名稱，包括引數。 請注意，`schema.function`名稱可正規化 （也就是逸出） 以及一致性的文字中的任何其他項目。 例如：<br /><br /> `[dbo].[fn_securitypredicate]([wing], [startTime], [endTime])`|  
|predicate_type|**int**|安全性原則所使用的述詞的類型：<br /><br /> 0 = 篩選器述詞<br /><br /> 1 = BLOCK 述詞|  
|predicate_type_desc|**nvarchar （60)**|安全性原則所使用的述詞的類型：<br /><br /> FILTER<br /><br /> 區塊|  
|operation (作業)|**int**|指定述詞的作業類型：<br /><br /> NULL = 適用的所有作業<br /><br /> 1 = AFTER INSERT<br /><br /> 2 = 更新之後<br /><br /> 3 = 更新之前<br /><br /> 4 = 之前刪除|  
|operation_desc|**nvarchar （60)**|指定述詞的作業類型：<br /><br /> NULL<br /><br /> 在插入之後<br /><br /> AFTER UPDATE<br /><br /> 更新之前<br /><br /> 刪除前|  
  
## <a name="permissions"></a>Permissions  
 具有主體**ALTER ANY SECURITY POLICY**權限可以存取這份目錄檢視，以及任何人使用中的所有物件**VIEW DEFINITION**物件上。  
  
## <a name="see-also"></a>請參閱＜  
 [資料列層級安全性](../../relational-databases/security/row-level-security.md)   
 [sys.security_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [CREATE SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [安全性目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [主體 &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
