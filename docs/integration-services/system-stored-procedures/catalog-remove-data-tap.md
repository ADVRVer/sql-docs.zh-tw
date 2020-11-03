---
description: catalog.remove_data_tap
title: catalog.remove_data_tap | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: b77db3e6-478c-441a-a838-82c4de750275
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ca55276a6108cd53ffae82fd4c40089023da20fb
ms.sourcegitcommit: 80701484b8f404316d934ad2a85fd773e26ca30c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93243601"
---
# <a name="catalogremove_data_tap"></a>catalog.remove_data_tap 

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  從執行中的元件輸出移除資料點選。 資料點選的唯一識別碼與執行的執行個體相關聯。  
  
## <a name="syntax"></a>語法  
  
```sql  
catalog.remove_data_tap [ @data_tap_id = ] data_tap_id  
```  
  
## <a name="arguments"></a>引數  
 [ @data_tap_id = ] *data_tap_id*  
 使用 catalog.add_data_tap 預存程序來建立之資料點選的唯一識別碼。 *data_tap_id* 是 **bigint** 。  
  
## <a name="remarks"></a>備註  

- 如果封裝包含多個具有相同名稱的資料流程工作，則會將資料點選加入具有給定名稱的第一個資料流程工作。  
  
- 若要移除資料點選，執行的執行個體必須處於已建立狀態 ([catalog.operations &#40;SSISDB 資料庫&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md) 檢視之 [狀態]  資料行中的值為 1)。  
  
## <a name="return-codes"></a>傳回碼  
 0 (成功)  
  
 當預存程序失敗時，會擲回錯誤。  
  
## <a name="result-set"></a>結果集  
 None  
  
## <a name="permissions"></a>權限  
 這個預存程序需要下列其中一個權限：  
  
-   執行的執行個體之 MODIFY 權限  
  
-   **ssis_admin** 資料庫角色的成員資格  
  
-   **系統管理員** 伺服器角色的成員資格  
  
## <a name="errors-and-warnings"></a>錯誤和警告  
 下列清單描述會導致預存程序失敗的情況。  
  
-   使用者沒有 MODIFY 權限。  
  
## <a name="see-also"></a>另請參閱  
 [catalog.add_data_tap](../../integration-services/system-stored-procedures/catalog-add-data-tap.md)   
 [catalog.add_data_tap_by_guid](../../integration-services/system-stored-procedures/catalog-add-data-tap-by-guid.md)  
  
  
