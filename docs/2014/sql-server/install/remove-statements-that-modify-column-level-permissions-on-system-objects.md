---
title: 移除修改系統物件的資料行層級權限的陳述式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- column-level permissions [SQL Server]
- removed statement permissions [SQL Server]
ms.assetid: 7f4fbbef-2696-4911-903b-63f6d9e4484a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dfc0bf1d77322bca3a95ec5d0ed49ab856ce9cf9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48125268"
---
# <a name="remove-statements-that-modify-column-level-permissions-on-system-objects"></a>移除在系統物件上修改資料行層級權限的陳述式
  Upgrade Advisor 偵測到系統物件上有非標準的資料行層級權限。 升級時，將無法保持這些權限的變更。 此外，將不再支援系統物件上的資料行層級權限。 請從設定系統物件之資料行層級權限的應用程式中移除陳述式。  
  
## <a name="component"></a>元件  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>更正動作  
 請從授與、拒絕或撤銷系統物件之資料行層級權限的應用程式中移除陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [Database Engine 升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor&#91;新增&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
