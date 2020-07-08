---
title: catalog.environment_variables (SSISDB 資料庫) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 45f5aacd-505a-443b-8fc2-c7929e78cff8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: adaca2021f02d28dcb295265f8d6598515bd2e80
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85673276"
---
# <a name="catalogenvironment_variables-ssisdb-database"></a>catalog.environment_variables (SSISDB 資料庫)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  針對 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目錄中的所有環境顯示環境變數詳細資料。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|variable_id|**bigint**|環境變數的唯一識別碼 (ID)。|  
|environment_id|**bigint**|與變數相關聯之環境的唯一識別碼。|  
|NAME|**sysname**|環境變數的名稱。|  
|description|**nvarchar(1024)**|環境變數的描述。|  
|type|**nvarchar(128)**|環境變數的資料類型。|  
|sensitive|**bit**|當值為 `1` 時，變數為敏感值，會在儲存時加密。 當值為 `0` 時，變數則不是敏感值，且會在儲存為純文字。|  
|value|**sql_variant**|環境變數的值。 當 sensitive 為 `0` 時，會顯示純文字值。 當 sensitive 為 `1` 時，會顯示 **NULL**。|  
  
## <a name="remarks"></a>備註  
 這個檢視會顯示目錄中每個環境變數的資料列。  
  
## <a name="permissions"></a>權限  
 這個檢視需要下列其中一個權限：  
  
-   對應環境的 READ 權限  
  
-   **ssis_admin** 資料庫角色的成員資格  
  
-   **系統管理員**伺服器角色的成員資格  
  
> [!NOTE]  
>  當您擁有在伺服器上執行操作的權限時，也會具有檢視作業資訊的權限。 強制使用資料列層級安全性，只會顯示您具有檢視權限的資料列。  
  
  
