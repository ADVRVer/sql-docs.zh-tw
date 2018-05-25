---
title: sys.dm_os_loaded_modules (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_loaded_modules
- dm_os_loaded_modules
- sys.dm_os_loaded_modules_TSQL
- dm_os_loaded_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_loaded_modules dynamic management view
ms.assetid: 56c7743a-b568-4943-bd3b-73c57d9d641c
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1888f39f6024a0b299834217c2f8b69052761b65
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmosloadedmodules-transact-sql"></a>sys.dm_os_loaded_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對已載入至伺服器位址空間的每一個模組，各傳回一個資料列。  
  
> [!NOTE]  
>  若要呼叫從[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]，使用名稱**sys.dm_pdw_nodes_os_loaded_modules**。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**base_address**|**varbinary(8)**|處理序中的模組位址。|  
|**file_version**|**varchar(23)**|檔案的版本。 以下列格式呈現：<br /><br /> x.x:x.x|  
|**product_version**|**varchar(23)**|產品的版本。 以下列格式呈現：<br /><br /> x.x:x.x|  
|**debug**|**bit**|1 = 模組是已載入模組的偵錯版本。|  
|**修補**|**bit**|1 = 模組已修補。|  
|**發行前版本**|**bit**|1 = 模組是已載入模組的發行前版本。|  
|**private_build**|**bit**|1 = 模組是已載入模組的私用建置。|  
|**special_build**|**bit**|1 = 模組是已載入模組的特殊建置。|  
|**語言**|**int**|模組之版本資訊的語言。|  
|**公司**|**nvarchar(256)**|建立模組的公司名稱。|  
|**描述**|**nvarchar(256)**|模組的描述。|  
|**name**|**nvarchar(255)**|模組的名稱。 包含模組的完整路徑。|  
|**pdw_node_id**|**int**|**適用於**：[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此發行版本上的節點識別碼。|  
  
## <a name="permissions"></a>Permissions  
 需要伺服器的 VIEW SERVER STATE 權限。  
  
## <a name="see-also"></a>另請參閱  
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server 作業系統相關的動態管理檢視&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
