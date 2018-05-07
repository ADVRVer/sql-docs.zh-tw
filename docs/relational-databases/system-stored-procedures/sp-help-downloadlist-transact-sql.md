---
title: sp_help_downloadlist (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_downloadlist_TSQL
- sp_help_downloadlist
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_downloadlist
ms.assetid: 745b265b-86e8-4399-b928-c6969ca1a2c8
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e48423bc91413518abe3002a3c3d8da2cef330c2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="sphelpdownloadlist-transact-sql"></a>sp_help_downloadlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  列出所有資料列**sysdownloadlist**系統提供的工作，或如果未指定作業的所有資料列的資料表。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_help_downloadlist { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }   
     [ , [ @operation = ] 'operation' ]   
     [ , [ @object_type = ] 'object_type' ]   
     [ , [ @object_name = ] 'object_name' ]   
     [ , [ @target_server = ] 'target_server' ]   
     [ , [ @has_error = ] has_error ]   
     [ , [ @status = ] status ]   
     [ , [ @date_posted = ] date_posted ]  
```  
  
## <a name="arguments"></a>引數  
 [ **@job_id=** ] *job_id*  
 要傳回資訊的作業識別碼。 *job_id*是**uniqueidentifier**，預設值是 NULL。  
  
 [ **@job_name=** ] **'***job_name***'**  
 作業的名稱。 *job_name*是**sysname**，預設值是 NULL。  
  
> [!NOTE]  
>  任一*job_id*或*job_name*必須指定，但不可同時指定兩者。  
  
 [  **@operation=** ] **'***作業***'**  
 指定作業的有效動作。 *作業*是**varchar(64)**，預設值是 NULL，而且可以是下列值之一。  
  
|Value|Description|  
|-----------|-----------------|  
|**DEFECT**|要求從主要目標伺服器脫離的伺服器作業**SQLServerAgent**服務。|  
|**DELETE**|移除整項作業的作業動作。|  
|**INSERT**|插入整項作業或重新整理現有作業的作業動作。 適當的話，這個動作包括所有作業步驟和排程。|  
|**重新登錄**|使目標伺服器將編列資訊 (包括輪詢間隔和時區) 重新傳送到多伺服器網域的伺服器作業。 目標伺服器也會重新下載**MSXOperator**詳細資料。|  
|**SET-POLL**|設定目標伺服器輪詢多伺服器網域的間隔 (以秒為單位) 之伺服器作業。 如果指定，*值*解譯為必要的間隔值，而且可以是值**10**至**28800**。|  
|**啟動**|要求開始執行作業的作業動作。|  
|**停止**|要求停止執行作業的作業動作。|  
|**同步處理時間**|使目標伺服器將它的系統時鐘和多伺服器網域同步化的伺服器作業。 由於這項作業成本很高，因此，請盡量不要太常執行這項作業。|  
|**UPDATE**|只更新作業**sysjobs**作業，而非從作業步驟或排程的資訊。 會自動呼叫**sp_update_job**。|  
  
 [ **@object_type=** ] **'***object_type***'**  
 指定作業的物件類型。 *object_type*是**varchar(64)**，預設值是 NULL。 *object_type*可以是 JOB 或 SERVER。 如需有關有效*object_type*值，請參閱[sp_add_category &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md)。  
  
 [ **@object_name=** ] **'***object_name***'**  
 物件的名稱。 *object_name*是**sysname**，預設值是 NULL。 如果*object_type*是工作， *object_name*是工作名稱。 如果*object_type*是伺服器， *object_name*是伺服器的名稱。  
  
 [ **@target_server=** ] **'***target_server***'**  
 目標伺服器的名稱。 *target_server*是**nvarchar （128)**，預設值是 NULL。  
  
 [ **@has_error=** ] *has_error*  
 這是指作業是否應該認可錯誤。 *has_error*是**tinyint**，預設值是 NULL，表示應該認可任何錯誤。 **1**指出不應該認可所有錯誤。  
  
 [  **@status=** ]*狀態*  
 作業的狀態。 *狀態*是**tinyint**，預設值是 NULL。  
  
 [ **@date_posted=** ] *date_posted*  
 在指定的日期和時間或之後建立所有項目的日期和時間，都應該包括在結果集中。 *date_posted*是**datetime**，預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|指示的唯一整數識別碼。|  
|**source_server**|**nvarchar(30)**|指示的來源伺服器電腦名稱。 在[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 版中，這一律是主要伺服器 (MSX) 的電腦名稱。|  
|**operation_code**|**nvarchar(4000)**|指示的作業碼。|  
|**object_name**|**sysname**|指示所影響的物件。|  
|**object_id**|**uniqueidentifier**|指示所影響之物件的識別碼 (**job_id**的工作物件，或是 0x00 代表伺服器物件) 或特定資料值**operation_code**。|  
|**target_server**|**nvarchar(30)**|將下載這個指示的目標伺服器。|  
|**error_message**|**nvarchar(1024)**|當目標伺服器在處理這個指示發生問題時，所發出的錯誤訊息 (如果有的話)。<br /><br /> 附註： 任何錯誤訊息都會封鎖所有進一步的下載目標伺服器。|  
|**date_posted**|**datetime**|將指示公佈到資料表中的日期。|  
|**date_downloaded**|**datetime**|目標伺服器下載指示的日期。|  
|**status**|**tinyint**|作業的狀態：<br /><br /> **0** = 尚未下載<br /><br /> **1** = 下載成功。|  
  
## <a name="permissions"></a>Permissions  
 這個程序的執行權限預設會授與 **系統管理員 (sysadmin)** 固定伺服器角色的成員。  
  
## <a name="examples"></a>範例  
 下列範例會列出 `sysdownloadlist` 作業之 `NightlyBackups` 中的資料列。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_downloadlist  
    @job_name = N'NightlyBackups',  
    @operation = N'UPDATE',   
    @object_type = N'JOB',   
    @object_name = N'NightlyBackups',  
    @target_server = N'SEATTLE2',   
    @has_error = 1,   
    @status = NULL,   
    @date_posted = NULL ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
