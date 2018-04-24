---
title: MSSQLSERVER_1406 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 1406 (Database Engine error)
ms.assetid: 915f97de-9b74-41f8-8bd5-b2d061416718
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0949d99e01e3b4f58060c1e1fbacc121e66639bf
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver1406"></a>MSSQLSERVER_1406
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|1406|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|DBM_BADSTATEFORFORCESERVICE|  
|訊息文字|無法安全地強制服務。 請移除資料庫鏡像及復原資料庫 "%.*ls"，以取得存取權。|  
  
## <a name="explanation"></a>說明  
[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 不能強制服務，因為鏡像狀態無法保證強制服務處理序會正確地運作。  
  
## <a name="user-action"></a>使用者動作  
移除資料庫鏡像。 然後，您就可以復原鏡像資料庫，以取得存取權。  
  
## <a name="see-also"></a>另請參閱  
[在資料庫鏡像工作階段中強制服務 &#40;Transact-SQL&#41;](~/database-engine/database-mirroring/force-service-in-a-database-mirroring-session-transact-sql.md)  
[移除資料庫鏡像 &#40;SQL Server&#41;](~/database-engine/database-mirroring/removing-database-mirroring-sql-server.md)  
  
