---
title: "s (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- syscollector_config_store_TSQL
- syscollector_config_store
dev_langs: TSQL
helpviewer_keywords:
- data collector view
- syscollector_config_store view
ms.assetid: f15f6b05-6808-4b76-b6a8-48dec844cf63
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6811c1ab9fef0f15422f1d51ac9b969476e58699
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2017
---
# <a name="syscollectorconfigstore-transact-sql"></a>syscollector_config_store (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回套用至整個資料收集器 (而非收集集合執行個體) 的屬性。 這個檢視中的每個資料列都會描述特定資料收集器屬性，例如管理資料倉儲的名稱，以及管理資料倉儲所在的執行個體名稱。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|parameter_name|**nvarchar （128)**|屬性的名稱。 不可為 Null。|  
|parameter_value|**sql_variant**|屬性的實際值。 可為 Null。|  
  
## <a name="permissions"></a>Permissions  
 在 dc_operator、dc_proxy 或 dc_admin 固定資料庫角色中，需要具有檢視表或成員資格的 SELECT 權限。  
  
## <a name="remarks"></a>備註  
 可用屬性的清單是固定的，而且您只能使用適當的預存程序來變更其值。 下表說明可透過這個檢視公開的屬性。  
  
|屬性名稱|Description|  
|-------------------|-----------------|  
|CacheDirectory|收集器類型封裝在檔案系統中儲存暫存資訊的目錄名稱。<br /><br /> NULL = 使用預設的暫存 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目錄。|  
|CacheWindow|指出失敗的資料上傳的快取目錄資料保留原則。<br /><br /> -1 = 保留所有上傳失敗的資料。<br /><br /> 0 = 不要保留任何上傳失敗的資料。<br /><br /> *n*= 保留資料 *n* 次先前上傳失敗，其中 *n*  > = 1。<br /><br /> 您可以使用 sp_syscollector_set_cache_window 預存程序來變更此值。|  
|CollectorEnabled|指出資料收集器的狀態。<br /><br /> 0 = 已停用<br /><br /> 1 = 已啟用<br /><br /> 您可以使用 sp_syscollector_enable_collector 或 sp_syscollector_disable_collector 預存程序來變更此值。|  
|MDWDatabase|管理資料倉儲的名稱。 您可以使用 sp_syscollector_set_warehouse_database_name 預存程序來變更此值。|  
|MDWInstance|管理資料倉儲之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱。 您可以使用 sp_syscollector_set_warehouse_instance_name 預存程序來變更此值。|  
  
## <a name="examples"></a>範例  
 下列範例會查詢 syscollector_config_store 檢視。  
  
```tsql  
SELECT parameter_name, parameter_value  
FROM msdb.dbo.syscollector_config_store;  
```  
  
## <a name="see-also"></a>請參閱  
 [資料收集器預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [資料收集器檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [資料收集](../../relational-databases/data-collection/data-collection.md)   
 [sp_syscollector_enable_collector &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql.md)   
 [sp_syscollector_disable_collector &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql.md)   
 [sp_syscollector_set_warehouse_database_name &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-syscollector-set-warehouse-database-name-transact-sql.md)   
 [sp_syscollector_set_warehouse_instance_name &#40;TRANSACT-SQL &#41;](../../relational-databases/system-stored-procedures/sp-syscollector-set-warehouse-instance-name-transact-sql.md)   
 [sp_syscollector_set_cache_window &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-set-cache-window-transact-sql.md)  
  
  
