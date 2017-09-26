---
title: "catalog.folders （SSISDB 資料庫） |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 21a37c16-60aa-4b3f-8bca-ac90ad1697ac
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9622bd1a5f1415c9f506a00a63441081154b53ff
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="catalogfolders-ssisdb-database"></a>catalog.folders (SSISDB 資料庫)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  顯示 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目錄中的資料夾。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|id|**bigint**|資料夾的唯一識別碼。|  
|name|**sysname(nvarchar(128)**|資料夾的名稱，這在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目錄中是唯一的。|  
|description|**nvarchar （1024)**|資料夾的描述。|  
|created_by_sid|**varbinary(85)**|建立資料夾之使用者的安全性識別碼 (SID)。|  
|created_by_name|**nvarchar （128)**|建立資料夾的使用者名稱。|  
|created_time|**datetimeoffset(7)**|建立資料夾的日期和時間。|  
  
## <a name="remarks"></a>備註  
 這個檢視會顯示目錄中每個資料夾的資料列。  
  
## <a name="permissions"></a>Permissions  
 這個檢視需要下列其中一個權限：  
  
-   資料夾的 READ 權限  
  
-   成員資格**ssis_admin**資料庫角色  
  
-   成員資格**sysadmin**伺服器角色  
  
> [!NOTE]  
>  當您擁有在伺服器上執行操作的權限時，也會具有檢視作業資訊的權限。 強制使用資料列層級安全性，只會顯示您具有檢視權限的資料列。  
  
  
