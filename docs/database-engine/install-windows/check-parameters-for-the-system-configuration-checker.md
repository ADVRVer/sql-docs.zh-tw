---
title: 檢查 System Configuration Checker 的參數 | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, system configuration checks
- failed system configuration checks [SQL Server]
- verifying configuration before installation
- SCC [SQL Server]
- system configuration checker
- scanning computer before installation [SQL Server]
- checking configuration before installation
- status information [SQL Server], system configuration checker
- parameters [SQL Server], system configuration checker
- configuration checkers [SQL Server]
- Setup [SQL Server], system configuration checker
ms.assetid: 8e712c15-6bfa-4d71-b303-9526101e5594
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: e3f6682dab001ac01ad811a4b15a989b91ef81ed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68052290"
---
# <a name="check-parameters-for-the-system-configuration-checker"></a>檢查 System Configuration Checker 的參數

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝期間，System Configuration Checker (SCC) 會掃描將安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的電腦。 SCC 會檢查是否有任何狀況阻止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝成功。 在安裝程式啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝精靈以前，SCC 會擷取每一個項目的狀態。 然後它會比較所需條件的結果，並提供解決封鎖問題的指引。  
  
系統組態檢查會產生報告，其中包含每個已執行規則以及執行狀態的簡短描述。 系統組態檢查報告位於 %programfiles%\Microsoft SQL Server\140\Setup Bootstrap\Log\\\<YYYYMMDD_HHMM>\\\.    
  
如需詳細資訊，請參閱下列連結：

- [安裝 SQL Server 的硬體與軟體需求](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)   
- [SQL Server 安裝的安全性考量](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   
- [支援的版本與版本升級](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
  
