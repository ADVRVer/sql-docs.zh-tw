---
title: MSSQLSERVER_10535 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10535 (Database Engine error)
ms.assetid: 478fd978-11d9-4155-8329-f599fdbec14b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b026dd0a0b9ecfc252947874b746cd5c18593f47
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68043684"
---
# <a name="mssqlserver10535"></a>MSSQLSERVER_10535
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|10535|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|PG_NO_PLAN|  
|訊息文字|無法建立計畫指南 '%.*ls'，因為在計畫快取中找不到指定計畫控制代碼的對應計畫。 請指定快取的計畫控制代碼。 如需快取的計畫控制代碼清單，請查詢 sys.dm_exec_query_stats 動態管理檢視。|  
  
## <a name="explanation"></a>說明  
在計畫快取中找不到指定計畫控制代碼的對應計畫。  
  
## <a name="user-action"></a>使用者動作  
請指定快取的計畫控制代碼。 如需快取的計畫控制代碼清單，請查詢 sys.dm_exec_query_stats 動態管理檢視。  
  
## <a name="see-also"></a>另請參閱  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
[sys.dm_exec_query_stats &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
