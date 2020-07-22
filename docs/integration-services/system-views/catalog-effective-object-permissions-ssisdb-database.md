---
title: catalog.effective_object_permissions (SSISDB 資料庫) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
helpviewer_keywords:
- catalog.effective_object_permissions views [Integration Services]
- effective_object_permissions view [Integration Services]
ms.assetid: e70c4ce9-79f5-44df-ac75-6c29b6e38776
author: chugugrace
ms.author: chugu
ms.openlocfilehash: af72db9d78859f9065673aa145bc4b763199b298
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86912669"
---
# <a name="catalogeffective_object_permissions-ssisdb-database"></a>catalog.effective_object_permissions (SSISDB 資料庫)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  針對 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目錄中的所有物件顯示目前主體的有效權限。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|object_type|**smallint**|安全性實體物件的類型。 安全性實體物件類型包括資料夾 (`1`)、專案 (`2`)、環境 (`3`) 和作業 (`4`)。|  
|object_id|**bigint**|物件的唯一識別碼 (ID) 或主索引鍵。|  
|permission_type|**smallint**|權限的類型。|  
  
## <a name="remarks"></a>備註  
 這個檢視會顯示下表列出的權限類型：  
  
|permission_type 值|權限名稱|權限描述|適用的物件類型|  
|----------------------------|---------------------|----------------------------|-----------------------------|  
|`1`|READ|允許主體讀取會被視為物件一部分 (例如屬性) 的資訊。 它不允許主體列舉或讀取物件內所包含之其他主體的內容。|資料夾、專案、環境、作業|  
|`2`|MODIFY|允許主體修改會被視為物件一部分 (例如屬性) 的資訊。 它不允許主體修改物件內所包含之其他主體的內容。|資料夾、專案、環境、作業|  
|`3`|執行 CREATE 陳述式之前，請先執行|允許主體執行專案中所有的封裝。|隨附此逐步解說的專案|  
|`4`|MANAGE_PERMISSIONS|允許主體將權限指派至物件。|資料夾、專案、環境、作業|  
|`100`|CREATE_OBJECTS|允許主體在資料夾中建立物件。|資料夾|  
|`101`|READ_OBJECTS|允許主體讀取資料夾中的所有物件。|資料夾|  
|`102`|MODIFY_OBJECTS|允許主體修改資料夾中的所有物件。|資料夾|  
|`103`|EXECUTE_OBJECTS|允許主體執行來自資料夾中所有專案的所有封裝。|資料夾|  
|`104`|MANAGE_OBJECT_PERMISSIONS|允許主體管理資料夾中所有物件的權限。|資料夾|  
  
 只會評估呼叫者具有權限的物件。 權限會根據下列項目計算：  
  
-   明確權限  
  
-   繼承權限  
  
-   主體在角色中的成員資格  
  
-   主體在群組中的成員資格  
  
## <a name="permissions"></a>權限  
 使用者只可以看到本身和具有成員資格之角色的有效權限。  
  
  
