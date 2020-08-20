---
description: sp_mergearticlecolumn (Transact-SQL)
title: sp_mergearticlecolumn (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_mergearticlecolumn
- sp_mergearticlecolumn_TSQL
helpviewer_keywords:
- sp_mergearticlecolumn
ms.assetid: b4f2b888-e094-4759-a472-d893638995eb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d1036539564811e25be7764a3afb1106e05b1f37
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473964"
---
# <a name="sp_mergearticlecolumn-transact-sql"></a>sp_mergearticlecolumn (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  進行合併式發行集的垂直資料分割。 這個預存程序執行於發行集資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_mergearticlecolumn [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @column = ] 'column'  
    [ , [ @operation = ] 'operation'   
    [ , [ @schema_replication = ] 'schema_replication' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]   
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]   
```  
  
## <a name="arguments"></a>引數  
`[ @publication = ] 'publication'` 這是發行集的名稱。 *發行* 集是 **sysname**，沒有預設值。  
  
`[ @article = ] 'article'` 這是發行集中的發行項名稱。 *文章* 是 **sysname**，沒有預設值。  
  
`[ @column = ] 'column'` 識別用來建立垂直資料分割的資料行。 資料*行*是**sysname**，預設值是 Null。 如果是 NULL 和 `@operation = N'add'`，依預設，會將來源資料表中所有的資料行加入至發行項。 當作業設為**drop***時，資料**行*不可以是 Null。 若要從發行項排除資料行，請執行**sp_mergearticlecolumn**並指定資料*行*，以及 `@operation = N'drop'` 要從指定的*article*發行項中移除的每個資料行。  
  
`[ @operation = ] 'operation'` 這是複寫狀態。 *操作* 是 **Nvarchar (4) **，預設值是 ADD。 **add** 會標示覆寫的資料行。 **drop** 會清除資料行。  
  
`[ @schema_replication = ] 'schema_replication'` 指定當合併代理程式執行時，將傳播架構變更。 *schema_replication* 是 **Nvarchar (5) **，預設值是 FALSE。  
  
> [!NOTE]  
>  *Schema_replication*只支援**FALSE** 。  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` 啟用或停用使快照集失效的能力。 *force_invalidate_snapshot* 是 **bit**，預設值是 **0**。  
  
 **0** 指定合併發行項的變更不會使快照集失效。  
  
 **1** 指定合併發行項的變更可能使快照集失效，如果是這種情況， **1** 值就會提供新快照集的許可權。  
  
`[ @force_reinit_subscription = ]force_reinit_subscription_` 啟用或停用訂用帳戶重新初始化能力的能力。 *force_reinit_subscription* 是 bit，預設值是 **0**。  
  
 **0** 指定合併發行項的變更不會使訂閱重新初始化。  
  
 **1** 指定合併發行項的變更可能會導致訂閱重新初始化，如果是這種情況， **1** 值就會提供將發生之訂閱重新初始化的許可權。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或 **1** (失敗)   
  
## <a name="remarks"></a>備註  
 **sp_mergearticlecolumn** 用於合併式複寫中。  
  
 如果使用自動識別範圍管理，便無法從發行項中卸除識別欄位。 如需詳細資訊，請參閱[複寫識別資料欄](../../relational-databases/replication/publish/replicate-identity-columns.md)。  
  
 如果應用程式在建立初始快照集之後，設定新的垂直資料分割，就必須產生新的快照集，並重新套用至每項訂閱上。 當執行下一個已排程的快照集及散發或合併代理程式時，會套用快照集。  
  
 如果使用資料列追蹤執行衝突偵測 (預設值)，基底資料表最多可以包含 1,024 個資料行，但必須從發行項篩選資料行，以便發行最多 246 個資料行。 如果使用資料行追蹤，則基底資料表可包括的資料行數上限為 246。  
  
## <a name="example"></a>範例  
 [!code-sql[HowTo#sp_AddMergeArticle](../../relational-databases/replication/codesnippet/tsql/sp-mergearticlecolumn-tr_1.sql)]  
  
## <a name="permissions"></a>權限  
 只有 **系統管理員（sysadmin** ）固定伺服器角色或 **db_owner** 固定資料庫角色的成員，才能夠執行 **sp_mergearticlecolumn**。  
  
## <a name="see-also"></a>另請參閱  
 [定義和修改合併發行項之間的聯結篩選](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [針對合併發行項定義及修改參數化資料列篩選](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [篩選發行的資料](../../relational-databases/replication/publish/filter-published-data.md)   
 [複寫預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
