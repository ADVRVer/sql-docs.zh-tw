---
title: "sysextendedarticlesview (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sysextendedarticlesview_TSQL
- sysextendedarticlesview
dev_langs: TSQL
helpviewer_keywords: sysextendedarticlesview view
ms.assetid: 8bdd22f7-c268-49b6-820c-3fe603feb128
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e267d3762d601c6bfcd43ff897d96a84a08ddae2
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="sysextendedarticlesview-transact-sql"></a>sysextendedarticlesview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sysextendedarticlesview**檢視會提供已發行的發行項的相關資訊。 這份檢視儲存在散發資料庫中。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|提供發行項唯一識別碼的識別欄位。|  
|**creation_script**|**nvarchar(255)**|建立發行項之結構描述的指令碼。|  
|**del_cmd**|**nvarchar(255)**|執行於 DELETE 的命令；否則，便從記錄檔中建構。|  
|**描述**|**nvarchar(255)**|發行項的描述性項目。|  
|**dest_table**|**nvarchar （128)**|目的地資料表的名稱。|  
|**filter**|**int**|水平資料分割所用之預存程序的物件識別碼。|  
|**filter_clause**|**ntext**|用來進行水平篩選的發行項 WHERE 子句。|  
|**ins_cmd**|**nvarchar(255)**|執行於 INSERT 的命令。|  
|**name**|**nvarchar （128)**|發行項的相關聯名稱，在發行集內是唯一的。|  
|**objid**|**int**|已發行的資料表物件識別碼。|  
|**pubid**|**int**|發行項所屬發行集的識別碼。|  
|**pre_creation_cmd**|**tinyint**|DROP TABLE、DELETE TABLE 或 TRUNCATE 的預先建立命令：<br /><br /> **0** = 無。<br /><br /> **1** = 卸除。<br /><br /> **2** = 刪除。<br /><br /> **3** = TRUNCATE。|  
|**status**|**int**|發行項選項和狀態的位元遮罩，它可能是一個或多個這些值的位元邏輯 OR 結果：<br /><br /> **1** = 發行項在使用中。<br /><br /> **8** = 資料行名稱包括在 INSERT 陳述式。<br /><br /> **16** = 使用參數化陳述式。<br /><br /> **24** = 這包括在 INSERT 陳述式的資料行名稱，並使用參數化陳述式。<br /><br /> 例如，對於使用參數化陳述式的使用中發行項，這個資料行的值是 17。 0 值表示發行項不在使用中，且未定義任何其他屬性。|  
|**sync_objid**|**int**|代表發行項定義之資料表或檢視的識別碼。|  
|**型別**|**tinyint**|發行項的類型：<br /><br /> **1** = 記錄式發行項。<br /><br /> **3** = 含有手動篩選記錄檔為基礎的發行項。<br /><br /> **5** = 含有手動檢視的記錄式發行項。<br /><br /> **7** = 含有手動篩選和手動檢視的記錄式發行項。|  
|**upd_cmd**|**nvarchar(255)**|執行於 UPDATE 的命令；否則，便從記錄檔中建構。|  
|**schema_option**|**binary**|指示已發行之物件的哪些屬性要在快照集中建立指令碼。 如需支援的結構描述選項的清單，請參閱[sp_addarticle](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)。|  
|**dest_owner**|**nvarchar （128)**|目的地資料庫的資料表擁有者。|  
|**ins_scripting_proc**|**int**|複寫 INSERT 陳述式時所執行之自訂預存程序或指令碼的物件識別碼。|  
|**del_scripting_proc**|**int**|複寫 DELETE 陳述式時所執行之自訂預存程序或指令碼的物件識別碼。|  
|**upd_scripting_proc**|**int**|複寫 UPDATE 陳述式時所執行之自訂預存程序或指令碼的物件識別碼。|  
|**custom_script**|**int**|DDL 觸發程序完成時所執行之自訂指令碼或程序的物件識別碼。|  
|**fire_triggers_on_snapshot**|**int**|指出當套用快照集時，是否執行複寫的觸發程序，它可以是下列值之一：<br /><br /> **0** = 不執行觸發程序。<br /><br /> **1** = 執行觸發程序。|  
  
## <a name="see-also"></a>請參閱＜  
 [複寫資料表 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addarticle &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sysarticles &#40;TRANSACT-SQL &#41;](../../relational-databases/system-tables/sysarticles-transact-sql.md)  
  
  
