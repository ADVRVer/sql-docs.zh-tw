---
title: catalog.create_folder (SSISDB 資料庫) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 06fb3549-e970-4ca2-a61f-59affb9c6dcc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 95f74f595481d9cf373c51be18cccf404b824e49
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85749655"
---
# <a name="catalogcreate_folder-ssisdb-database"></a>catalog.create_folder (SSISDB 資料庫)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目錄中建立資料夾。  
  
## <a name="syntax"></a>語法  
  
```sql  
catalog.create_folder [ @folder_name = ] folder_name, [ @folder_id = ] folder_id OUTPUT  
```  
  
## <a name="arguments"></a>引數  
 [@folder_name =] *folder_name*  
 新資料夾的名稱。 *folder_name* 是 **nvarchar(128)** 。  
  
 [@folder_name =] *folder_id*  
 資料夾的唯一識別碼 (ID)。 *folder_id* 是 **bigint**。  
  
## <a name="return-code-value"></a>傳回碼值  
 傳回資料夾識別項。  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="permissions"></a>權限  
 這個預存程序需要下列其中一個權限：  
  
-   **ssis_admin** 資料庫角色的成員資格  
  
-   **系統管理員**伺服器角色的成員資格  
  
## <a name="errors-and-warnings"></a>錯誤和警告  
如有同名的資料夾存在，預存程序會傳回錯誤。  
  
  
