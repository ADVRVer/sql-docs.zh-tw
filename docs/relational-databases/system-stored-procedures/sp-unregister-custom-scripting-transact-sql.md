---
title: "sp_unregister_custom_scripting (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_unregister_custom_scripting_TSQL
- sp_unregister_custom_scripting
helpviewer_keywords:
- sp_unregister_custom_scripting
ms.assetid: b6e9e0d2-9144-434d-88af-4874f2582399
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fce6b2d16e732b76519cb0fbf66a16ca5db6928f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="spunregistercustomscripting-transact-sql"></a>sp_unregister_custom_scripting (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  這個預存程序會移除使用者定義自訂預存程序或[!INCLUDE[tsql](../../includes/tsql-md.md)]所註冊的指令碼檔案[sp_register_custom_scripting](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md)。 這個預存程序執行於發行集資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_unregister_custom_scripting [ @type  = ] 'type'  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>引數  
 [  **@type**  =] **'***類型***'**  
 這是要移除之自訂預存程序或指令碼的類型。 *型別*是**varchar （16)**，沒有預設值，它可以是下列值之一。  
  
|值|Description|  
|-----------|-----------------|  
|**插入**|註冊的自訂預存程序或指令碼，是在複寫 INSERT 陳述式時執行。|  
|**更新**|註冊的自訂預存程序或指令碼，是在複寫 UPDATE 陳述式時執行。|  
|**刪除**|註冊的自訂預存程序或指令碼，是在複寫 DELETE 陳述式時執行。|  
|**custom_script**|註冊的自訂預存程序或指令碼，是在資料定義語言 (DDL) 觸發程序結尾執行。|  
  
 [  **@publication**  =] **'***發行集***'**  
 要移除之自訂預存程序或指令碼的發行集名稱。 *發行集*是**sysname**，預設值是 NULL。  
  
 [  **@article**  =] **'***文章***'**  
 要移除之自訂預存程序或指令碼的發行項名稱。 *發行項*是**sysname**，預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_unregister_custom_scripting**用於快照式和異動複寫。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定伺服器角色、 **db_owner**固定資料庫角色或**db_ddladmin**固定的資料庫角色可以執行**sp_unregister_custom_scripting**。  
  
## <a name="see-also"></a>請參閱＜  
 [sp_register_custom_scripting &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md)  
  
  
