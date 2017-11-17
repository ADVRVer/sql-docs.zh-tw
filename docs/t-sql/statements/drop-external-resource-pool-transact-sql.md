---
title: "卸除的外部資源集區 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/17/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP EXTERNAL RESOURCE POOL
- DROP_EXTERNAL_RESOURCE_POOL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP EXTERNAL RESOURCE POOL statement
ms.assetid: e2fa01bd-96ff-4ea9-bb08-6cb6b6adf68c
caps.latest.revision: 6
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a0aae6de75280fb0e32879ece5acea6d0fd94f3c
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="drop-external-resource-pool-transact-sql"></a>卸除的外部資源集區 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  刪除資源管理員外部的資源集區用來定義外部處理序的資源。 針對 R 服務外部集區管理`rterm.exe`， `BxlServer.exe`，及其所衍生的其他處理序。 外部資源集區會建立使用[CREATE EXTERNAL RESOURCE POOL &#40;TRANSACT-SQL &#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)使用和修改[ALTER EXTERNAL RESOURCE POOL &#40;TRANSACT-SQL &#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md).  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [TRANSACT-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)。  
  
## <a name="syntax"></a>語法  
  
```  
DROP EXTERNAL RESOURCE POOL pool_name  
```  
  
## <a name="arguments"></a>引數  
 *pool_name*  
 要刪除的外部資源集區名稱。  
  
## <a name="remarks"></a>備註  
 如果它包含工作負載群組，您無法卸除的外部資源集區。  
  
 您無法卸除資源管理員的預設或內部集區。  
  
 重新設定未 n  
  
 當您要執行 DDL 陳述式時，建議您先熟悉資源管理員的狀態。 如需詳細資訊，請參閱[Resource Governor](../../relational-databases/resource-governor/resource-governor.md)。  
  
## <a name="permissions"></a>Permissions  
 需要 `CONTROL SERVER` 權限。  
  
## <a name="examples"></a>範例  
 下列範例會卸除名稱為外部資源集區`ex_pool`。  
  
```  
DROP EXTERNAL RESOURCE POOL ex_pool;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [啟用外部指令碼伺服器組態選項](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [SQL Server R services 已知的問題](../../advanced-analytics/r-services/known-issues-for-sql-server-r-services.md)   
 [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [ALTER 外部資源集區 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [卸除資源集區 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)  
  
  

