---
title: "sys.server_assembly_modules (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/15/2017
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
- server_assembly_modules_TSQL
- sys.server_assembly_modules
- server_assembly_modules
- sys.server_assembly_modules_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.server_assembly_modules catalog view
ms.assetid: af799e38-2d16-49b2-bcf5-6f9199af899e
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eeb90ab264d2ba8fd9ca2213faca6fd4a872e3d9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="sysserverassemblymodules-transact-sql"></a>sys.server_assembly_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對 TA 類型伺服器層級觸發程序的每個組件模組，各包含一個資料列。 這份檢視會將組件觸發程序對應至基礎 CLR 實作。 您可以加入至這個關聯**sys.server_triggers**。 組件必須載入到**主要**資料庫。 Tuple (object_id) 是關聯性的索引鍵。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|這是對定義這個組件模組之物件的 FOREIGN KEY 參考。|  
|**assembly_id**|**int**|建立這個模組所用之組件的識別碼。 組件必須載入到 master 資料庫中。|  
|**assembly_class**|**sysname**|定義這個模組之組件內的類別名稱。|  
|**assembly_method**|**sysname**|定義這個模組之類別內的方法名稱。 如果是彙總函式 (AF)，則為 NULL。|  
|**sys.sql_modules**|**int**|EXECUTE AS 伺服器主體的識別碼。<br /><br /> 在預設或 EXECUTE AS CALLER 的情況下為 NULL。<br /><br /> 指定主體 if 的識別碼執行 AS SELF EXECUTE AS\<主體 >。<br /><br /> -2 = EXECUTE AS OWNER。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>請參閱＜  
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [物件目錄檢視 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
