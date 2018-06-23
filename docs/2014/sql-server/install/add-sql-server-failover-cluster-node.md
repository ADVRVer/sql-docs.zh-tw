---
title: 加入 SQL Server 容錯移轉叢集節點 |Microsoft 文件
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e5035122-784f-40ee-8188-7f485a9ae3e8
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f1acda3ae51a6b248347defad1c2cad1d022ac9a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36132127"
---
# <a name="add-sql-server-failover-cluster-node"></a>加入 SQL Server 容錯移轉叢集節點
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式作業完成之前，安裝程式會驗證您的電腦組態。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝期間，System Configuration Checker (SCC) 會掃描將安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的電腦。 SCC 會檢查是否有任何狀況阻止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝作業成功。 在安裝程式啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝精靈以前，SCC 會擷取每一個項目的狀態。 然後它會比較所需條件的結果，並提供解決封鎖問題的指引。  
  
 系統組態檢查會產生報告，其中包含每個已執行規則以及執行狀態的簡短描述。 系統組態檢查報告位於 %programfiles%\Microsoft SQL Server\120\Setup Bootstrap\Log\\< YYYYMMDD_HHMM >\\。  
  
 執行安裝作業之前，請檢閱下列主題：  
  
1.  [硬體 and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [SQL Server 2014 各版本所支援的功能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [SQL Server 安裝的安全性考量](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [SQL Server 中的地區語言版本](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 其他參考資料：  
  
1.  [支援的版本與版本升級](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [安裝容錯移轉叢集之前](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="see-also"></a>另請參閱  
 [安裝規則](../../../2014/sql-server/install/install-rules.md)  
  
  