---
title: SQL Server 登入密碼逾期 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7e3bf9da-a436-433d-847a-47c30428cad3
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 81140c252be05bb75bee1800a988fe70e67d2bf0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32952993"
---
# <a name="sql-server-login-password-expiration"></a>SQL Server 登入密碼逾期
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  此規則會檢查每一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入的「密碼逾期」是否已啟用。 如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證已啟用，而且作業系統版本比 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]舊，則攻擊者可能會重複利用已知的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入密碼。  
  
## <a name="best-practices-recommendations"></a>最佳做法建議  
 我們建議您將作業系統升級到 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]。  
  
 如果您的環境中不需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，請使用 Windows 驗證。 如需詳細資訊，請參閱 [選擇驗證模式](../../relational-databases/security/choose-an-authentication-mode.md)。  
  
 針對所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入啟用「密碼逾期」。 使用 [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) 來為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入設定密碼原則。  
  
## <a name="for-more-information"></a>詳細資訊  
 [密碼原則](../../relational-databases/security/password-policy.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用原則式管理來監視和強制最佳做法](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
