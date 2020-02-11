---
title: sp_syscollector_create_collection_set （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_create_collection_set_TSQL
- sp_syscollector_create_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_create_collection_set
ms.assetid: 69e9ff0f-c409-43fc-89f6-40c3974e972c
author: stevestein
ms.author: sstein
ms.openlocfilehash: e859ed97afdc3dfbb4e39a93b8691d044ceca37d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68032645"
---
# <a name="sp_syscollector_create_collection_set-transact-sql"></a>sp_syscollector_create_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  建立新的收集組。 您可以使用這個預存程序來建立用於資料收集的自訂收集組。  
  
> [!WARNING]  
>  如果設定為 Proxy 的 Windows 帳戶為非互動使用者或是尚未登入的互動使用者，則設定檔目錄不會存在，而且暫存目錄的建立將會失敗。 因此，如果您在網域控制站上使用 Proxy 帳戶，則必須指定已至少使用一次的互動帳戶，以確保設定檔目錄已經建立。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_syscollector_create_collection_set   
      [ @name = ] 'name'  
    , [ [ @target = ] 'target' ]  
    , [ [ @collection_mode = ] collection_mode ]  
    , [ [ @days_until_expiration = ] days_until_expiration ]  
    , [ [ @proxy_id = ] proxy_id ]  
    , [ [ @proxy_name = ] 'proxy_name' ]  
    , [ [ @schedule_uid = ] 'schedule_uid' ]  
    , [ [ @schedule_name = ] 'schedule_name' ]  
    , [ [ @logging_level = ] logging_level ]  
    , [ [ @description = ] 'description' ]  
    , [ @collection_set_id = ] collection_set_id OUTPUT   
    , [ [ @collection_set_uid = ] 'collection_set_uid' OUTPUT ]  
```  
  
## <a name="arguments"></a>引數  
`[ @name = ] 'name'`這是收集組的名稱。 *名稱*是**sysname** ，不能是空字串或 Null。  
  
 *名稱*必須是唯一的。 如需目前的收集組名稱清單，請查詢 syscollector_collection_sets 系統檢視表。  
  
`[ @target = ] 'target'`保留供日後使用。 *名稱*為**Nvarchar （128）** ，預設值為 Null。  
  
`[ @collection_mode = ] collection_mode`指定收集和儲存資料的方式。 *collection_mode*是**Smallint** ，而且可以有下列其中一個值：  
  
 0 - 快取模式。 資料收集和上傳會依照不同的排程。 指定連續收集的快取模式。  
  
 1 - 非快取模式。 資料收集和上傳位於相同的排程上。 針對特定收集或快照集收集指定非快取模式。  
  
 *Collection_mode*的預設值為0。 當*collection_mode*為0時，必須指定*schedule_uid*或*schedule_name* 。  
  
`[ @days_until_expiration = ] days_until_expiration`這是收集的資料儲存在管理資料倉儲中的天數。 *days_until_expiration*是**Smallint** ，預設值為730（兩年）。 *days_until_expiration*必須是0或正整數。  
  
`[ @proxy_id = ] proxy_id`這是[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent proxy 帳戶的唯一識別碼。 *proxy_id*是**int** ，預設值為 Null。 如果指定， *proxy_name*必須是 Null。 若要取得*proxy_id*，請查詢 sysproxies 系統資料表。 dc_admin 固定資料庫角色必須具有存取此 Proxy 的權限。 如需詳細資訊，請參閱[建立 SQL Server Agent Proxy](../../ssms/agent/create-a-sql-server-agent-proxy.md)。  
  
`[ @proxy_name = ] 'proxy_name'`這是 proxy 帳戶的名稱。 *proxy_name*是**sysname** ，預設值是 Null。 如果指定， *proxy_id*必須是 Null。 若要取得*proxy_name*，請查詢 sysproxies 系統資料表。  
  
`[ @schedule_uid = ] 'schedule_uid'`這是指向排程的 GUID。 *schedule_uid*是**uniqueidentifier** ，預設值為 Null。 如果指定， *schedule_name*必須是 Null。 若要取得*schedule_uid*，請查詢 sysschedules 系統資料表。  
  
 當*collection_mode*設定為0時，必須指定*schedule_uid*或*schedule_name* 。 當*collection_mode*設為1時， *schedule_uid*或*schedule_name*會在指定時予以忽略。  
  
`[ @schedule_name = ] 'schedule_name'`這是排程的名稱。 *schedule_name*是**sysname** ，預設值是 Null。 如果指定， *schedule_uid*必須是 Null。 若要取得*schedule_name*，請查詢 sysschedules 系統資料表。  
  
`[ @logging_level = ] logging_level`這是記錄層級。 *logging_level*是**Smallint**並具有下列其中一個值：  
  
 0 – 記錄執行資訊和追蹤的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 事件：  
  
-   開始/停止收集組  
  
-   開始/停止封裝  
  
-   錯誤資訊  
  
 1 - 層級 0 記錄和：  
  
-   執行統計資料  
  
-   持續執行的收集進度  
  
-   
  [!INCLUDE[ssIS](../../includes/ssis-md.md)] 的警告事件  
  
 2 - 層級 1 記錄和 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 的詳細事件資訊  
  
 *Logging_level*的預設值為1。  
  
`[ @description = ] 'description'`這是收集組的描述。 *描述*是**Nvarchar （4000）** ，預設值為 Null。  
  
`[ @collection_set_id = ] collection_set_id`這是收集組的唯一本機識別碼。 *collection_set_id*是具有 OUTPUT 的**int** ，而且是必要的。  
  
`[ @collection_set_uid = ] 'collection_set_uid'`這是收集組的 GUID。 *collection_set_uid*是具有輸出的**uniqueidentifier** ，其預設值為 Null。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功）或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 sp_syscollector_create_collection_set 必須在 msdb 系統資料庫的內容中執行。  
  
## <a name="permissions"></a>權限  
 需要 dc_admin (具有 EXECUTE 權限) 固定資料庫角色中的成員資格，才能執行此程序。  
  
## <a name="examples"></a>範例  
  
### <a name="a-creating-a-collection-set-by-using-default-values"></a>A. 使用預設值建立收集組  
 下列範例藉由只指定必要參數來建立收集組。 
  `@collection_mode` 不是必要項，但是預設收集模式 (快取) 需要指定排程識別碼或排程名稱。  
  
```  
USE msdb;  
GO  
DECLARE @collection_set_id int;  
EXECUTE dbo.sp_syscollector_create_collection_set  
    @name = N'Simple collection set test 1',  
    @description = N'This is a test collection set that runs in non-cached mode.',  
    @collection_mode = 1,  
    @collection_set_id = @collection_set_id OUTPUT;  
GO  
```  
  
### <a name="b-creating-a-collection-set-by-using-specified-values"></a>B. 使用指定的值建立收集組  
 下列範例藉由指定許多參數的值來建立收集組。  
  
```  
USE msdb;  
GO  
DECLARE @collection_set_id int;  
DECLARE @collection_set_uid uniqueidentifier;  
SET @collection_set_uid = NEWID();  
EXEC dbo.sp_syscollector_create_collection_set  
    @name = N'Simple collection set test 2',  
    @collection_mode = 0,  
    @days_until_expiration = 365,  
    @description = N'This is a test collection set that runs in cached mode.',  
    @logging_level = 2,  
    @schedule_name = N'CollectorSchedule_Every_30min',  
    @collection_set_id = @collection_set_id OUTPUT,  
    @collection_set_uid = @collection_set_uid OUTPUT;  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料收集](../../relational-databases/data-collection/data-collection.md)   
 [建立使用一般 T-SQL 查詢收集器型別的自訂收集組 &#40;Transact-SQL&#41;](../../relational-databases/data-collection/create-custom-collection-set-generic-t-sql-query-collector-type.md)   
 [資料收集器預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [syscollector_collection_sets &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)  
  
  
