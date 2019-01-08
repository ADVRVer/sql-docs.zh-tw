---
title: IHarticles (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHarticles
- IHarticles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHarticles system table
ms.assetid: 773ef9b7-c993-4629-9516-70c47b9dcf65
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cc1a800ff61bde8e4d446462143bf0d333a16fe7
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2018
ms.locfileid: "52802610"
---
# <a name="iharticles-transact-sql"></a>IHarticles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHarticles**系統資料表包含每個發行項複寫從非 SQL Server 發行者使用目前散發者的一個資料列。 這份資料表儲存在散發資料庫中。  
  
## <a name="definition"></a>定義  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**article_id**|**int**|提供發行項唯一識別碼的識別欄位。|  
|**name**|**sysname**|發行項的相關聯名稱，在發行集內是唯一的。|  
|**publication_id**|**smallint**|發行項所屬發行集的識別碼。|  
|**table_id**|**int**|從發行之資料表的識別碼[IHpublishertables](../../relational-databases/system-tables/ihpublishertables-transact-sql.md)。|  
|**publisher_id**|**smallint**|非 SQL Server 發行者的識別碼。|  
|**creation_script**|**nvarchar(255)**|發行項的結構描述指令碼。|  
|**del_cmd**|**nvarchar(255)**|當隨著資料表發行項而複寫刪除時，所用的複寫命令類型。 如需詳細資訊，請參閱[指定交易式發行項變更的傳播方式](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)。|  
|**filter**|**int**|此資料行未使用，且包含只是為了讓[sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)檢視**IHarticles**相容於資料表[sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)用於 SQL Server 文件 （檢視[sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md))。|  
|**filter_clause**|**ntext**|用來進行水平篩選且寫在非 SQL 發行者所能解譯的標準 Transact-SQL 中的發行項 WHERE 子句。|  
|**ins_cmd**|**nvarchar(255)**|當隨著資料表發行項而複寫插入時，所用的複寫命令類型。 如需詳細資訊，請參閱[指定交易式發行項變更的傳播方式](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)。|  
|**pre_creation_cmd**|**tinyint**|當訂閱者端已有同名物件存在時，在套用初始快照集之前所執行的命令。<br /><br /> **0** = 無-不執行命令。<br /><br /> **1** = DROP-卸除目的地資料表。<br /><br /> **2** = DELETE-刪除目的地資料表中的資料。<br /><br /> **3** = TRUNCATE-截斷目的地資料表。|  
|**status**|**tinyint**|發行項選項和狀態的位元遮罩，它可能是一個或多個這些值的位元邏輯 OR 結果：<br /><br /> **0** = 無其他內容。<br /><br /> **1** = 作用。<br /><br /> **8** = 包含 INSERT 陳述式中的資料行名稱。<br /><br /> **16** = 使用參數化陳述式。<br /><br /> 例如，對於使用參數化陳述式的使用中發行項，這個資料行的值是 17。 0 值表示發行項不在使用中，且未定義任何其他屬性。|  
|**type**|**tinyint**|發行項的類型：<br /><br /> **1** = 記錄式發行項。|  
|**upd_cmd**|**nvarchar(255)**|當隨著資料表發行項而複寫更新時，所用的複寫命令類型。 如需詳細資訊，請參閱[指定交易式發行項變更的傳播方式](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)。|  
|**schema_option**|**binary(8)**|給定發行項之結構描述產生選項的點陣圖，它可能是一或多個這些值的位元邏輯 OR 結果：<br /><br /> **0x00** = 停用快照集代理程式的指令碼，並使用所提供的 CreationScript。<br /><br /> **0x01** = 產生物件的建立 （CREATE TABLE、 CREATE PROCEDURE 等等）。<br /><br /> **0x10** = 產生對應的叢集索引。<br /><br /> **0x40** = 產生對應的非叢集索引。<br /><br /> **0x80** = 包含宣告式參考完整性的主索引鍵。<br /><br /> **0x1000** = 複寫資料行層級定序。 注意：依預設，會設定 Oracle 發行者的這個選項來啟用區分大小寫的比較。<br /><br /> **0x4000** = 複寫唯一索引鍵，如果資料表發行項上定義。<br /><br /> **0x8000** = 主索引鍵和唯一索引鍵的資料表發行項作為使用 ALTER TABLE 陳述式條件約束的複寫。|  
|**dest_owner**|**sysname**|目的地資料庫的資料表擁有者。|  
|**dest_table**|**sysname**|目的地資料表的名稱。|  
|**tablespace_name**|**nvarchar(255)**|識別發行項之記錄資料表所用的資料表空間。|  
|**objid**|**int**|此資料行未使用，且包含只是為了讓[sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)檢視**IHarticles**相容於資料表[sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)用於 SQL Server 文件 （檢視[sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md))。|  
|**sync_objid**|**int**|此資料行未使用，且包含只是為了讓[sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)檢視**IHarticles**相容於資料表[sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)用於 SQL Server 文件 （檢視[sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md))。|  
|**description**|**nvarchar(255)**|發行項的描述性項目。|  
|**publisher_status**|**int**|用來指出是否已定義的檢視定義已發行之發行項，藉由呼叫[sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)。<br /><br /> **0** = [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)已呼叫。<br /><br /> **1** = [sp_articleview](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)尚未呼叫。|  
|**article_view_owner**|**nvarchar(255)**|記錄讀取器代理程式所用的發行者之同步處理物件的擁有者。|  
|**article_view**|**nvarchar(255)**|記錄讀取器代理程式所用的發行者之同步處理物件。|  
|**ins_scripting_proc**|**int**|此資料行未使用，且包含只是為了讓[sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)檢視**IHarticles**相容於資料表[sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)用於 SQL Server 文件 （檢視[sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md))。|  
|**del_scripting_proc**|**int**|此資料行未使用，且包含只是為了讓[sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)檢視**IHarticles**相容於資料表[sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)用於 SQL Server 文件 （檢視[sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md))。|  
|**upd_scripting_proc**|**int**|此資料行未使用，且包含只是為了讓[sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)檢視**IHarticles**相容於資料表[sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)用於 SQL Server 文件 （檢視[sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md))。|  
|**custom_script**|**int**|此資料行未使用，且包含只是為了讓[sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)檢視**IHarticles**相容於資料表[sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)用於 SQL Server 文件 （檢視[sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md))。|  
|**fire_triggers_on_snapshot**|**bit**|此資料行未使用，且包含只是為了讓[sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)檢視**IHarticles**相容於資料表[sysarticles](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)用於 SQL Server 文件 （檢視[sysarticles](../../relational-databases/system-tables/sysarticles-transact-sql.md))。|  
|**instance_id**|**int**|識別已發行的資料表之發行項記錄的目前執行個體。|  
|**use_default_datatypes**|**bit**|指出發行項是否使用預設資料類型對應;值為**1**表示使用預設資料類型對應。|  
  
## <a name="see-also"></a>另請參閱  
 [異質資料庫複寫](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [複寫資料表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視&#40;Transact SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addarticle &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_changearticle &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)  
  
  
