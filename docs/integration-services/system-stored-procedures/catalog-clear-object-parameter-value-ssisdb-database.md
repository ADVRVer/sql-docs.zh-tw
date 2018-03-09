---
title: "catalog.clear_object_parameter_value (SSISDB 資料庫) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: dcbbb714-a051-4805-9e2b-2c2fb647c890
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 799b3c1305daa8cdc7021a79a4c8f8007ef91241
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="catalogclearobjectparametervalue-ssisdb-database"></a>catalog.clear_object_parameter_value (SSISDB 資料庫)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  清除現有 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案或封裝儲存在伺服器上的參數值。  
  
## <a name="syntax"></a>語法  
  
```sql  
catalog.clear_object_parameter [ @folder_name = ] folder_name   
    , [ @project_name = ] project_name   
    , [ @object_type = ] object_type   
    , [ @object_name = ] object_name   
    , [ @parameter_ name = ] parameter_name  
```  
  
## <a name="arguments"></a>引數  
 [ @folder_name = ] *folder_name*  
 包含專案之資料夾的名稱。 *folder_name* 是 **nvarchar(128)**。  
  
 [ @project_name = ] *project_name*  
 專案的名稱。 *project_name* 是 **nvarchar(128)**。  
  
 [ @object_type = ] *object_type*  
 物件的類型。 有效的值包括 `20` (專案) 和 `30` (封裝)。 *object_type* 是 **smallInt**。  
  
 [ @ object _name = ] *object _name*  
 封裝名稱。 *object _name* 是 **nvarchar(260)**。  
  
 [ @parameter_ name = ] *parameter_name*  
 參數的名稱。 *parameter_ name* 是 **nvarchar(128)**。  
  
## <a name="return-code-value"></a>傳回碼值  
 0 (成功)  
  
## <a name="result-sets"></a>結果集  
 無  
  
## <a name="permissions"></a>Permissions  
 這個預存程序需要下列其中一個權限：  
  
-   專案的 READ 和 MODIFY 權限  
  
-   **ssis_admin** 資料庫角色的成員資格  
  
-   **系統管理員**伺服器角色的成員資格  
  
## <a name="errors-and-warnings"></a>錯誤和警告  
 下列清單將描述可能會造成 clear_object_parameter 預存程序引發錯誤的某些條件：  
  
-   指定了無效的物件類型，或在專案中找不到物件名稱。  
  
-   專案不存在、無法存取專案或專案名稱無效。  
  
-   指定的參數名稱無效。  
  
-   使用者未具備適當的權限。  
  
  
