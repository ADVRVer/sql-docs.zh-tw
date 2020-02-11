---
title: sp_spaceused （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 08/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_spaceused_TSQL
- sp_spaceused
dev_langs:
- TSQL
helpviewer_keywords:
- sp_spaceused
ms.assetid: c6253b48-29f5-4371-bfcd-3ef404060621
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6b0bd2f253dede1c427eda826eba0e998a144736
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "72252018"
---
# <a name="sp_spaceused-transact-sql"></a>sp_spaceused (Transact-SQL)
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

對於[!INCLUDE[sssdw-md](../../includes/sssdw-md.md)]和[!INCLUDE[sspdw-md](../../includes/sspdw-md.md)]， `sp_spaceused`必須指定具名引數（例如， `sp_spaceused (@objname= N'Table1');`而不是依賴參數的序數位置）。 

`[ @objname = ] 'objname'`
   
 這是要求的空間使用方式資訊所屬之資料表、索引檢視或佇列的完整或非完整名稱。 只有在指定完整物件名稱時，才會需要引號。 如果提供完整物件名稱 (包括資料庫名稱)，資料庫名稱就必須是目前資料庫的名稱。  
如果未指定*objname* ，則會傳回整個資料庫的結果。  
*objname*是**Nvarchar （776）**，預設值是 Null。  
> [!NOTE]  
> [!INCLUDE[sssdw-md](../../includes/sssdw-md.md)]和[!INCLUDE[sspdw-md](../../includes/sspdw-md.md)]只支援資料庫和資料表物件。
  
`[ @updateusage = ] 'updateusage'`表示應執行 DBCC UPDATEUSAGE 以更新空間使用方式資訊。 未指定*objname*時，會在整個資料庫上執行語句;否則，語句會在*objname*上執行。 值可以是**true**或**false**。 *updateusage*是**Varchar （5）**，預設值是**false**。  
  
`[ @mode = ] 'mode'`指出結果的範圍。 針對延展的資料表或資料庫， *mode*參數可讓您包含或排除物件的遠端部分。 如需詳細資訊，請參閱 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)。  
  
 *Mode*引數可以有下列值：  
  
|值|描述|  
|-----------|-----------------|  
|ALL|傳回物件或資料庫的儲存體統計資料，包括本機部分和遠端部分。|  
|LOCAL_ONLY|只傳回物件或資料庫的本機部分的儲存統計資料。 如果物件或資料庫未啟用 Stretch，會傳回與 when @mode = ALL 相同的統計資料。|  
|REMOTE_ONLY|只傳回物件或資料庫之遠端部分的儲存統計資料。 當下列其中一個條件成立時，此選項會引發錯誤：<br /><br /> 資料表未啟用 Stretch。<br /><br /> 資料表已啟用延展功能，但您從未啟用過資料移轉。 在此情況下，遠端資料表還沒有架構。<br /><br /> 使用者已手動卸載遠端資料表。<br /><br /> 布建遠端資料封存會傳回「成功」狀態，但事實上卻失敗。|  
  
 *mode*是**Varchar （11）**，預設值是**N'ALL '**。  
  
`[ @oneresultset = ] oneresultset`指出是否傳回單一結果集。 *Oneresultset*引數可以有下列值：  
  
|值|描述|  
|-----------|-----------------|  
|0|當* \@objname*為 null 或未指定時，會傳回兩個結果集。 有兩個結果集是預設行為。|  
|1|當* \@objname* = null 或未指定時，會傳回單一結果集。|  
  
 *oneresultset*是**bit**，預設值是**0**。  

`[ @include_total_xtp_storage] 'include_total_xtp_storage'`
**適用于：** [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)]、 [!INCLUDE[sssds-md](../../includes/sssds-md.md)]。  
  
 當@oneresultset= 1 時，參數@include_total_xtp_storage會決定單一結果集是否包含 MEMORY_OPTIMIZED_DATA 儲存體的資料行。 預設值為0，也就是根據預設（如果省略參數），XTP 資料行不會包含在結果集中。  

## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
 如果省略*objname* ，且*oneresultset*的值為0，則會傳回下列結果集以提供目前的資料庫大小資訊。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|目前資料庫的名稱。|  
|**database_size**|**Varchar （18）**|目前資料庫的大小 (以 MB 為單位)。 **database_size**同時包含資料和記錄檔。|  
|**未配置空間**|**Varchar （18）**|資料庫中尚未保留給資料庫物件的空間。|  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**留**|**Varchar （18）**|資料庫中的物件所配置的空間總量。|  
|**data**|**Varchar （18）**|資料所用的空間總量。|  
|**index_size**|**Varchar （18）**|索引所用的空間總量。|  
|**未使用**|**Varchar （18）**|保留給資料庫中之物件但尚未使用的空間總量。|  
  
 如果省略*objname* ，且*oneresultset*的值為1，則會傳回下列單一結果集，以提供目前的資料庫大小資訊。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|目前資料庫的名稱。|  
|**database_size**|**Varchar （18）**|目前資料庫的大小 (以 MB 為單位)。 **database_size**同時包含資料和記錄檔。|  
|**未配置空間**|**Varchar （18）**|資料庫中尚未保留給資料庫物件的空間。|  
|**留**|**Varchar （18）**|資料庫中的物件所配置的空間總量。|  
|**data**|**Varchar （18）**|資料所用的空間總量。|  
|**index_size**|**Varchar （18）**|索引所用的空間總量。|  
|**未使用**|**Varchar （18）**|保留給資料庫中之物件但尚未使用的空間總量。|  
  
 如果指定*objname* ，則會針對指定的物件傳回下列結果集。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(128)**|要求的空間使用方式資訊所屬的物件名稱。<br /><br /> 不會傳回物件的結構描述名稱。 如果需要架構名稱，請使用[sys.databases dm_db_partition_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md)或[dm_db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)動態管理檢視來取得對等的大小資訊。|  
|**rows**|**char （20）**|資料表現有的資料列數。 如果指定的物件是一個 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 佇列，這個資料行會指出佇列中的訊息數目。|  
|**留**|**Varchar （18）**|*Objname*保留空間的總數量。|  
|**data**|**Varchar （18）**|*Objname*中的資料所使用的總空間量。|  
|**index_size**|**Varchar （18）**|*Objname*中的索引所使用的空間總量。|  
|**未使用**|**Varchar （18）**|保留給*objname*但尚未使用的總空間量。|  
 
如果未指定任何參數，這就是預設模式。 系統會傳回下列結果集，詳述磁片上的資料庫大小資訊。 

|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|目前資料庫的名稱。|  
|**database_size**|**Varchar （18）**|目前資料庫的大小 (以 MB 為單位)。 **database_size**同時包含資料和記錄檔。 如果資料庫具有 MEMORY_OPTIMIZED_DATA 檔案群組，這會包含檔案群組中所有檢查點檔案的磁片大小總計。|  
|**未配置空間**|**Varchar （18）**|資料庫中尚未保留給資料庫物件的空間。 如果資料庫具有 MEMORY_OPTIMIZED_DATA 檔案群組，這會包含在檔案群組中具有狀態預先建立之檢查點檔案的磁片大小總計。|  

資料庫中的資料表所使用的空間：（這個結果集不會反映記憶體優化資料表，因為沒有每個資料表的磁片使用量計量） 

|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**留**|**Varchar （18）**|資料庫中的物件所配置的空間總量。|  
|**data**|**Varchar （18）**|資料所用的空間總量。|  
|**index_size**|**Varchar （18）**|索引所用的空間總量。|  
|**未使用**|**Varchar （18）**|保留給資料庫中之物件但尚未使用的空間總量。|

只有在資料庫具有具有至少一個容器的 MEMORY_OPTIMIZED_DATA 檔案群組時，**才**會傳回下列結果集： 

|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**xtp_precreated**|**Varchar （18）**|具有狀態預先建立的檢查點檔案大小總計（以 KB 為單位）。 計算整體資料庫中未配置的空間。 [例如，如果有 600000 KB 的預先建立檢查點檔案，則此資料行包含 ' 600000 KB ']|  
|**xtp_used**|**Varchar （18）**|在 [結構]、[作用中] 和 [合併目標] 底下狀態的檢查點檔案大小總計，以 KB 為單位。 這是記憶體優化資料表中的資料主動使用的磁碟空間。|  
|**xtp_pending_truncation**|**Varchar （18）**|狀態 WAITING_FOR_LOG_TRUNCATION 的檢查點檔案大小總計（以 KB 為單位）。 這是在記錄截斷發生後，用於等待清除之檢查點檔案的磁碟空間。|

如果省略*objname* ，oneresultset 的值為1，而*include_total_xtp_storage*為1，則會傳回下列單一結果集，以提供目前的資料庫大小資訊。 如果`include_total_xtp_storage`為0（預設值），則會省略最後三個數據行。 

|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|目前資料庫的名稱。|  
|**database_size**|**Varchar （18）**|目前資料庫的大小 (以 MB 為單位)。 **database_size**同時包含資料和記錄檔。 如果資料庫具有 MEMORY_OPTIMIZED_DATA 檔案群組，這會包含檔案群組中所有檢查點檔案的磁片大小總計。|
|**未配置空間**|**Varchar （18）**|資料庫中尚未保留給資料庫物件的空間。 如果資料庫具有 MEMORY_OPTIMIZED_DATA 檔案群組，這會包含在檔案群組中具有狀態預先建立之檢查點檔案的磁片大小總計。|  
|**留**|**Varchar （18）**|資料庫中的物件所配置的空間總量。|  
|**data**|**Varchar （18）**|資料所用的空間總量。|  
|**index_size**|**Varchar （18）**|索引所用的空間總量。|  
|**未使用**|**Varchar （18）**|保留給資料庫中之物件但尚未使用的空間總量。|
|**xtp_precreated**|**Varchar （18）**|具有狀態預先建立的檢查點檔案大小總計（以 KB 為單位）。 這會計入整個資料庫中的未配置空間。 如果資料庫沒有至少包含一個容器的 memory_optimized_data 檔案群組，則會傳回 Null。 *只有當@include_total_xtp_storage= 1 時，才會包含這個資料行*。| 
|**xtp_used**|**Varchar （18）**|在 [結構]、[作用中] 和 [合併目標] 底下狀態的檢查點檔案大小總計，以 KB 為單位。 這是記憶體優化資料表中的資料主動使用的磁碟空間。 如果資料庫沒有至少包含一個容器的 memory_optimized_data 檔案群組，則會傳回 Null。 *只有當@include_total_xtp_storage= 1 時，才會包含這個資料行*。| 
|**xtp_pending_truncation**|**Varchar （18）**|狀態 WAITING_FOR_LOG_TRUNCATION 的檢查點檔案大小總計（以 KB 為單位）。 這是在記錄截斷發生後，用於等待清除之檢查點檔案的磁碟空間。 如果資料庫沒有至少包含一個容器的 memory_optimized_data 檔案群組，則會傳回 Null。 只有在時`@include_total_xtp_storage=1`，才會包含這個資料行。|

## <a name="remarks"></a>備註  
 **database_size**一律大於**保留** + **未配置空間**的總和，因為它包含記錄檔的大小，但**保留**且**unallocated_space**只考慮資料頁。  
  
 XML 索引和全文檢索索引所使用的頁面會包含在兩個結果集的**index_size**中。 當指定*objname*時，物件的 XML 索引和全文檢索索引的頁面也會計算在**保留**和**index_size**的總結果中。  
  
 如果針對資料庫或具有空間索引的物件計算空間使用量，則空間大小的資料行（例如**database_size**、**保留**和**index_size**）會包含空間索引的大小。  
  
 當指定*updateusage*時，會[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]掃描資料庫中的資料頁，並針對每個資料表所使用的儲存**空間，進行**任何必要**allocation_units**的更正。 例如，在某些狀況下，在卸除索引之後，資料表的空間資訊可能不是目前的資訊。 *updateusage*可能需要一些時間才能在大型資料表或資料庫上執行。 只有當您懷疑傳回不正確的值，以及當進程對資料庫中的其他使用者或處理常式不會有負面影響時，才使用*updateusage* 。 如果願意的話，您可以個別執行 DBCC UPDATEUSAGE。  
  
> [!NOTE]  
>  當您卸除或重建大型索引時，或卸除或截斷大型資料表時，[!INCLUDE[ssDE](../../includes/ssde-md.md)] 會延遲取消配置實際的頁面及其相關聯鎖定，直到認可交易之後。 延遲的卸除作業並不會立即釋出已配置的空間。 因此，在卸載或截斷大型物件之後， **sp_spaceused**所傳回的值，可能不會反映實際可用的磁碟空間。  
  
## <a name="permissions"></a>權限  
 執行 **sp_spaceused** 的權限會授與 **public** 角色。 只有 **db_owner** 固定資料庫角色的成員，可以指定 **\@updateusage** 參數。  
  
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
  
### <a name="c-displaying-space-usage-information-about-the-remote-table-associated-with-a-stretch-enabled-table"></a>C. 顯示與已啟用 Stretch 之資料表相關聯之遠端資料表的空間使用方式資訊  
 下列範例會使用** \@mode**引數來指定遠端目標，以摘要說明與已啟用 Stretch 之資料表相關聯的遠端資料表所使用的空間。 如需詳細資訊，請參閱 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)。  
  
```sql  
USE StretchedAdventureWorks2016  
GO  
EXEC sp_spaceused N'Purchasing.Vendor', @mode = 'REMOTE_ONLY'  
```  
  
### <a name="d-displaying-space-usage-information-for-a-database-in-a-single-result-set"></a>D. 在單一結果集中顯示資料庫的空間使用方式資訊  
 下列範例會匯總單一結果集中目前資料庫的空間使用狀況。  
  
```sql  
USE AdventureWorks2016  
GO  
EXEC sp_spaceused @oneresultset = 1  
```  

### <a name="e-displaying-space-usage-information-for-a-database-with-at-least-one-memory_optimized-file-group-in-a-single-result-set"></a>E. 在單一結果集中顯示至少有一個 MEMORY_OPTIMIZED 檔案群組之資料庫的空間使用量資訊 
 下列範例會使用單一結果集中至少一個 MEMORY_OPTIMIZED 檔案群組，來匯總目前資料庫的空間使用量。
 
```sql
USE WideWorldImporters
GO
EXEC sp_spaceused @updateusage = 'FALSE', @mode = 'ALL', @oneresultset = '1', @include_total_xtp_storage = '1';
GO
``` 

### <a name="f-displaying-space-usage-information-for-a-memory_optimized-table-object-in-a-database"></a>F. 顯示資料庫中 MEMORY_OPTIMIZED 資料表物件的空間使用方式資訊。
 下列範例會使用至少一個 MEMORY_OPTIMIZED 檔案群組，摘要說明目前資料庫中 MEMORY_OPTIMIZED table 物件的空間使用量。
 
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
 [CREATE TABLE &#40;Transact-sql&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [DBCC UPDATEUSAGE &#40;Transact-sql&#41;](../../t-sql/database-console-commands/dbcc-updateusage-transact-sql.md)   
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)   
 [sys.allocation_units &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [sys.databases &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.databases &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
