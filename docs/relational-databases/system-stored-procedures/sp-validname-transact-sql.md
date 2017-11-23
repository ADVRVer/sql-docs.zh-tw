---
title: "sp_validname (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_validname
- sp_validname_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_validname
ms.assetid: d51c53c2-1332-407f-b725-4983f2e710eb
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5e010d546f38b315624a8a905e8042792f6bed2c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="spvalidname-transact-sql"></a>sp_validname (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  檢查有效的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 識別碼名稱。 所有非二進位和非零資料，包括使用可儲存 Unicode 資料**nchar**， **nvarchar**，或**ntext**資料型別，都會獲得接受，成為有效的字元識別項名稱。  
  
||  
|-|  
|**適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [目前版本](http://go.microsoft.com/fwlink/p/?LinkId=299658))、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。|  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_validname [@name =] 'name'   
     [, [@raise_error =] raise_error]  
```  
  
## <a name="arguments"></a>引數  
 [  **@name=** ] **'***名稱***'**  
 名稱[識別碼](../../relational-databases/databases/database-identifiers.md)用來檢查有效性。 *名稱*是**sysname**，沒有預設值。 *名稱*不能是 NULL、 不可為空字串，也不可包含二進位零字元。  
  
 [  **@raise_error=** ] *raise_error*  
 指定是否要引發錯誤。 *raise_error*是**元**，預設值是 1。 這表示錯誤將會出現。 如果是 0，則表示不會出現任何錯誤訊息。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="permissions"></a>Permissions  
 需要 **public** 角色的成員資格。  
  
## <a name="see-also"></a>請參閱＜  
 [Database Engine 預存程序 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [資料類型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [NCHAR &#40;TRANSACT-SQL &#41;](../../t-sql/functions/nchar-transact-sql.md)   
 [nchar 和 nvarchar &#40;TRANSACT-SQL &#41;](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)   
 [ntext、 text，映像 &#40;TRANSACT-SQL &#41;](../../t-sql/data-types/ntext-text-and-image-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
