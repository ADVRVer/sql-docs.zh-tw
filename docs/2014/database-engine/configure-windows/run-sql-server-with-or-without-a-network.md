---
title: 使用或不使用網路執行 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- verifying Server service has been started
- net start [SQL Server]
- command prompt [SQL Server], connections
- SQL Server services, networks
- status information [SQL Server], Server service
- running SQL Server
- networking [SQL Server], SQL Server with or without
- services [SQL Server], networks
- starting Server service
- SQL Server, running
ms.assetid: 54eac961-5c7a-4481-982d-f93a64b5c2f4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 050986f4c78fc285e936b206c82faef90b89d75e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "62810356"
---
# <a name="run-sql-server-with-or-without-a-network"></a>使用 (或不使用) 網路執行 SQL Server
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可在網路上執行，也可在不使用網路的情況下執行。  
  
## <a name="running-sql-server-on-a-network"></a>在網路上執行 SQL Server  
 若要讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 能夠透過網路通訊，就必須執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。 根據預設， [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 會自行啟動內建的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。 若要查看是否已啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務，可在命令提示字元中輸入：  
  
 **net start**  
  
 若與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 相關的服務已啟動，則會在 **net start** 輸出中出現下列服務：  
  
-   Analysis Services (MSSQLSERVER)  
  
-   SQL Server (MSSQLSERVER)  
  
-   SQL Server Agent (MSSQLSERVER)  
  
## <a name="running-sql-server-without-a-network"></a>不使用網路執行 SQL Server  
 在不使用網路的情況下執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體時，就不需要內建的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。 即使未使用網路， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、SQL Server 組態管理員以及 **net start** 和 **net stop** 命令仍可作用，因此啟動及停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的程序，與在網路作業或獨立作業中的程序相同。  
  
 從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sqlcmd **之類的本機用戶端連接獨立的**執行個體時，您可以不使用網路，而使用本機管道直接連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。 本機管道與網路管道的差別在於是否使用網路。 除非另外指向，否則本機與網路管道都會使用標準管道 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .\pipe\sql\query) 建立與\\\\執行個體的連接。  
  
 當您未指定伺服器名稱而連接到本機 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時，就會使用本機管道。 當您連接到本機 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，並明確指定伺服器名稱時，使用的是網路管道或別的網路跨處理序通訊 (IPC) 機制，如 Internetwork Packet Exchange (IPX) /Sequenced Packet Exchange (SPX) (假設您已將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設成可使用多個網路)。 由於獨立的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不支援網路管道，因此從用戶端連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時，必須省略不必要的 **/** <伺服器名稱>  引數。 例如，若要從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] osql **連接到獨立**執行個體，請輸入：  
  
 **osql /Usa /P** \<sa 密碼>   
  
  
