---
title: dbo.cdc_jobs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc_jobs
- cdc_jobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dbo.cdc_jobs
ms.assetid: 85e2d580-1c54-4b81-b7e6-2e12997199fd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0c9668c234728dc34952a7095889fe6ba5cfd06a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68084698"
---
# <a name="dbocdcjobs-transact-sql"></a>dbo.cdc_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  儲存擷取和清除作業的異動資料擷取組態參數。 這份資料表儲存在**msdb**。  
  
 
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|在其中執行作業之資料庫的識別碼。|  
|**job_type**|**nvarchar(20)**|作業的類型：「擷取」或「清除」。|  
|**job_id**|**uniqueidentifier**|與作業相關聯的唯一識別碼。|  
|**maxtrans**|**int**|每個掃描循環中要處理的交易數目上限。<br /><br /> **maxtrans**只適用於擷取作業。|  
|**maxscans**|**int**|要執行以便從記錄中擷取所有資料列的掃描循環數目上限。<br /><br /> **maxscans**只適用於擷取作業。|  
|**連續**|**bit**|旗標，指出擷取作業是連續執行 (1)，還是僅執行一次 (0)。 如需詳細資訊，請參閱 < [sys.sp_cdc_add_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)。<br /><br /> **連續**只適用於擷取作業。|  
|**pollinginterval**|**bigint**|記錄掃描循環之間的秒數。<br /><br /> **pollinginterval**只適用於擷取作業。|  
|**retention**|**bigint**|變更資料列要保留在變更資料表中的分鐘數。<br /><br /> **保留**只適用於清除作業。|  
|**threshold**|**bigint**|可以使用單一清除陳述式來刪除的最大刪除項目數。|  
  
## <a name="see-also"></a>另請參閱  
 [sys.sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)   
 [sys.sp_cdc_change_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md)   
 [sys.sp_cdc_help_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)   
 [sys.sp_cdc_drop_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-drop-job-transact-sql.md)  
  
  
