---
title: "catalog.set_worker_agent_property (SSISDB 資料庫) | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ddd2a534-6925-4d66-90e7-541c14f41de7
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1438d3a2cf200450791c085f501c49329d61154d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2017
---
# <a name="catalogsetworkeragentproperty-ssisdb-database"></a>catalog.set_worker_agent_property (SSISDB 資料庫)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

設定 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out Worker 的屬性。

## <a name="syntax"></a>語法

```sql
catalog.set_worker_agent_property [@WorkerAgentId =] WorkerAgentId, [@PropertyName =] PropertyName, [@PropertyValue =] PropertyValue 
```

## <a name="arguments"></a>引數
[@WorkerAgentId =] *WorkerAgentId*  
Scale Out Worker 的背景工作代理程式識別碼。 *WorkerAgentId* 是 **uniqueidentifier**。

[@PropertyName =] *PropertyName*  
屬性的名稱。 *PropertyName* 是 **nvarchar(256)**。

[@PropertyValue =] *PropertyValue*  
屬性的值。 *PropertyValue* 是 **nvarchar(max)**。

## <a name="remarks"></a>備註
有效屬性名稱是 **DisplayName**、**Description**、**Tags**。

## <a name="return-code-value"></a>傳回碼值  
 0 (成功)  
  
## <a name="result-sets"></a>結果集  
 無  

## <a name="permissions"></a>Permissions  
 這個預存程序需要下列其中一個權限：  
  
-   **ssis_admin** 資料庫角色的成員資格  
  
-   **sysadmin** 伺服器角色的成員資格

## <a name="errors-and-warnings"></a>錯誤和警告
  下列清單將描述可能會引發錯誤或警告的某些條件：  
  
-   使用者未具備適當的權限 

-   背景工作代理程式識別碼無效。

-   屬性名稱無效。

-   屬性值無效。  
