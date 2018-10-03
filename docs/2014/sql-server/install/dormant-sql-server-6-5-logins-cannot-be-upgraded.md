---
title: 無法升級休眠 SQL Server 6.5 登入 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- passwords [SQL Server], dormant logins
- dormant logins
- logins [SQL Server], upgrading dormant logins
- identifying dormant logins
- password hashes [SQL Server]
ms.assetid: ebe18a74-0375-4df4-b894-239f8fdabb64
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 03cfdc1e7c639c387e175829f34329344fd9e160
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227178"
---
# <a name="dormant-sql-server-65-logins-cannot-be-upgraded"></a>無法升級休眠 SQL Server 6.5 登入
  Upgrade Advisor 偵測到密碼無法直接升級到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 登入。  
  
 若要啟用這項登入，您必須重設其密碼。 您可以使用 ALTER LOGIN 來重設密碼。  
  
```  
ALTER LOGIN <login name> WITH PASSWORD = '<new password>' MUST_CHANGE  
```  
  
 除非已停用原則檢查，否則，將根據系統的密碼複雜性原則來驗證新密碼。 建議您使用複雜密碼，而且不停用原則檢查。 MUST_CHANGE 選項會強制使用者選取新密碼。 雖然這不是必要的條件，但建議您這麼做。  
  
 您可以使用下列查詢來識別休眠登入：  
  
```  
SELECT * FROM sysxlogins WHERE (xstatus & 2048) = 2048;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [Database Engine 升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor&#91;新增&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
