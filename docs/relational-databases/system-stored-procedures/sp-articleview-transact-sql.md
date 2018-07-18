---
title: sp_articleview (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_articleview
- sp_articleview_TSQL
helpviewer_keywords:
- sp_articleview
ms.assetid: a3d63fd6-f360-4a2f-8a82-a0dc15f650b3
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 68d7b62faa098eedb77bf1576020f01c090fcbd5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32993385"
---
# <a name="sparticleview-transact-sql"></a>sp_articleview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [ **@publication=**] **'***publication***'**  
 這是發行項所在的發行集名稱。 *發行集*是**sysname**，沒有預設值。  
  
 [  **@article=**] **'***文章***'**  
 這是發行項的名稱。 *發行項*是**sysname**，沒有預設值。  
  
 [  **@view_name=**] **'***view_name***'**  
 這是定義已發行之發行項的檢視名稱。 *view_name*是**nvarchar （386)**，預設值是 NULL。  
  
 [  **@filter_clause=**] **'***filter_clause***'**  
 這是定義水平篩選的限制 (WHERE) 子句。 當輸入限制子句時，請省略 WHERE 關鍵字。 *filter_clause*是**ntext**，預設值是 NULL。  
  
 [  **@change_active =** ] *change_active*  
 可讓您修改已有訂閱之發行集的資料行。 *change_active*是**int**，預設值是**0**。 如果**0**，不會變更資料行。 如果**1**，可建立或擁有訂用帳戶的使用中發行項上重新建立檢視。  
  
 [  **@force_invalidate_snapshot =** ] *force_invalidate_snapshot*  
 認可這個預存程序所採取的動作可能使現有的快照集失效。 *force_invalidate_snapshot*是**元**，預設值是**0**。  
  
 **0**指定發行項的變更不會使快照集失效。 如果預存程序偵測到變更需要新的快照集，就會發生錯誤，且不會進行任何變更。  
  
 **1**指定發行項的變更可能使快照集失效，如果有現有的訂閱需要新的快照集，提供權限將會標示為已棄用之現有快照集和產生新的快照集。  
  
 [  **@force_reinit_subscription =]** *force_reinit_subscription*  
 認可這個預存程序所採取的動作可能需要重新初始化現有的訂閱。 *force_reinit_subscription*是**元**預設值是**0**。  
  
 **0**指定發行項的變更不會使訂閱重新初始化。 如果預存程序偵測到變更需要重新初始化訂閱，就會發生錯誤，且不會進行任何變更。  
  
 **1**指定發行項的變更會使現有的訂閱重新初始化，並提供發生訂閱重新初始化的權限。  
  
 [ **@publisher**=] **'***發行者***'**  
 指定非[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]發行者。 *發行者*是**sysname**，預設值是 NULL。  
  
> [!NOTE]  
>  *發行者*不應從發行時[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]發行者。  
  
 [ **@refreshsynctranprocs** =] *refreshsynctranprocs*  
 這是指是否自動重新建立用來同步處理複寫的預存程序。 *refreshsynctranprocs*是**元**，預設值是 1。  
  
 **1**表示預存程序會重新建立。  
  
 **0**表示不重新建立預存程序。  
  
 [ **@internal**=]*內部*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_articleview**建立之檢視的定義已發行的發行項，並將插入的此檢視的識別碼**sync_objid**資料行[sysarticles &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md)資料表，並限制子句中的文字插入**filter_clause**資料行。 如果複寫所有資料行，而且沒有任何**filter_clause**、 **sync_objid**中[sysarticles &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md)資料表設定的識別碼基底資料表，以及使用**sp_articleview**並非必要。  
  
 若要發行垂直篩選的資料表 (也就是篩選資料行) 第一次執行**sp_addarticle**沒有*sync_object*參數，執行[sp_articlecolumn &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)每個資料行複寫 （定義垂直篩選），然後再執行一次**sp_articleview**來建立定義已發行的發行項的檢視。  
  
 若要發行水平篩選的資料表 （也就是篩選資料列），執行[sp_addarticle &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)沒有*篩選*參數。 執行[sp_articlefilter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)，提供所有參數，包括*filter_clause*。 然後執行**sp_articleview**，提供包括相同的所有參數*filter_clause*。  
  
 若要發行垂直和水平篩選的資料表，執行[sp_addarticle &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)沒有*sync_object*或*篩選*參數。 執行[sp_articlecolumn &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)一次複寫，每個資料行，然後執行[sp_articlefilter &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)和**sp_articleview**。  
  
 如果發行項已經有定義已發行之發行項的檢視**sp_articleview**卸除現有的檢視，並會自動建立一個新。 如果以手動方式建立檢視 (**類型**中[sysarticles &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md)是**5**)，不卸除現有的檢視。  
  
 如果您建立自訂篩選預存程序和檢視，以手動方式定義發行的項時，不會執行**sp_articleview**。 相反地，提供這些做為*篩選*和*sync_object*參數[sp_addarticle &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)，以及適當*類型*值。  
  
## <a name="example"></a>範例  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articleview-transact-_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色或**db_owner**固定的資料庫角色可以執行**sp_articleview**。  
  
## <a name="see-also"></a>另請參閱  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [定義及修改靜態資料列篩選](../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [sp_addarticle &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [複寫預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
