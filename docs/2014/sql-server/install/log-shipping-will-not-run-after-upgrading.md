---
title: 記錄傳送將不會在升級之後執行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server]
ms.assetid: 6727cb7d-ac01-4972-a730-dbb7cdc29705
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: df9616830fb9aed775640eb784909c1a8ef0fee4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37305058"
---
# <a name="log-shipping-will-not-run-after-upgrading"></a>升級之後，不會執行記錄傳送
  Upgrade Advisor 偵測到您正在使用記錄傳送。 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 記錄傳送與 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中的記錄傳送不相容，也不能直接升級。 請在升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 之後，使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或預存程序重新設定記錄傳送。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Agent 記錄傳送作業類別目錄會造成升級失敗](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [升級會將 SQL Server Agent 使用者 Proxy 帳戶變更為暫時的 upgradedproxyaccount](../../../2014/sql-server/install/upgrading-changes-sql-server-agent-user-proxy-account-to-temporary-account.md)   
 [Database Engine 升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor&#91;新增&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
