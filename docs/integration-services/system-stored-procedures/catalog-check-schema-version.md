---
title: catalog.check_schema_version | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: e0d5e9f5-59c6-4118-87b5-4aa5c37a7df6
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9d0568db561467e05b73993fe183d0da179fb8d0
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="catalogcheckschemaversion"></a>catalog.check_schema_version
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  判斷 SSISDB 目錄結構描述與 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 二進位檔 (ISServerExec 和 SQLCLR 組件) 是否相容。  
  
 如果該結構描述與二進位檔不相容，則 ISServerExec.exc 會記錄一個錯誤訊息。  
  
 當結構描述在套用修補程式與升級期間變更時，會遞增 SSISDB 結構描述版本。 建議您在還原 SSISDB 備份之後執行此預存程序，以確保結構描述和二進位檔相容。  
  
## <a name="syntax"></a>語法  
  
```sql  
catalog.check_schema_version [@use32bitruntime = ] use32bitruntime  
```  
  
## <a name="arguments"></a>引數  
 [ @use32bitruntime= ] *use32bitruntime*  
 當此參數設為 **True** 時，會呼叫 32 位元版本的 dtexec。 *use32bitruntime* 是 **Bool**。  
  
## <a name="result-set"></a>結果集  
 無  
  
## <a name="permissions"></a>Permissions  
 這個預存程序需要下列權限：  
  
-   **ssis_admin** 資料庫角色的成員資格。  
  
  
