---
title: sp_restoremergeidentityrange & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_restoremergeidentityrange_TSQL
- sp_restoremergeidentityrange
helpviewer_keywords:
- sp_restoremergeidentityrange
ms.assetid: 7923e422-2748-40c0-b5a8-6410c48d5b70
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3c5e07b7dde01cc8e8a0c1289a25c8fd3de83aae
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792126"
---
# <a name="sprestoremergeidentityrange-transact-sql"></a>sp_restoremergeidentityrange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  這個預存程序用來更新識別範圍的指派。 它會確定自動識別範圍管理在發行者從備份還原之後，有正常運作。 這個預存程序執行於發行集資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_restoremergeidentityrange [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>引數  
 [ **@publication** = ] **'***publication***'**  
 這是發行集的名稱。 *發行集*已**sysname**，預設值是**所有**。 當指定時，只有該發行集的識別範圍才會還原。  
  
 [ **@article** =] **'***文章***'**  
 這是發行項的名稱。 *發行項*已**sysname**，預設值是**所有**。 當指定時，只有該發行項的識別範圍才會還原。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_restoremergeidentityrange**搭配合併式複寫。  
  
 **sp_restoremergeidentityrange**取得最大的識別範圍配置資訊從散發者，並更新中的值**max_used**資料行[MSmerge_identity_range_allocations &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/msmerge-identity-range-allocations-transact-sql.md)使用自動識別範圍管理之發行項。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色或**db_owner**固定的資料庫角色可以執行**sp_restoremergeidentityrange**。  
  
## <a name="see-also"></a>另請參閱  
 [sp_addmergearticle &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [複寫識別資料行](../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
  
