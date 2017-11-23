---
title: "sp_droppublication (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_droppublication_TSQL
- sp_droppublication
helpviewer_keywords: sp_droppublication
ms.assetid: b52b37e6-4fec-40cf-abba-7dce4ff395fd
caps.latest.revision: "35"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 52e49b72c1cac9b043b0a31113f2a03f46a6adf1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="spdroppublication-transact-sql"></a>sp_droppublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  卸除發行集及其相關快照集代理程式。 在卸除發行集之前，必須先卸除所有訂閱。 發行集中的發行項會自動卸除。 這個預存程序執行於發行集資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_droppublication [ @publication= ] 'publication'   
    [ , [ @ignore_distributor = ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>引數  
 [  **@publication=** ] **'***發行集***'**  
 這是要卸除的發行集名稱。 *發行集*是**sysname**，沒有預設值。 如果**所有**指定，則會卸除發行集資料庫，除了含有訂閱的所有發行集。  
  
 [  **@ignore_distributor =** ] *ignore_distributor*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_droppublication**用於快照式複寫和異動複寫。  
  
 **sp_droppublication**遞迴卸除發行集相關聯的所有發行項，然後再卸除發行集本身。 如果發行集有一或多項訂閱，便不能移除它。 如需如何移除訂用帳戶資訊，請參閱[Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md)和[Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md)。  
  
 執行**sp_droppublication**卸除發行集不會移除已發行的物件發行集資料庫或從訂閱資料庫對應的物件。 請使用 DROP\<物件 > 來手動移除這些物件，如有必要。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色可以執行**sp_droppublication**。  
  
## <a name="examples"></a>範例  
 [!code-sql[HowTo#sp_droppublication](../../relational-databases/replication/codesnippet/tsql/sp-droppublication-trans_1.sql)]  
  
## <a name="see-also"></a>請參閱＜  
 [刪除發行集](../../relational-databases/replication/publish/delete-a-publication.md)   
 [sp_addpublication &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_helppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)   
 [複寫預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
