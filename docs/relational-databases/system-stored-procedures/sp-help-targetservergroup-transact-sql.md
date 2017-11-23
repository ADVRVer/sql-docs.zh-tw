---
title: "sp_help_targetservergroup (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_targetservergroup_TSQL
- sp_help_targetservergroup
dev_langs: TSQL
helpviewer_keywords: sp_help_targetservergroup
ms.assetid: ec3a4a68-b591-431c-9518-053ede522d0c
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7a814f05cda311cd57c23b1b9a272797b22c8c32
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="sphelptargetservergroup-transact-sql"></a>sp_help_targetservergroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  列出指定群組中的所有目標伺服器。 如果未指定任何群組，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會傳回所有目標伺服器群組的相關資訊。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_help_targetservergroup  
    [ [ @name = ] 'name' ]  
```  
  
## <a name="argument"></a>引數  
 [  **@name=** ] **'***名稱***'**  
 這是要傳回資訊的目標伺服器群組名稱。 *名稱*是**sysname**，預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**servergroup_id**|**int**|伺服器群組的識別碼|  
|**name**|**sysname**|伺服器群組的名稱|  
  
## <a name="permissions"></a>Permissions  
 若要執行此程序的權限預設為**sysadmin**固定的伺服器角色。  
  
## <a name="examples"></a>範例  
  
### <a name="a-listing-information-for-all-target-server-groups"></a>A. 列出所有目標伺服器群組的資訊  
 這個範例會列出所有目標伺服器群組的資訊。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_targetservergroup ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-target-server-group"></a>B. 列出特定目標伺服器群組的資訊  
 這個範例列出 `Servers Maintaining Customer Information` 目標伺服器群組的資訊。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_targetservergroup   
    N'Servers Maintaining Customer Information' ;  
GO  
```  
  
## <a name="see-also"></a>請參閱＜  
 [sp_add_targetservergroup &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql.md)   
 [sp_delete_targetservergroup &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql.md)   
 [sp_update_targetservergroup &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
