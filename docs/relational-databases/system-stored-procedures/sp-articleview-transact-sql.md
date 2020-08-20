---
description: sp_articleview (Transact-SQL)
title: sp_articleview (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_articleview
- sp_articleview_TSQL
helpviewer_keywords:
- sp_articleview
ms.assetid: a3d63fd6-f360-4a2f-8a82-a0dc15f650b3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5b1d18b8e4249f2948dccb3b042742afe0c0f54a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464526"
---
# <a name="sp_articleview-transact-sql"></a>sp_articleview (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  建立在進行資料表的垂直或水平篩選時，用來定義所發行之發行項的檢視。 這份檢視用來作為目的地資料表之結構描述和資料的篩選來源。 這個預存程序只能修改未訂閱的發行項。 這個預存程序執行於發行集資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_articleview [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @view_name = ] 'view_name']  
    [ , [ @filter_clause = ] 'filter_clause']  
    [ , [ @change_active = ] change_active ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @refreshsynctranprocs = ] refreshsynctranprocs ]  
    [ , [ @internal = ] internal ]  
```  
  
## <a name="arguments"></a>引數  
`[ @publication = ] 'publication'` 這是包含發行項的發行集名稱。 *發行* 集是 **sysname**，沒有預設值。  
  
`[ @article = ] 'article'` 這是發行項的名稱。 *文章* 是 **sysname**，沒有預設值。  
  
`[ @view_name = ] 'view_name'` 這是定義已發行之發行項的視圖名稱。 *view_name* 是 **Nvarchar (386) **，預設值是 Null。  
  
`[ @filter_clause = ] 'filter_clause'` 這是定義水準篩選之) 子句的限制 (。 當輸入限制子句時，請省略 WHERE 關鍵字。 *filter_clause* 是 **Ntext**，預設值是 Null。  
  
`[ @change_active = ] change_active` 允許修改具有訂閱之發行集的資料行。 *change_active* 是 **int**，預設值是 **0**。 如果為 **0**，則不會變更資料行。 如果是 **1**，就可以在具有訂閱的使用中發行項上建立或重新建立 views。  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` 認可這個預存程式所採取的動作可能使現有的快照集失效。 *force_invalidate_snapshot* 是 **bit**，預設值是 **0**。  
  
 **0** 指定發行項的變更不會使快照集失效。 如果預存程序偵測到變更需要新的快照集，就會發生錯誤，且不會進行任何變更。  
  
 **1** 指定發行項的變更可能使快照集失效，如果有現有的訂閱需要新的快照集，則會將現有快照集的許可權標示為已淘汰，並產生新的快照集。  
  
`[ @force_reinit_subscription = ] _force_reinit_subscription_` 認可這個預存程式所採取的動作可能需要重新初始化現有的訂閱。 *force_reinit_subscription* 是 **bit** ，預設值是 **0**。  
  
 **0** 指定發行項的變更不會使訂閱重新初始化。 如果預存程序偵測到變更需要重新初始化訂閱，就會發生錯誤，且不會進行任何變更。  
  
 **1** 指定發行項的變更會使現有的訂閱重新初始化，且會提供將發生之訂閱重新初始化的許可權。  
  
`[ @publisher = ] 'publisher'` 指定非 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 發行者。 *publisher* 是 **sysname**，預設值是 Null。  
  
> [!NOTE]  
>  從發行者發行時，不應使用「*發行者*」 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
`[ @refreshsynctranprocs = ] refreshsynctranprocs` 這是指是否自動重新建立用來同步處理複寫的預存程式。 *refreshsynctranprocs* 是 **bit**，預設值是1。  
  
 **1** 表示重新建立預存程式。  
  
 **0** 表示不會重新建立預存程式。  
  
`[ @internal = ] internal` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或 **1** (失敗)   
  
## <a name="remarks"></a>備註  
 **sp_articleview**建立定義已發行之發行項的視圖，並在[sysarticles &#40;transact-sql&#41;](../../relational-databases/system-tables/sysarticles-transact-sql.md)資料表的**sync_objid**資料行中插入此視圖的識別碼，並將限制子句的文字插入**filter_clause**資料行中。 如果所有資料行都已複寫且沒有**filter_clause**，則[sysarticles &#40;transact-sql&#41;](../../relational-databases/system-tables/sysarticles-transact-sql.md)資料表中的**sync_objid**會設定為基表的識別碼，而且不需要使用**sp_articleview** 。  
  
 若要發行垂直篩選的資料表 (也就是，若要篩選資料行) 第一次執行不含*sync_object*參數的**sp_addarticle** ，請針對要複寫的每個資料行執行[sp_articlecolumn &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)一次 (定義垂直篩選) ，然後執行**sp_articleview**來建立定義已發行之發行項的視圖。  
  
 若要發行水準篩選的資料表 (也就是) 篩選資料列，請執行 sp_addarticle 不含*篩選*參數[&#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) 。 執行 [sp_articlefilter &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)，並提供包含 *filter_clause*在內的所有參數。 然後執行 **sp_articleview**，並提供所有參數（包括相同的 *filter_clause*）。  
  
 若要發行垂直和水準篩選的資料表，請在不使用*sync_object*或*篩選*參數的情況下執行[sp_addarticle &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) 。 針對要複寫的每個資料行執行 [sp_articlecolumn &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) 一次，然後執行 [sp_articlefilter &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) 和 **sp_articleview**。  
  
 如果發行項已經有定義已發行之發行項的視圖， **sp_articleview** 會卸載現有的視圖，並自動建立一個新的視圖。 如果視圖是以手動方式建立 (在 sysarticles 中 **輸入** ， [&#40;transact-sql&#41;](../../relational-databases/system-tables/sysarticles-transact-sql.md) 為 **5**) ，則不會卸載現有的視圖。  
  
 如果您建立自訂篩選預存程式以及手動定義已發行之發行項的視圖，則請勿執行 **sp_articleview**。 相反地，請提供這些做為 *篩選* 和 *sync_object* 參數，以 [sp_addarticle &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)以及適當的 *類型* 值。  
  
## <a name="example"></a>範例  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articleview-transact-_1.sql)]  
  
## <a name="permissions"></a>權限  
 只有 **系統管理員（sysadmin** ）固定伺服器角色或 **db_owner** 固定資料庫角色的成員，才能夠執行 **sp_articleview**。  
  
## <a name="see-also"></a>另請參閱  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [定義及修改靜態資料列篩選](../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [sp_addarticle &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlefilter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)   
 [sp_changearticle &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [複寫預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
