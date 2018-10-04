---
title: 移除卸除系統物件的陳述式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e1f355b9e13bb85f1bc91d9626e27d6ee3fafa15
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48153712"
---
# <a name="remove-statements-that-drop-system-objects"></a>移除卸除系統物件的陳述式
  Upgrade Advisor 偵測到卸除系統物件的陳述式。 系統物件，包含擴充預存程序，部署在唯讀**資源**資料庫 (mssqlsystemresource) 中且無法卸除。 請修改您的應用程式，以便撤銷或拒絕系統物件的 EXECUTE 權限。  
  
## <a name="component"></a>元件  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>描述  
 例如 DROP TABLE、 DROP PROCEDURE 陳述式及**sp_dropextendedproc**不能用來移除系統物件中，因為這些物件部署在唯讀**資源**資料庫。  
  
## <a name="corrective-action"></a>更正動作  
 請移除嘗試從應用程式中卸除系統物件的所有陳述式。 請修改您的應用程式，以便撤銷或拒絕系統物件的 EXECUTE 權限。 或者，您也可以使用介面區組態 (SAC) 工具來停用其中某些物件。 例如， **xp_cmdshell**擴充預存程序可以停用或啟用使用 SAC 工具。  
  
## <a name="see-also"></a>另請參閱  
 [Database Engine 升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor&#91;新增&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
