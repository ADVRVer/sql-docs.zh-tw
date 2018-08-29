---
title: sp_spaceused & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 08/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_spaceused_TSQL
- sp_spaceused
dev_langs:
- TSQL
helpviewer_keywords:
- sp_spaceused
ms.assetid: c6253b48-29f5-4371-bfcd-3ef404060621
caps.latest.revision: 62
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6dc2878c9a913b5bb95ef32c9f00a6e7b1e94520
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43089381"
---
# <a name="spspaceused-transact-sql"></a>sp_spaceused (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  顯示資料列的數目、所保留的磁碟空間和資料表所用的磁碟空間、索引檢視，或目前資料庫中的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 佇列，或顯示整個資料庫所保留和使用的磁碟空間。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
sp_spaceused [[ @objname = ] 'objname' ]   
[, [ @updateusage = ] 'updateusage' ]  
[, [ @mode = ] 'mode' ]  
[, [ @oneresultset = ] oneresultset ]  
[, [ @include_total_xtp_storage = ] include_total_xtp_storage ]
```  
  
## <a name="arguments"></a>引數  

針對[!INCLUDE[sssdw-md](../../includes/sssdw-md.md)]並[!INCLUDE[sspdw-md](../../includes/sspdw-md.md)]，`sp_spaceused`必須指定具名的參數 (例如`sp_spaceused (@objname= N'Table1');`而不是依賴參數的序數位置。 

 [  **@objname=**] **'***objname***'** 
   
 這是要求的空間使用方式資訊所屬之資料表、索引檢視或佇列的完整或非完整名稱。 只有在指定完整物件名稱時，才會需要引號。 如果提供完整物件名稱 (包括資料庫名稱)，資料庫名稱就必須是目前資料庫的名稱。  
如果*objname*未指定，整個資料庫會傳回結果。  
*objname*已**nvarchar(776)**，預設值是 NULL。  
> [!NOTE]  
> [!INCLUDE[sssdw-md](../../includes/sssdw-md.md)] 和[!INCLUDE[sspdw-md](../../includes/sspdw-md.md)]僅支援資料庫和資料表的物件。
  
 [ **@updateusage=**] **'***updateusage***'**  
 指出應該執行 DBCC UPDATEUSAGE 來更新空間使用方式資訊。 當*objname*是未指定，整個資料庫上執行此陳述式; 此陳述式上的執行，否則為*objname*。 值可以是**真**或是**false**。 *updateusage*已**varchar(5)**，預設值是**false**。  
  
 [  **@mode=**] **'***模式***'**  
 表示結果的範圍。 延展的資料表或資料庫，如*模式*參數可讓您包含或排除物件中的遠端的一部分。 如需詳細資訊，請參閱 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)。  
  
 *模式*引數可以是下列值：  
  
|值|描述|  
|-----------|-----------------|  
|ALL|傳回儲存體的統計資料物件或資料庫包括本機部分和遠端的部分。|  
|LOCAL_ONLY|傳回儲存體的統計資料的本機部分的物件或資料庫。 如果物件或資料庫不是已啟用延展功能，會傳回相同的統計資料時一樣，因此@mode= ALL。|  
|REMOTE_ONLY|傳回遠端部份的物件或資料庫的儲存體統計資料。 當下列條件之一成立時，此選項就會引發錯誤：<br /><br /> 未啟用 Stretch 的資料表。<br /><br /> 資料表已啟用延展功能，但您永遠不會啟用資料移轉。 在此情況下，遠端資料表還沒有結構描述。<br /><br /> 使用者已手動卸除遠端資料表。<br /><br /> 遠端資料封存的佈建傳回的狀態為成功，但事實上它失敗。|  
  
 *模式*已**varchar(11)**，預設值是**N'ALL'**。  
  
 [  **@oneresultset=**] *oneresultset*  
 指出是否要傳回單一結果集。 *Oneresultset*引數可以是下列值：  
  
|值|描述|  
|-----------|-----------------|  
|0|當*@objname*為 null 或未指定，會傳回兩個結果集。 兩個結果集是預設行為。|  
|1|當*@objname* = null 或未指定，會傳回單一結果集。|  
  
 *oneresultset*已**位元**，預設值是**0**。  

[ **@include_total_xtp_storage**] **'***include_total_xtp_storage***'**  
**適用於：** [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)]， [!INCLUDE[sssds-md](../../includes/sssds-md.md)]。  
  
 當@oneresultset= 1，參數@include_total_xtp_storage決定單一結果集是否包含 MEMORY_OPTIMIZED_DATA 儲存體的資料行。 預設值為 0，也就是預設 （如果省略此參數） 的 XTP 資料行不包含在結果集。  

## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
 如果*objname*省略，而*oneresultset*是 0，則會傳回下列結果集提供目前的資料庫大小資訊。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|目前資料庫的名稱。|  
|**database_size**|**varchar(18)**|目前資料庫的大小 (以 MB 為單位)。 **database_size**包含資料和記錄檔。|  
|**未配置的空間**|**varchar(18)**|資料庫中尚未保留給資料庫物件的空間。|  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**保留**|**varchar(18)**|資料庫中的物件所配置的空間總量。|  
|**data**|**varchar(18)**|資料所用的空間總量。|  
|**index_size**|**varchar(18)**|索引所用的空間總量。|  
|**未使用**|**varchar(18)**|保留給資料庫中之物件但尚未使用的空間總量。|  
  
 如果*objname*省略，而*oneresultset*為 1，下列的單一結果集傳回以目前的資料庫大小資訊。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|目前資料庫的名稱。|  
|**database_size**|**varchar(18)**|目前資料庫的大小 (以 MB 為單位)。 **database_size**包含資料和記錄檔。|  
|**未配置的空間**|**varchar(18)**|資料庫中尚未保留給資料庫物件的空間。|  
|**保留**|**varchar(18)**|資料庫中的物件所配置的空間總量。|  
|**data**|**varchar(18)**|資料所用的空間總量。|  
|**index_size**|**varchar(18)**|索引所用的空間總量。|  
|**未使用**|**varchar(18)**|保留給資料庫中之物件但尚未使用的空間總量。|  
  
 如果*objname*指定，則指定的物件傳回下列結果集。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(128)**|要求的空間使用方式資訊所屬的物件名稱。<br /><br /> 不會傳回物件的結構描述名稱。 如果需要的結構描述名稱，使用[sys.dm_db_partition_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md)或是[sys.dm_db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)動態管理檢視來取得對等的大小資訊。|  
|**rows**|**char(20)**|資料表現有的資料列數。 如果指定的物件是一個 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 佇列，這個資料行會指出佇列中的訊息數目。|  
|**保留**|**varchar(18)**|保留空間的總量*objname*。|  
|**data**|**varchar(18)**|中的資料所使用的空間總量*objname*。|  
|**index_size**|**varchar(18)**|中的索引所使用的空間總量*objname*。|  
|**未使用**|**varchar(18)**|為保留的空間總量*objname*但尚未使用。|  
 
當未不指定任何參數時，這是預設的模式。 下列結果集傳回詳列出的磁碟上的資料庫大小資訊。 

|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|目前資料庫的名稱。|  
|**database_size**|**varchar(18)**|目前資料庫的大小 (以 MB 為單位)。 **database_size**包含資料和記錄檔。 如果資料庫具有 MEMORY_OPTIMIZED_DATA 檔案群組，這會包括檔案群組中的所有檢查點檔案的磁碟大小總計。|  
|**未配置的空間**|**varchar(18)**|資料庫中尚未保留給資料庫物件的空間。 如果資料庫具有 MEMORY_OPTIMIZED_DATA 檔案群組，這會包括檔案群組中的狀態預先建立的檢查點檔案的磁碟大小總計。|  

在資料庫中的資料表所使用的空間: （此結果集不會反映記憶體最佳化的資料表，因為不沒有磁碟使用量的任何資料表每個計量） 

|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**保留**|**varchar(18)**|資料庫中的物件所配置的空間總量。|  
|**data**|**varchar(18)**|資料所用的空間總量。|  
|**index_size**|**varchar(18)**|索引所用的空間總量。|  
|**未使用**|**varchar(18)**|保留給資料庫中之物件但尚未使用的空間總量。|

會傳回下列結果集**只有當**資料庫具有 MEMORY_OPTIMIZED_DATA 檔案群組與至少一個容器： 

|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**xtp_precreated**|**varchar(18)**|使用預先建立，以 kb 為單位的狀態的檢查點檔案的大小總計。 項目會計整個資料庫中的未配置空間。 [比方說，如果沒有 600,000 KB 的預先建立的檢查點檔案，此資料行包含 ' 600000 KB']|  
|**xtp_used**|**varchar(18)**|建構、 使用中及合併的目標，以 kb 為單位的狀態的檢查點檔案的大小總計。 這是目前正在使用中記憶體最佳化資料表的資料的磁碟空間。|  
|**xtp_pending_truncation**|**varchar(18)**|檢查點檔案狀態 WAITING_FOR_LOG_TRUNCATION，以 kb 為單位的大小總計。 這是正在等待清除，之後會截斷記錄檔, 的檢查點檔案使用的磁碟空間。|

如果*objname*已省略，oneresultset 的值為 1，並*include_total_xtp_storage*為 1，下列的單一結果集傳回以目前的資料庫大小資訊。 如果`include_total_xtp_storage`是 0 （預設值），則會省略的最後三個資料行。 

|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|目前資料庫的名稱。|  
|**database_size**|**varchar(18)**|目前資料庫的大小 (以 MB 為單位)。 **database_size**包含資料和記錄檔。 如果資料庫具有 MEMORY_OPTIMIZED_DATA 檔案群組，這會包括檔案群組中的所有檢查點檔案的磁碟大小總計。|
|**未配置的空間**|**varchar(18)**|資料庫中尚未保留給資料庫物件的空間。 如果資料庫具有 MEMORY_OPTIMIZED_DATA 檔案群組，這會包括檔案群組中的狀態預先建立的檢查點檔案的磁碟大小總計。|  
|**保留**|**varchar(18)**|資料庫中的物件所配置的空間總量。|  
|**data**|**varchar(18)**|資料所用的空間總量。|  
|**index_size**|**varchar(18)**|索引所用的空間總量。|  
|**未使用**|**varchar(18)**|保留給資料庫中之物件但尚未使用的空間總量。|
|**xtp_precreated**|**varchar(18)**|使用預先建立，以 kb 為單位的狀態的檢查點檔案的大小總計。 這整個會計入在資料庫中的未配置空間。 如果資料庫沒有 memory_optimized_data 檔案群組與至少一個容器，則傳回 NULL。 *此資料行只會包含的若@include_total_xtp_storage= 1*。| 
|**xtp_used**|**varchar(18)**|建構、 使用中及合併的目標，以 kb 為單位的狀態的檢查點檔案的大小總計。 這是目前正在使用中記憶體最佳化資料表的資料的磁碟空間。 如果資料庫沒有 memory_optimized_data 檔案群組與至少一個容器，則傳回 NULL。 *此資料行只會包含的若@include_total_xtp_storage= 1*。| 
|**xtp_pending_truncation**|**varchar(18)**|檢查點檔案狀態 WAITING_FOR_LOG_TRUNCATION，以 kb 為單位的大小總計。 這是正在等待清除，之後會截斷記錄檔, 的檢查點檔案使用的磁碟空間。 如果資料庫沒有 memory_optimized_data 檔案群組與至少一個容器，則傳回 NULL。 這個資料行是只包含的如果`@include_total_xtp_storage=1`。|

## <a name="remarks"></a>備註  
 **database_size**一律大於設定的總和**保留** + **未配置空間**因為它包含的記錄檔大小，但**保留**並**unallocated_space**只考量資料頁。  
  
 XML 索引和全文檢索索引所使用的頁面都會納入**index_size**兩個結果集。 當*objname*指定時，XML 索引和全文檢索索引之物件的頁面也會列入計算總**保留**並**index_size**結果。  
  
 如果資料庫或物件，例如具有空間索引的空間大小資料行中，計算空間使用量**database_size**，**保留**，並**index_size**，包括空間索引的大小。  
  
 當*updateusage*指定，則[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]掃描的資料在資料庫中的分頁，並可讓任何所需的更正**sys.allocation_units**和**sys.partitions**目錄檢視有關每個資料表使用的儲存空間。 例如，在某些狀況下，在卸除索引之後，資料表的空間資訊可能不是目前的資訊。 *updateusage*可能需要一些時間才能在大型資料表或資料庫上執行。 使用*updateusage*只當您懷疑所傳回的不正確的值，而當程序不會造成不良的影響其他使用者或處理資料庫中。 如果願意的話，您可以個別執行 DBCC UPDATEUSAGE。  
  
> [!NOTE]  
>  當您卸除或重建大型索引時，或卸除或截斷大型資料表時，[!INCLUDE[ssDE](../../includes/ssde-md.md)] 會延遲取消配置實際的頁面及其相關聯鎖定，直到認可交易之後。 延遲的卸除作業並不會立即釋出已配置的空間。 因此，所傳回的值**sp_spaceused**之後立即卸除或截斷大型物件可能無法反映實際的磁碟可用空間。  
  
## <a name="permissions"></a>Permissions  
 執行 **sp_spaceused** 的權限會授與 **public** 角色。 只有 **db_owner** 固定資料庫角色的成員，才能夠指定 **@updateusage** 參數。  
  
## <a name="examples"></a>範例  
  
### <a name="a-displaying-disk-space-information-about-a-table"></a>A. 顯示資料表的相關磁碟空間資訊  
 下列範例會報告 `Vendor` 資料表及其索引的磁碟空間資訊。  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_spaceused N'Purchasing.Vendor';  
GO  
```  
  
### <a name="b-displaying-updated-space-information-about-a-database"></a>B. 顯示資料庫的相關更新空間資訊  
 下列範例會摘要目前資料庫所用的空間，並利用選擇性參數 `@updateusage` 來確定會傳回目前的值。  
  
```sql  
USE AdventureWorks008R2;  
GO  
EXEC sp_spaceused @updateusage = N'TRUE';  
GO  
```  
  
### <a name="c-displaying-space-usage-information-about-the-remote-table-associated-with-a-stretch-enabled-table"></a>C. 顯示遠端資料表的空間使用狀況資訊相關聯的已啟用 Stretch 的資料表  
 下列範例會摘要說明使用已啟用 Stretch 的資料表與關聯之遠端資料表所用的空間**@mode**引數來指定遠端目標。 如需詳細資訊，請參閱 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)。  
  
```sql  
USE StretchedAdventureWorks2016  
GO  
EXEC sp_spaceused N'Purchasing.Vendor', @mode = 'REMOTE_ONLY'  
```  
  
### <a name="d-displaying-space-usage-information-for-a-database-in-a-single-result-set"></a>D. 顯示資料庫的空間使用量資訊中，將單一結果集  
 下列範例會摘要說明目前的資料庫，在單一結果集的空間使用量。  
  
```sql  
USE AdventureWorks2016  
GO  
EXEC sp_spaceused @oneresultset = 1  
```  

### <a name="e-displaying-space-usage-information-for-a-database-with-at-least-one-memoryoptimized-file-group-in-a-single-result-set"></a>E. 顯示單一結果集內的資料庫與至少一個記憶體最佳化檔案群組的空間使用方式資訊 
 下列範例會摘要說明單一結果集中至少一個記憶體最佳化檔案群組的目前資料庫的空間使用量。
 
```sql
USE WideWorldImporters
GO
EXEC sp_spaceused @updateusage = 'FALSE', @mode = 'ALL', @oneresultset = '1', @include_total_xtp_storage = '1';
GO
``` 

### <a name="f-displaying-space-usage-information-for-a-memoryoptimized-table-object-in-a-database"></a>F. 顯示資料庫中的 MEMORY_OPTIMIZED 資料表物件的空間使用量資訊。
 下列範例會摘要說明 MEMORY_OPTIMIZED 資料表物件目前的資料庫與至少一個記憶體最佳化檔案群組中的空間使用量。
 
```sql
USE WideWorldImporters
GO
EXEC sp_spaceused
@objname = N'VehicleTemparatures',
@updateusage = 'FALSE',
@mode = 'ALL',
@oneresultset = '0',
@include_total_xtp_storage = '1';
GO
```  

## <a name="see-also"></a>另請參閱  
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [DBCC UPDATEUSAGE &#40;Transact SQL&#41;](../../t-sql/database-console-commands/dbcc-updateusage-transact-sql.md)   
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)   
 [sys.allocation_units &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
