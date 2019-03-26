---
title: catalog.grant_permission (SSISDB 資料庫) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
helpviewer_keywords:
- grant_permission stored procedure [Integration Services]
- catalog.grant_permission stored procedure [Integration Services]
ms.assetid: e72cfd52-de66-45e9-98b9-b8580ac7b956
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b0e129306c256106da59c890d32a96c9b1d81abd
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2019
ms.locfileid: "58290184"
---
# <a name="cataloggrantpermission-ssisdb-database"></a>catalog.grant_permission (SSISDB 資料庫)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  為 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目錄中的安全性實體物件授與權限。  
  
## <a name="syntax"></a>語法  
  
```sql
catalog.grant_permission [ @object_type = ] object_type  
    , [ @object_id = ] object_id  
    , [ @principal_id = ] principal_id  
    , [ @permission_type = ] permission_type  
```  
  
## <a name="arguments"></a>引數  
 [ @object_type = ] *object_type*  
 安全性實體物件的類型。 安全性實體物件類型包含資料夾 (`1`)、專案 (`2`)、環境 (`3`) 和作業 (`4`)。*object_type* 是 **smallint**_。_  
  
 [ @object_id = ] *object_id*  
 安全性實體物件的唯一識別碼 (ID)。 *object_id* 是 **bigint**。  
  
 [ @principal_id = ] *principal_id*  
 要授與其權限之主體的識別碼。 *principal_id* 是 **int**。  
  
 [ @permission_type = ] *permission_type*  
 要授與的權限類型。 *permission_type* 是 **smallint**。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功)  
  
 1 (object_class 無效)  
  
 2 (object_id 不存在)  
  
 3 (主體不存在)  
  
 4 (權限無效)  
  
 5 (其他錯誤)  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="permissions"></a>權限  
 這個預存程序需要下列其中一個權限：  
  
-   專案的 ASSIGN_PERMISSIONS 權限  
  
-   **ssis_admin** 資料庫角色的成員資格  
  
-   **系統管理員**伺服器角色的成員資格  

由 SQL Server 驗證的登入不能呼叫這個程序。 sa 登入也不能呼叫它。
  
## <a name="remarks"></a>Remarks  
 這個預存程序可讓您授與下表所述的權限類型：  
  
|permission_type 值|權限名稱|權限描述|適用的物件類型|  
|----------------------------|---------------------|----------------------------|-----------------------------|  
|`1`|READ|允許主體讀取會被視為物件一部分 (例如屬性) 的資訊。 它不允許主體列舉或讀取物件內所包含之其他主體的內容。|資料夾、專案、環境、作業|  
|`2`|MODIFY|允許主體修改會被視為物件一部分 (例如屬性) 的資訊。 它不允許主體修改物件內所包含之其他主體的內容。|資料夾、專案、環境、作業|  
|`3`|執行 CREATE 陳述式之前，請先執行|允許主體執行專案中所有的封裝。|專案|  
|`4`|MANAGE_PERMISSIONS|允許主體將權限指派至物件。|資料夾、專案、環境、作業|  
|`100`|CREATE_OBJECTS|允許主體在資料夾中建立物件。|資料夾|  
|`101`|READ_OBJECTS|允許主體讀取資料夾中的所有物件。|資料夾|  
|`102`|MODIFY_OBJECTS|允許主體修改資料夾中的所有物件。|資料夾|  
|`103`|EXECUTE_OBJECTS|允許主體執行來自資料夾中所有專案的所有封裝。|資料夾|  
|`104`|MANAGE_OBJECT_PERMISSIONS|允許主體管理資料夾中所有物件的權限。|資料夾|  
  
## <a name="errors-and-warnings"></a>錯誤和警告  
 請參閱＜傳回碼值＞一節以了解相關的錯誤和警告。  
  
  
