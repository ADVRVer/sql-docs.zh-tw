---
title: sys.sp_cdc_scan (TRANSACT-SQL) |Microsoft Docs
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
- sys.sp_cdc_scan_TSQL
- sp_cdc_scan
- sys.sp_cdc_scan
- sp_cdc_scan_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_scan
ms.assetid: 46e4294c-97b8-47d6-9ed9-b436a9929353
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f321deee03c7231287a02d03472e637731e62926
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43038391"
---
# <a name="sysspcdcscan-transact-sql"></a>sys.sp_cdc_scan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  執行異動資料擷取記錄掃描作業。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sys.sp_cdc_scan [ [ @maxtrans = ] max_trans ]   
     [ , [ @maxscans = ] max_scans ]   
     [ , [ @continuous = ] continuous ]   
     [ , [ @pollinginterval = ] polling_interval ]   
```  
  
## <a name="arguments"></a>引數  
 [  **@maxtrans=** ] *max_trans&lt*  
 每個掃描循環中要處理的交易數目上限。 *max_trans&lt*已**int**預設值是 500。  
  
 [  **@maxscans=** ] *max_scans*  
 要執行以便從記錄中擷取所有資料列的掃描循環數目上限。 *max_scans*已**int**預設值是 10。  
  
 [  **@continuous=** ]*連續*  
 指出預存程序應該結束之後執行單一掃描循環 (0)，還是連續執行時，所指定的時間暫停*polling_interval*之前重新掃描循環 (1)。 *持續*已**tinyint**預設值是 0。  
  
 [  **@pollinginterval=** ] *polling_interval*  
 記錄掃描循環之間的秒數。 *polling_interval*已**bigint**預設值是 0。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="remarks"></a>備註  
 如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 擷取作業正由異動資料擷取使用中，sys.sp_MScdc_capture_job 就會在內部呼叫 sys.sp_cdc_scan。 當異動資料擷取記錄掃描作業已經在使用中，或者資料庫已啟用異動複寫時，就無法明確執行此程序。 想要自訂自動設定擷取作業之行為的管理員應該使用這個預存程序。  
  
## <a name="permissions"></a>Permissions  
 需要 db_owner 固定資料庫角色中的成員資格。  
  
## <a name="see-also"></a>另請參閱  
 [dbo.cdc_jobs &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
  
  
