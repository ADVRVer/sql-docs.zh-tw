---
title: MSSQLSERVER_10536 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 10536 (Database Engine error)
ms.assetid: 9f97b41f-0ef8-4ad2-aec0-906a5d7522ba
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 849175c9e620ebe88f91c344ea12b967906e1b1f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver10536"></a>MSSQLSERVER_10536
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|10536|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|PG_TOO_MANY_STMTS|  
|訊息文字|無法建立計畫指南 '%.\*ls'，因為指定的 **@plan_handle** 所對應的批次或模組中包含超過 1000 個適合的陳述式。 請為批次或模組中的每個陳述式分別指定 **statement_start_offset** 值，以各建立一個計畫指南。|  
  
## <a name="explanation"></a>說明  
指定的 **@plan_handle** 所對應的批次或模組中包含超過 1000 個適合的陳述式。  
  
## <a name="user-action"></a>使用者動作  
請為批次或模組中的每個陳述式分別指定 **statement_start_offset** 值，以各建立一個計畫指南。  
  
## <a name="see-also"></a>另請參閱  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[計畫指南](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
