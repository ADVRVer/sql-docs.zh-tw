---
title: MSSQLSERVER_11001 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- "12001"
helpviewer_keywords:
- 11001 (Database Engine error)
ms.assetid: 53d4d63a-61e3-441f-bfe9-9d44f7a05fd4
caps.latest.revision: 10
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 070a44caa2738ec1cc475b2d7d26148b27063619
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver11001"></a>MSSQLSERVER_11001
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|11001|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱||  
|訊息文字|建立伺服器的連接時發生錯誤。  連接到 SQL Server 時，可能因為在預設的設定下 SQL Server 不允許遠端連接而引起此失敗。 (提供者：TCP 提供者，錯誤：0 - 無法識別這部主機。) (.Net SqlClient 資料提供者)|  
  
## <a name="explanation"></a>說明  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用戶端無法連接到伺服器。 發生這個錯誤的原因，可能是用戶端無法解析伺服器的名稱，或伺服器的名稱不正確。  
  
## <a name="user-action"></a>使用者動作  
確定在用戶端上輸入的伺服器名稱正確，並且可從用戶端解析伺服器的名稱。 若要檢查 TCP/IP 名稱解析，您可以使用 Windows 作業系統的 **ping** 命令。  
  
## <a name="see-also"></a>另請參閱  
[網路通訊協定和網路程式庫](~/sql-server/install/network-protocols-and-network-libraries.md)  
[用戶端網路組態](~/database-engine/configure-windows/client-network-configuration.md)  
[設定用戶端通訊協定](~/database-engine/configure-windows/configure-client-protocols.md)  
[啟用或停用伺服器網路通訊協定](~/database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  

