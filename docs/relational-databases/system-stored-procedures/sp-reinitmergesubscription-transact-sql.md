---
title: sp_reinitmergesubscription (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_reinitmergesubscription_TSQL
- sp_reinitmergesubscription
helpviewer_keywords:
- sp_reinitmergesubscription
ms.assetid: 249a4048-e885-48e0-a92a-6577f59de751
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9b9928305b3fec528dc2820fed275c321cc2cdad
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="spreinitmergesubscription-transact-sql"></a>sp_reinitmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  將合併訂閱標示為在下次執行合併代理程式時重新初始化。 這個預存程序執行於發行集資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_reinitmergesubscription [ [ @publication = ] 'publication'  
    [ , [ @subscriber = ] 'subscriber'  
    [ , [ @subscriber_db = ] 'subscriber_db'  
    [ , [ @upload_first = ] 'upload_first'  
```  
  
## <a name="arguments"></a>引數  
 [ **@publication =** ] **'***publication***'**  
 這是發行集的名稱。 *發行集*是**sysname**，預設值是**所有**。  
  
 [  **@subscriber =** ] **'***訂閱者***'**  
 這是訂閱者的名稱。 *訂閱者*是**sysname**，預設值是**所有**。  
  
 [  **@subscriber_db =** ] **'***subscriber_db***'**  
 這是訂閱者資料庫的名稱。 *subscriber_db*是**sysname**，預設值是**所有**。  
  
 [  **@upload_first =** ] **'***upload_first***'**  
 這是指在訂閱重新初始化之前，是否上傳在訂閱者端的變更。 *upload_first*是**nvarchar （5)**，預設值是 FALSE。 如果**true**，訂閱重新初始化之前上傳變更。 如果**false**，不會上傳變更。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_reinitmergesubscription**用於合併式複寫中。  
  
 **sp_reinitmergesubscription**可以呼叫從 「 發行者 」，若要重新初始化合併訂閱。 我們建議您也要重新執行快照集代理程式。  
  
 如果您新增、卸除或變更參數化篩選，在重新初始化期間，便無法將訂閱者的暫止變更上傳到發行者。 如果您要上傳暫止變更，請在變更篩選之前，同步處理所有訂閱。  
  
## <a name="example"></a>範例  
 [!code-sql[HowTo#sp_reinitmergepushsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergesubscripti_1.sql)]  
  
## <a name="example"></a>範例  
 [!code-sql[HowTo#sp_reinitmergepushsubwithupload](../../relational-databases/replication/codesnippet/tsql/sp-reinitmergesubscripti_2.sql)]  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色或**db_owner**固定的資料庫角色可以執行**sp_reinitmergesubscription**。  
  
## <a name="see-also"></a>另請參閱  
 [重新初始化訂閱](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
