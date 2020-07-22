---
title: catalog.rename_environment (SSISDB 資料庫) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: c73d7452-31c5-4f4e-afcc-e9eca760c826
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 400b93128b19ca12550816889c732793c0e9e5d0
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86912931"
---
# <a name="catalogrename_environment-ssisdb-database"></a>catalog.rename_environment (SSISDB 資料庫)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  重新命名 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目錄中的環境。  
  
## <a name="syntax"></a>語法  
  
```sql  
catalog.rename_environment [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @new_environment_name= ] new_environment_name  
```  
  
## <a name="arguments"></a>引數  
 [ @folder_name = ] *folder_name*  
 包含環境之資料夾的名稱。 *folder_name* 是 **nvarchar(128)** 。  
  
 [ @environment_name = ] *environment_name*  
 環境的原始名稱。 *environment_name* 是 **nvarchar(128)** 。  
  
 [ @new_environment_name = ] *new_environment_name*  
 環境的新名稱。 *new_environment_name* 是 **nvarchar(128)** 。  
  
## <a name="return-code-value"></a>傳回碼值  
 0 (成功)  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="permissions"></a>權限  
 這個預存程序需要下列其中一個權限：  
  
-   環境的 MODIFY 權限  
  
-   **ssis_admin** 資料庫角色的成員資格  
  
-   **系統管理員**伺服器角色的成員資格  
  
## <a name="errors-and-warnings"></a>錯誤和警告  
 下列清單將描述可能會引發錯誤或警告的某些條件：  
  
-   原始環境名稱無效  
  
-   新的名稱已經使用於現有環境  
  
## <a name="remarks"></a>備註  
 重新命名環境時，不會自動更新來自專案的環境參考。 環境參考必須隨之更新。 即使環境參考因為變更環境名稱而中斷，這個預存程序仍然會成功。 環境參考必須在預存程序完成之後更新。  
  
> [!NOTE]  
>  當環境參考無效時，使用這些參考的對應封裝之驗證和執行將會失敗。  
  
  
