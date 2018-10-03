---
title: sp_deletetracertokenhistory & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_deletetracertokenhistory
- sp_deletetracertokenhistory_TSQL
helpviewer_keywords:
- sp_deletetracertokenhistory
ms.assetid: 9ae1be14-0d2f-40b1-9d6e-22d79726abf4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6e9d8a03d44fe33c02064e8b025dc6b24cee5f2a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47808466"
---
# <a name="spdeletetracertokenhistory-transact-sql"></a>sp_deletetracertokenhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  移除追蹤 token 記錄，從[MStracer_tokens &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md)並[MStracer_history &#40;-&#41; ](../../relational-databases/system-tables/mstracer-history-transact-sql.md)系統資料表。 這個預存程序是在發行集資料庫的發行者端，或散發資料庫的散發者端執行。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_deletetracertokenhistory [ @publication = ] 'publication'   
    [ , [ @tracer_id = ] tracer_id ]  
    [ , [ @cutoff_date = ] cutoff_date ]  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>引數  
 [  **@publication=** ] **'***發行集***'**  
 這是追蹤 Token 插入其中之發行集的名稱。 *發行集*已**sysname**，沒有預設值。  
  
 [  **@tracer_id=** ] *tracer_id*  
 這是要刪除之追蹤 Token 的識別碼。 *tracer_id*已**int**，預設值是 NULL。 如果**null**，則會刪除屬於發行集的所有追蹤 token。  
  
 [  **@cutoff_date=** ] *cutoff_date*  
 指定截止日期，以便移除在這個日期之前插入發行集的所有追蹤 Token。 *cutoff_date*是 datetime，預設值是 NULL。  
  
 [  **@publisher=** ] **'***發行者***'**  
 發行者的名稱。 *發行者*已**sysname**，預設值是 NULL。  
  
> [!NOTE]  
>  這個參數應該只能指定為非[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]發行者。  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 發行集資料庫的名稱。 *publisher_db*已**sysname**，預設值是 NULL。 如果預存程序執行於發行者端，則會忽略這個參數。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_deletetracertokenhistory**用於異動複寫中。  
  
 執行時**sp_deletetracertokenhistory**，您只能指定其中一個*tracer_id*或是*cutoff_date*。 當您同時指定這兩個參數時，會發生錯誤。  
  
 如果您不會執行**sp_deletetracertokenhistory**若要移除追蹤 token 中繼資料，將會移除資訊時定期排程的記錄清除工作。  
  
 您可以藉由執行判斷追蹤 token 識別碼[sp_helptracertokens &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md)或藉由查詢[MStracer_tokens &#40;-&#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md)系統資料表。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定伺服器角色**db_owner**固定資料庫角色，在發行集資料庫中，或**db_owner**固定的資料庫或**replmonitor**散發資料庫中的角色可以執行**sp_deletetracertokenhistory**。  
  
## <a name="see-also"></a>另請參閱  
 [針對異動複寫測量延遲及驗證連線](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [sp_helptracertokenhistory &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md)  
  
  
