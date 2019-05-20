---
title: catalog.set_environment_property (SSISDB 資料庫) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: a345675b-d32e-4624-96cf-ec656730b114
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 427af0f98682975e040452f1e2fd009526bd067d
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "65715941"
---
# <a name="catalogsetenvironmentproperty-ssisdb-database"></a>catalog.set_environment_property (SSISDB 資料庫)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  設定 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目錄中的環境屬性。  
  
## <a name="syntax"></a>語法  
  
```sql  
catalog.set_environment_property [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @property_name = ] property_name  
    , [ @property_value = ] property_value  
```  
  
## <a name="arguments"></a>引數  
 [ @folder_name = ] *folder_name*  
 包含環境之資料夾的名稱。 *folder_name* 是 **nvarchar(128)**。  
  
 [ @environment_name = ] *environment_name*  
 環境的名稱。 *environment_name* 是 **nvarchar(128)**。  
  
 [ @property_name = ] *property_name*  
 環境屬性的名稱。 *property_name* 是 **nvarchar(128)**。  
  
 [ @property_value = ] *property_value*  
 環境屬性的值。 *property_value* 是 **nvarchar(1024)**。  
  
## <a name="return-code-value"></a>傳回碼值  
 0 (成功)  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="permissions"></a>權限  
 這個預存程序需要下列其中一個權限：  
  
-   環境的 READ 和 MODIFY 權限  
  
-   **ssis_admin** 資料庫角色的成員資格  
  
-   **系統管理員**伺服器角色的成員資格  
  
## <a name="errors-and-warnings"></a>錯誤和警告  
 下列清單將描述可能會引發錯誤或警告的某些條件：  
  
-   資料夾名稱無效  
  
-   屬性名稱無效  
  
-   環境名稱無效  
  
## <a name="remarks"></a>Remarks  
 在這個版本中，只可以設定 `Description` 屬性。 `Description` 屬性的屬性值不能超過 4000 個字元。  
  
  
