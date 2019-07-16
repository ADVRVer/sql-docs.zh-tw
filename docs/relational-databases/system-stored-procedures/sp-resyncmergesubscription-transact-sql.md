---
title: sp_resyncmergesubscription (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_resyncmergesubscription_TSQL
- sp_resyncmergesubscription
helpviewer_keywords:
- sp_resyncmergesubscription
ms.assetid: e04d464a-60ab-4b39-a710-c066025708e6
author: stevestein
ms.author: sstein
ms.openlocfilehash: e77488a379543dd6f2749a07048fa67a92d530ee
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041027"
---
# <a name="spresyncmergesubscription-transact-sql"></a>sp_resyncmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  將合併訂閱重新同步處理到您指定的已知驗證狀態。 這可讓您將訂閱資料庫強制聚合或同步處理到某個特定的時間點，如上次驗證成功或指定的日期。 當利用這個方法來重新同步處理訂閱時，不會重新套用快照集。 快照式複寫訂閱或異動複寫訂閱不使用這個預存程序。 這個預存程序執行於發行集資料庫的發行者端，或訂閱資料庫的訂閱者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_resyncmergesubscription [ [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
        , [ @publication = ] 'publication'   
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
    [ , [ @resync_type = ] resync_type ]  
    [ , [ @resync_date_str = ] resync_date_string ]  
```  
  
## <a name="arguments"></a>引數  
`[ @publisher = ] 'publisher'` 是 「 發行者 」 的名稱。 *發行者*已**sysname**，預設值是 NULL。 如果預存程序執行於發行者端，NULL 值就有效。 如果預存程序執行於訂閱者端，就必須指定發行者。  
  
`[ @publisher_db = ] 'publisher_db'` 是發行集資料庫的名稱。 *publisher_db*已**sysname**，預設值是 NULL。 如果預存程序執行於發行集資料庫中的發行者端，NULL 值就有效。 如果預存程序執行於訂閱者端，就必須指定發行者。  
  
`[ @publication = ] 'publication'` 是發行集名稱。 *發行集*已**sysname**，沒有預設值。  
  
`[ @subscriber = ] 'subscriber'` 是訂閱者的名稱。 *訂閱者*已**sysname**，預設值是 NULL。 如果預存程序執行於訂閱者端，NULL 值就有效。 如果預存程序執行於發行者端，就必須指定訂閱者。  
  
`[ @subscriber_db = ] 'subscriber_db'` 是訂閱資料庫的名稱。 *subscription_db*已**sysname**，預設值是 NULL。 如果預存程序執行於訂閱資料庫中的訂閱者端，NULL 值就有效。 如果預存程序執行於發行者端，就必須指定訂閱者。  
  
`[ @resync_type = ] resync_type` 定義何時應該開始重新同步。 *resync_type*已**int**，而且可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**0**|從初始快照集之後開始同步處理。 這是最需要資源的選項，因為訂閱者會套用初始快照集之後的所有變更。|  
|**1**|從上次驗證成功之後開始同步處理。 訂閱者會重新套用上次驗證成功之後所引發的所有新的或不完整的層代 (Generation)。|  
|**2**|從所提供的日期開始同步處理*resync_date_str*。 訂閱者會重新套用這個日期之後所引發的所有新的或不完整的層代 (Generation)。|  
  
`[ @resync_date_str = ] resync_date_string` 定義何時應該開始重新同步的日期。 *resync_date_string*已**nvarchar(30)** ，預設值是 NULL。 使用這個參數時*resync_type*的值**2**。 指定的資料會轉換成其對等**datetime**值。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_resyncmergesubscription**用於合併式複寫中。  
  
 值為**0** for *resync_type*參數，將所有的變更重新套用初始快照集之後，可能會耗費資源，但可能不會比完整重新初始化。 例如，如果初始快照集是一個月前所傳遞的，這個值會造成重新套用上個月以來的資料。 如果初始快照集包含 1 GB 資料，但上個月以來的變更量含有 2 MB 已變更的資料，重新套用這些資料的效率，可能比重新套用完整的 1 GB 快照集好。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色或**db_owner**固定的資料庫角色可以執行**sp_resyncmergesubscription**。  
  
## <a name="see-also"></a>另請參閱  
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
