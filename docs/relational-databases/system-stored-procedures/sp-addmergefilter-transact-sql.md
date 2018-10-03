---
title: sp_addmergefilter & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_addmergefilter
- sp_addmergefilter_TSQL
helpviewer_keywords:
- sp_addmergefilter
ms.assetid: 4c118cb1-2008-44e2-a797-34b7dc34d6b1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 72d29fca659426075f4c7ee07f82ac6507fc0709
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47595207"
---
# <a name="spaddmergefilter-transact-sql"></a>sp_addmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  加入合併篩選，依據與其他資料表的聯結，建立資料分割。 這個預存程序執行於發行集資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_addmergefilter [ @publication = ] 'publication'   
        , [ @article = ] 'article'   
        , [ @filtername = ] 'filtername'   
        , [ @join_articlename = ] 'join_articlename'   
        , [ @join_filterclause = ] join_filterclause  
    [ , [ @join_unique_key = ] join_unique_key ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @filter_type = ] filter_type ]  
```  
  
## <a name="arguments"></a>引數  
 [  **@publication=** ] **'***發行集***'**  
 這是加入合併篩選時所在發行集的名稱。 *發行集*已**sysname**，沒有預設值。  
  
 [  **@article=** ] **'***文章***'**  
 這是加入合併篩選所在的發行項的名稱。 *發行項*已**sysname**，沒有預設值。  
  
 [  **@filtername=** ] **'***filtername***'**  
 這是篩選的名稱。 *filtername*是必要的參數。 *filtername*已**sysname**，沒有預設值。  
  
 [  **@join_articlename=** ] **'***join_articlename***'**  
 所指定的子發行項的父發行*一文*，必須使用所指定的聯結子句中加入*join_filterclause*，以判斷子發行項中符合的資料列合併篩選之篩選準則。 *join_articlename*已**sysname**，沒有預設值。 發行項必須是所指定的發行集中*發行集*。  
  
 [  **@join_filterclause=** ] *join_filterclause*  
 是一個聯結子句，必須用來將所指定的子發行項*一文*與所指定的父發行項*join_article*，以判斷符合合併篩選的資料列。 *join_filterclause*已**nvarchar(1000)**。  
  
 [  **@join_unique_key=** ] *join_unique_key*  
 如果指定子發行項之間的聯結*一文*與父發行項*join_article*是一個為一對多、 一對一、 多對一或多對多。 *join_unique_key*已**int**，預設值是 0。 **0**表示多對一或多對多聯結。 **1**表示一對一或一對多的聯結。 這個值是**1**聯結的資料行形成唯一的索引鍵中的當*join_article*，或如果*join_filterclause*之間的外部索引鍵*文章*和中的主索引鍵*join_article*。  
  
> [!CAUTION]  
>  只將此參數設定為**1**如果您有保證唯一性的父發行項之基礎資料表中的聯結資料行的條件約束。 如果*join_unique_key*設為**1**不正確時，可能會發生非聚合的資料。  
  
 [  **@force_invalidate_snapshot=** ] *force_invalidate_snapshot*  
 認可這個預存程序所採取的動作可能使現有的快照集失效。 *force_invalidate_snapshot*已**位元**，預設值**0**。  
  
 **0**指定合併發行項的變更不會使快照集失效。 如果預存程序偵測到變更需要新的快照集，就會發生錯誤，且不會進行任何變更。  
  
 **1**指定合併發行項的變更可能使快照集失效，如果有現有的訂閱需要新的快照集，則在標示為已棄用之現有快照集和新的快照集提供權限產生。  
  
 [  **@force_reinit_subscription=** ] *force_reinit_subscription*  
 認可這個預存程序所採取的動作可能需要重新初始化現有的訂閱。 *force_reinit_subscription*已**元**，預設值是 0。  
  
 **0**指定合併發行項的變更不會使訂閱重新初始化。 如果預存程序偵測到變更需要重新初始化訂閱，就會發生錯誤，且不會進行任何變更。  
  
 **1**指定合併發行項的變更會使現有的訂閱重新初始化，並提供發生之訂閱重新初始化的權限。  
  
 [  **@filter_type=** ] *filter_type*  
 指定要加入的篩選類型。 *filter_type*已**tinyint**，而且可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**1**|僅聯結篩選。 支援 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 訂閱者需要這個值。|  
|**2**|僅邏輯記錄關聯性。|  
|**3**|聯結篩選和邏輯記錄關聯性。|  
  
 如需詳細資訊，請參閱[使用邏輯記錄分組相關資料列的變更](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_addmergefilter**用於合併式複寫中。  
  
 **sp_addmergefilter**只能搭配資料表發行項。 不支援檢視和索引檢視發行項。  
  
 這個程序也可以在兩個發行項之間加入邏輯關聯性，不論這些發行項之間是否有聯結篩選。 *filter_type*用來指定要加入合併篩選是聯結篩選、 邏輯的關聯性，或兩者。  
  
 若要使用邏輯記錄，發行集和發行項必須符合許多需求。 如需詳細資訊，請參閱[使用邏輯記錄分組相關資料列的變更](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)。  
  
 通常，這個選項用於一個有已發行主索引鍵資料表之外部索引鍵參考的發行項，且主索引鍵資料表在它的發行項中定義了篩選。 主索引鍵資料列的子集可用來決定抄寫至訂閱者的外部索引鍵資料列。  
  
 當兩個發行項的來源資料表共用相同的資料表物件名稱時，您無法在這兩個已發行的發行項之間加入聯結篩選。 在這種情況下，即使兩個資料表為不同結構描述所擁有，且具有唯一的發行項名稱，聯結篩選的建立作業仍會失敗。  
  
 當參數化資料列篩選器和聯結篩選都用於資料表發行項上時，複寫會判斷資料列是否屬於訂閱者的資料分割。 它是藉由評估篩選函數或聯結篩選 (使用[OR](../../t-sql/language-elements/or-transact-sql.md)運算子)，而不是評估的兩個條件的交集 (使用[AND](../../t-sql/language-elements/and-transact-sql.md)運算子)。  
  
## <a name="example"></a>範例  
 [!code-sql[HowTo#sp_addmergefilter](../../relational-databases/replication/codesnippet/tsql/sp-addmergefilter-transa_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色或**db_owner**固定的資料庫角色可以執行**sp_addmergefilter**。  
  
## <a name="see-also"></a>另請參閱  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [定義和修改合併發行項之間的聯結篩選](../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Join Filters](../../relational-databases/replication/merge/join-filters.md)   
 [sp_changemergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_dropmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [複寫預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
