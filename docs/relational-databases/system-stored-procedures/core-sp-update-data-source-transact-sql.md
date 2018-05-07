---
title: core.sp_update_data_source (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_update_data_source
- sp_update_data_source_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_data_source
- management data warehouse, data collector stored procedures
- core.sp_update_data_source stored procedure
- data collector [SQL Server], stored procedures
ms.assetid: 66b95f96-6df7-4657-9b3c-86a58c788ca5
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3156ef5a6d4d1af2298222b660e6483eb109cddd
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="corespupdatedatasource-transact-sql"></a>core.sp_update_data_source (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在管理資料倉儲的 core.source_info_internal 資料表中，更新現有的資料列或插入新的資料列。 每次上傳封裝開始將資料上傳至管理資料倉儲時，資料收集器執行階段元件就會呼叫這個程序。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
core.sp_update_data_source [ @collection_set_uid = ] 'collection_set_uid'  
    ,[ @machine_name = ] 'machine_name'  
    , [ @named_instance = ] 'named_instance'  
    , [ @days_until_expiration = ] days_until_expiration  
    , [ @source_id = ] source_id OUTPUT  
```  
  
## <a name="arguments"></a>引數  
 [ @collection_set_uid = ] '*collection_set_uid*'  
 收集組的 GUID。 *collection_set_uid*是**uniqueidentifier**，沒有預設值。 若要取得 GUID，請查詢 msdb 資料庫中的 dbo.syscollector_collection_sets 檢視表。  
  
 [ @machine_name =] '*machine_name*'  
 收集組所在的伺服器名稱。 *machine_name*是**sysname** ，沒有預設值。  
  
 [ @named_instance =] '*named_instance*'  
 收集組的執行個體名稱。 *named_instance*是**sysname**，沒有預設值。  
  
> [!NOTE]  
>  *named_instance*必須是完整的執行個體名稱，其中包含電腦名稱與執行個體名稱，表單*computername*\\*instancename*。  
  
 [ @days_until_expiration = ] *days_until_expiration*  
 快照集資料保留期限中剩餘的天數。 *days_until_expiration*是**smallint**。  
  
 [ @source_id = ] *source_id*  
 更新來源的唯一識別碼。 *source_id*是**int**而且會當做 OUTPUT 傳回。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 每次上傳封裝開始將資料上傳至管理資料倉儲時，資料收集器執行階段元件就會呼叫 core.sp_update_data_source。 如果上次上傳之後已經發生了下列其中一項變更，就會更新 core.source_info_internal 資料表：  
  
-   已加入新的收集組。  
  
-   days_until_expiration 的值已變更。  
  
## <a name="permissions"></a>Permissions  
 需要的成員資格**mdw_writer** （具有 EXECUTE 權限） 固定的資料庫角色。  
  
## <a name="examples"></a>範例  
 下列範例會更新資料來源 (在此案例中為「磁碟使用量」收集組)、設定到期之前的天數，並傳回來源的識別碼。 此範例中會使用預設執行個體。  
  
```  
USE <management_data_warehouse>;  
GO  
DECLARE @source_id int;  
EXEC core.sp_update_data_source   
@collection_set_uid = '7B191952-8ECF-4E12-AEB2-EF646EF79FEF',   
@machine_name = '<computername>',  
@named_instance = 'MSSQLSERVER',  
@days_until_expiration = 10,  
@source_id = @source_id OUTPUT;  
```  
  
## <a name="see-also"></a>另請參閱  
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [資料收集器預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [管理資料倉儲](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  
