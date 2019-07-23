---
title: catalog.create_environment (SSISDB 資料庫) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 66367092-9f6e-40e6-90bd-81efb078ab70
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 7871b8225e6574067befb3ab8a90af1875410def
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68110385"
---
# <a name="catalogcreateenvironment-ssisdb-database"></a>catalog.create_environment (SSISDB 資料庫)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目錄建立環境。  
  
## <a name="syntax"></a>語法  
  
```sql  
catalog.create_environment [@folder_name =] folder_name  
     , [@environment_name =] environment_name  
  [  , [@environment_description =] environment_description ]  
```  
  
## <a name="arguments"></a>引數  
 [@folder_name =] *folder_name*  
 包含環境的資料夾名稱。 *folder_name* 是 **nvarchar(128)** 。  
  
 [@environment_name =] *environment_name*  
 環境的名稱。 *environment_name* 是 **nvarchar(128)** 。  
  
 [@environment_description=] *environment_description*  
 環境的選擇性描述。 *environment_description* 是 **nvarchar(1024)** 。  
  
## <a name="return-code-value"></a>傳回碼值  
 0 (成功)  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="permissions"></a>權限  
 這個預存程序需要下列其中一個權限：  
  
-   資料夾的 READ 和 MODIFY 權限  
  
-   **ssis_admin** 資料庫角色的成員資格  
  
-   資料庫角色  
  
-   **系統管理員**伺服器角色的成員資格  
  
## <a name="errors-and-warnings"></a>錯誤和警告  
 下列清單將描述可能會引發錯誤或警告的某些條件：  
  
-   找不到資料夾名稱  
  
-   指定的資料夾中已有名稱相同的環境  
  
## <a name="remarks"></a>Remarks  
 在資料夾中，環境名稱必須是唯一的。  
  
  
