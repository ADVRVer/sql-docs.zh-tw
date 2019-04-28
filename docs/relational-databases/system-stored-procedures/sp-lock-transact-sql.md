---
title: sp_lock (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_lock_TSQL
- sp_lock
dev_langs:
- TSQL
helpviewer_keywords:
- sp_lock
ms.assetid: 9eaa0ec2-2ad9-457c-ae48-8da92a03dcb0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8d917f71d7cf7a36bb5d2c50b0cddd7893102a7e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62960082"
---
# <a name="splock-transact-sql"></a>sp_lock (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  報告鎖定的相關資訊。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 若要取得鎖定的相關資訊[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]，使用[sys.dm_tran_locks](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)動態管理檢視。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_lock [ [ @spid1 = ] 'session ID1' ] [ , [@spid2 = ] 'session ID2' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引數  
`[ @spid1 = ] 'session ID1'` 已[!INCLUDE[ssDE](../../includes/ssde-md.md)]工作階段識別碼，從**sys.dm_exec_sessions** ，使用者想要鎖定資訊。 *session ID1*已**int**預設值是 NULL。 執行**sp_who**來取得工作階段的程序資訊。 如果*session ID1*未指定，會顯示所有鎖定的相關資訊。  
  
`[ @spid2 = ] 'session ID2'` 這是另一個[!INCLUDE[ssDE](../../includes/ssde-md.md)]工作階段識別碼，從**sys.dm_exec_sessions**可能會與同時具有鎖定*session ID1*和使用者也需要其相關資訊。 *工作階段 ID2*已**int**預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功)  
  
## <a name="result-sets"></a>結果集  
 **Sp_lock**結果集包含一個資料列中指定的工作階段所持有的每個鎖定**@spid1**並**@spid2**參數。 如果沒有**@spid1**也**@spid2**未指定，結果集會報告鎖定的所有工作階段目前作用中的執行個體[!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**spid**|**smallint**|要求鎖定之處理序的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 工作階段識別碼。|  
|**dbid**|**smallint**|保留鎖定之資料庫的識別碼。 您可以利用 DB_NAME() 函數來識別資料庫。|  
|**ObjId**|**int**|保留鎖定之物件的識別碼。 您可以在相關資料庫中，利用 OBJECT_NAME() 函數來識別物件。 99 這個值是一個特殊情況，表示用來記錄資料庫頁面配置之某系統頁面的鎖定。|  
|**IndId**|**smallint**|保留鎖定之索引的識別碼。|  
|**型別**|**nchar(4)**|鎖定類型：<br /><br /> RID = 鎖定資料表中資料列識別碼 (RID) 所識別的單一資料列。<br /><br /> KEY = 在索引內鎖定，用來保護可序列化交易中的某個索引鍵範圍。<br /><br /> PAG = 鎖定資料或索引頁面。<br /><br /> EXT = 鎖定範圍。<br /><br /> TAB = 鎖定整份資料表，其中包括所有資料和索引。<br /><br /> DB = 鎖定資料庫。<br /><br /> FIL = 鎖定資料庫檔案。<br /><br /> APP = 鎖定應用程式指定資源。<br /><br /> MD = 鎖定中繼資料或目錄資訊。<br /><br /> HBT = 鎖定堆積或 B 型樹狀目錄索引。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的這項資訊並不完整。<br /><br /> AU = 鎖定配置單位。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的這項資訊並不完整。|  
|**資源**|**nchar(32)**|用來識別鎖定資源的值。 值的格式取決於中所識別之資源的類型**型別**資料行：<br /><br /> **型別**值：**資源**值<br /><br /> RID:識別項格式 pagenumber: rid，其中 fileid 識別包含頁面上，檔案 pagenumber 識別包含資料列、 頁面和 rid 頁面上的特定資料列。 fileid 符合**file_id**中的資料行**sys.database_files**目錄檢視。<br /><br /> 索引鍵：在內部使用的十六進位數字[!INCLUDE[ssDE](../../includes/ssde-md.md)]。<br /><br /> PAG:數字格式 pagenumber，fileid 識別包含頁面上，檔案，pagenumber 識別頁面。<br /><br /> EXT:數字，識別範圍中的第一頁。 這個號碼的格式為 fileid:pagenumber。<br /><br /> 索引標籤：沒有資訊，因為資料表已經識別**ObjId**資料行。<br /><br /> DB:沒有資訊，因為在已識別的資料庫**dbid**資料行。<br /><br /> FIL:檔案中，用來比對的識別碼**file_id**中的資料行**sys.database_files**目錄檢視。<br /><br /> 應用程式：鎖定此應用程式資源的唯一識別碼。 格式 DbPrincipleId:\<前兩個至 16 個字元的資源字串 >\<雜湊值 >。<br /><br /> MD：隨資源類型而不同。 如需詳細資訊，請參閱說明**resource_description**中的資料行[sys.dm_tran_locks &#40;-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)。<br /><br /> HBT:未提供任何資訊。 使用**sys.dm_tran_locks**動態管理檢視。<br /><br /> AU:未提供任何資訊。 使用**sys.dm_tran_locks**動態管理檢視。|  
|**模式**|**nvarchar(8)**|要求的鎖定模式。 可為以下項目：<br /><br /> NULL = 未授與資源的任何存取權。 這用來作為預留位置。<br /><br /> Sch-S = 結構描述穩定性。 確定在任何工作階段持有結構描述元素的結構描述穩定性鎖定時，不卸除結構描述元素，如資料表或索引。<br /><br /> Sch-M = 結構描述修改。 想要變更指定資源結構描述的任何工作階段都必須持有這個項目。 請確定沒有其他工作階段在參考指示的物件。<br /><br /> S = 共用。 持有它的工作階段，會取得資源的共用存取權。<br /><br /> U = 更新。 表示取得最終可能會更新之資源的更新鎖定。 它用來防止當多個工作階段為了後來可能更新資源而鎖定資源時，所常見的死結形式。<br /><br /> X = 獨佔。 持有它的工作階段，會取得資源的獨佔存取權。<br /><br /> IS = 意圖共用。 表示在鎖定階層中的某些從屬資源上設定 S 鎖定的意圖。<br /><br /> IU = 意圖更新。 表示在鎖定階層中的某些從屬資源上設定 U 鎖定的意圖。<br /><br /> IX = 意圖獨佔。 表示在鎖定階層中的某些從屬資源上設定 X 鎖定的意圖。<br /><br /> SIU = 共用意圖更新。 表示意圖取得鎖定階層中從屬資源的更新鎖定之共用資源存取權。<br /><br /> SIX = 共用意圖獨佔。 表示意圖取得鎖定階層中從屬資源的獨佔鎖定之共用資源存取權。<br /><br /> UIX = 更新意圖獨佔。 表示意圖取得鎖定階層中從屬資源的獨佔鎖定之資源更新鎖定。<br /><br /> BU = 大量更新。 供大量作業使用。<br /><br /> RangeS_S = 共用索引鍵範圍和共用資源鎖定。 指出可序列化的範圍掃描。<br /><br /> RangeS_U = 共用索引鍵範圍和更新資源鎖定。 指出可序列化的更新掃描。<br /><br /> RangeI_N = 插入索引鍵範圍和 Null 資源鎖定。 在將新索引鍵插入索引之前，用來測試範圍。<br /><br /> RangeI_S = 索引鍵範圍轉換鎖定。 這是重疊 RangeI_N 和 S 鎖定所建立。<br /><br /> RangeI_U = 重疊 RangeI_N 和 U 鎖定而建立的索引鍵範圍轉換鎖定。<br /><br /> RangeI_X = 重疊 RangeI_N 和 X 鎖定而建立的索引鍵範圍轉換鎖定。<br /><br /> RangeX_S = 重疊 RangeI_N 和 RangeS_S 鎖定建立的索引鍵範圍轉換鎖定。 。<br /><br /> RangeX_U = 重疊 RangeI_N 和 RangeS_U 鎖定而建立的索引鍵範圍轉換鎖定。<br /><br /> RangeX_X = 獨佔索引鍵範圍和獨佔資源鎖定。 這是更新範圍中的索引鍵時所用的轉換鎖定。|  
|**狀態**|**nvarchar(5)**|鎖定要求狀態：<br /><br /> CNVRT:從另一個模式，正在轉換鎖定，但持有模式衝突的鎖定的另一個處理序封鎖轉換。<br /><br /> 授與：已取得鎖定。<br /><br /> 等候：鎖定會封鎖其他處理序持有模式衝突的鎖定。|  
  
## <a name="remarks"></a>備註  
 使用者可以利用下列方式來控制讀取作業的鎖定：  
  
-   利用 SET TRANSACTION ISOLATION LEVEL 來指定工作階段的鎖定層級。 如需語法和限制，請參閱[SET TRANSACTION ISOLATION LEVEL &#40;TRANSACT-SQL&#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)。  
  
-   利用鎖定資料表提示，在 FROM 子句中指定資料表之個別參考的鎖定層級。 如需語法和限制，請參閱[資料表提示&#40;TRANSACT-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md)。  
  
 所有未關聯於工作階段的分散式交易都是被遺棄的交易。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會指派 -2 的 SPID 值給所有被遺棄的分散式交易，讓使用者更容易識別封鎖的分散式交易。 如需詳細資訊，請參閱 [使用標示的異動以一致的方式復原相關資料庫 &#40;完整復原模式&#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)。  
  
## <a name="permissions"></a>Permissions  
 需要 VIEW SERVER STATE 權限。  
  
## <a name="examples"></a>範例  
  
### <a name="a-listing-all-locks"></a>A. 列出所有鎖定  
 下列範例會顯示 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體目前保留之所有鎖定的相關資訊。  
  
```  
USE master;  
GO  
EXEC sp_lock;  
GO  
```  
  
### <a name="b-listing-a-lock-from-a-single-server-process"></a>B. 列出單一伺服器處理序的鎖定  
 下列範例會顯示處理序識別碼 `53` 的相關資訊，其中包括鎖定。  
  
```  
USE master;  
GO  
EXEC sp_lock 53;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)   
 [DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)   
 [KILL &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-transact-sql.md)   
 [OBJECT_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/object-name-transact-sql.md)   
 [sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.dm_os_tasks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)   
 [sys.dm_os_threads &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql.md)  
  
  
