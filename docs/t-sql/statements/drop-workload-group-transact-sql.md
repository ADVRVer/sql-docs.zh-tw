---
title: DROP WORKLOAD GROUP (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_WORKLOAD_GROUP_TSQL
- DROP WORKLOAD GROUP
dev_langs:
- TSQL
helpviewer_keywords:
- DROP WORKLOAD GROUP statement
ms.assetid: 1cd68450-5b58-4106-a2bc-54197ced8616
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: c4900794c3a29067c38b1fb16b127d07cf574ab8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47812596"
---
# <a name="drop-workload-group-transact-sql"></a>DROP WORKLOAD GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  卸除現有使用者定義的資源管理員工作負載群組。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)。  
  
## <a name="syntax"></a>語法  
  
```  
  
DROP WORKLOAD GROUP group_name  
[;]  
```  
  
## <a name="arguments"></a>引數  
 *group_name*  
 現有使用者定義之工作負載群組的名稱。  
  
## <a name="remarks"></a>Remarks  
 在資源管理員的內部或預設群組上，不允許使用 DROP WORKLOAD GROUP 陳述式。  
  
 當您要執行 DDL 陳述式時，建議您先熟悉資源管理員的狀態。 如需詳細資訊，請參閱 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)。  
  
 如果工作負載群組包含使用中工作階段，當呼叫 ALTER RESOURCE GOVERNOR RECONFIGURE 陳述式以套用變更時，卸除工作負載群組或將工作負載群組移到不同的資源集區將會失敗。 若要避免這個問題，您可以採取下列其中一個動作：  
  
-   等到受影響之群組的所有工作階段已經中斷連接後，重新執行 ALTER RESOURCE GOVERNOR RECONFIGURE 陳述式。  
  
-   在受影響的群組中，使用 KILL 命令明確地停止工作階段，然後重新執行 ALTER RESOURCE GOVERNOR RECONFIGURE 陳述式。  
  
-   重新啟動伺服器。 重新啟動程序完成後，將不會建立已經刪除的群組，而且已經移動的群組將會使用新的資源集區指派。  
  
-   在您已經發出 DROP WORKLOAD GROUP 陳述式但決定您不要明確地停止工作階段以套用變更的實例中，您可以使用您發出 DROP 陳述式前的相同名稱重新建立群組，然後將該群組移到原始的資源集區。 若要套用變更，請執行 ALTER RESOURCE GOVERNOR RECONFIGURE 陳述式。  
  
## <a name="permissions"></a>[權限]  
 需要 CONTROL SERVER 權限。  
  
## <a name="examples"></a>範例  
 下列範例會卸除名稱為 `adhoc` 的工作負載群組。  
  
```  
DROP WORKLOAD GROUP adhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [[資源管理員]](../../relational-databases/resource-governor/resource-governor.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
