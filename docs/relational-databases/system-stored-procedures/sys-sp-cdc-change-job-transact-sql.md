---
description: sys.sp_cdc_change_job (Transact-SQL)
title: sys. sp_cdc_change_job (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_change_job_TSQL
- sys.sp_cdc_change_job
- sp_cdc_change_job_TSQL
- sp_cdc_change_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_change_job
ms.assetid: ea918888-0fc5-4cc1-b301-26b2a9fbb20d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bf81cfb8cbd06602252e62b3c72bafe694c14ed8
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545854"
---
# <a name="syssp_cdc_change_job-transact-sql"></a>sys.sp_cdc_change_job (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  修改目前資料庫中異動資料擷取清除或擷取作業的組態。 若要查看目前的作業設定，請查詢 [dbo. cdc_jobs](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md) 資料表，或使用 [sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sys.sp_cdc_change_job [ [ @job_type = ] 'job_type' ]  
    [ , [ @maxtrans = ] max_trans ]   
    [ , [ @maxscans = ] max_scans ]   
    [ , [ @continuous = ] continuous ]   
    [ , [ @pollinginterval = ] polling_interval ]   
    [ , [ @retention ] = retention ]   
    [ @threshold = ] 'delete threshold'  
```  
  
## <a name="arguments"></a>引數  
`[ @job_type = ] 'job_type'` 要修改的作業類型。 *job_type* 是 **Nvarchar (20) ** 預設值為 ' capture '。 有效的輸入是 'capture' 和 'cleanup'。  
  
`[ @maxtrans ] = max_trans_` 每個掃描迴圈中要處理的最大交易數目。 *max_trans* 是 **int** ，預設值是 Null，表示沒有此參數的變更。 如果已指定，該值必須是正整數。  
  
 *max_trans* 僅適用于 capture 工作。  
  
`[ @maxscans ] = max_scans_` 要從記錄檔中提取所有資料列時要執行的掃描迴圈數目上限。 *max_scans* 是 **int** ，預設值是 Null，表示沒有此參數的變更。  
  
 *max_scan* 僅適用于 capture 工作。  
  
`[ @continuous ] = continuous_` 指出 capture 作業是連續執行 (1) ，還是只執行一次 (0) 。 *連續* 是 **bit** ，預設值是 Null，表示沒有此參數的變更。  
  
 當 *連續* = 1 時， [sp_cdc_scan](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md) 作業會掃描記錄和處理最多 (*max_trans* \* *max_scans*) 交易。 然後，它會等候 *polling_interval* 中指定的秒數，然後再開始下次記錄檔掃描。  
  
 當 *連續* = 0 時， **sp_cdc_scan** 作業最多會執行 *max_scans* 掃描記錄檔，在每次掃描期間處理 *max_trans* 的交易，然後結束。  
  
 如果** \@ 連續**的變更從1變更為0， ** \@ pollinginterval**會自動設定為0。 為** \@ pollinginterval**指定的值會被忽略。  
  
 如果省略** \@ 連續**或明確設定為 Null，而且** \@ pollinginterval**明確設定為大於0的值，則** \@ 連續**會自動設定為1。  
  
 「*連續*」只對「捕獲」作業有效。  
  
`[ @pollinginterval ] = polling_interval_` 記錄檔掃描迴圈之間的秒數。 *polling_interval* 是 **Bigint** ，預設值是 Null，表示沒有此參數的變更。  
  
 當*連續*設定為1時， *polling_interval*僅適用于 capture 工作。  
  
`[ @retention ] = retention_` 變更資料列要保留在變更資料表中的分鐘數。 *保留* 是 **Bigint** ，預設值是 Null，表示沒有此參數的變更。 最大值為 52494800 (100 年)。 如果已指定，該值必須是正整數。  
  
 *保留* 僅適用于清除作業。  
  
`[ @threshold = ] 'delete threshold'` 可以使用單一清除語句來刪除的最大刪除專案數。 *delete 臨界* 值是 **Bigint** ，預設值是 Null，表示沒有此參數的變更。 *刪除閾值* 只對清除作業有效。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或 **1** (失敗)   
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="remarks"></a>備註  
 如果省略某個參數，就不會更新 [dbo. cdc_jobs](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md) 資料表中的關聯值。 明確設定為 NULL 的參數會被視為省略的參數。  
  
 指定對作業類型無效的參數將導致此陳述式失敗。  
  
 在使用 [sp_cdc_stop_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-stop-job-transact-sql.md) 停止作業之前，工作的變更不會生效，而是使用 [sp_cdc_start_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-start-job-transact-sql.md)重新開機。  
  
## <a name="permissions"></a>權限  
 需要 **db_owner** 固定資料庫角色中的成員資格。  
  
## <a name="examples"></a>範例  
  
### <a name="a-changing-a-capture-job"></a>A. 變更擷取作業  
 下列範例會更新 `@job_type` `@maxscans` `@maxtrans` 資料庫中 capture 工作的、和參數 `AdventureWorks2012` 。 擷取作業其他有效的參數 (`@continuous` 和 `@pollinginterval`) 被省略，而且其值不會進行修改。  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_change_job   
    @job_type = N'capture',  
    @maxscans = 1000,  
    @maxtrans = 15;  
GO  
```  
  
### <a name="b-changing-a-cleanup-job"></a>B. 變更清除作業  
 下列範例會在 `AdventureWorks2012` 資料庫中更新清除作業。 這種作業類型的所有有效參數（ ** \@ 臨界值**除外）都會指定。 ** \@ 閾值**的值未修改。  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_change_job   
    @job_type = N'cleanup',  
    @retention = 2880;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [dbo. cdc_jobs &#40;Transact-sql&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys. sp_cdc_enable_table &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [sys.sp_cdc_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
