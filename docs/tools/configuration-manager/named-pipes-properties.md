---
title: "具名管道內容 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [SQL Server]
- listening [SQL Server], pipes
- pipes [SQL Server], listening on pipes
- Named Pipes [SQL Server], listening on pipes
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
caps.latest.revision: "32"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 72fecdede46024eae399d9a762b0f8cdf7bb3a6b
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="named-pipes-properties"></a>具名管道屬性
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]使用**通訊協定**頁面**Named Pipes 內容**對話方塊來檢視或變更具名管道[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接聽的目標，當使用具名管道通訊協定。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]必須重新啟動才能啟用或停用通訊協定，或變更具名的管道。  
  
## <a name="options"></a>選項。  
 **已啟用**  
 可能的值為 [是] 和 [否]。  
  
 **管道名稱**  
 指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 接聽的具名管道。 根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 對於預設執行個體會接聽： `\\.\pipe\sql\query` ，而對於具名執行個體會接聽： `\\.\pipe\MSSQL$<instancename>\sql\query` 。 此欄位最長不可超過 2047 個字元。  
  
## <a name="creating-an-alternate-named-pipe"></a>建立替代具名管道  
 若要變更具名管道，請在 [具名管道] 方塊中輸入新的管道名稱，然後停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，之後再重新啟動。 因為已知 **sql\query** 是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用的具名管道，所以變更管道有助於降低遭惡意程式攻擊的風險。  
  
### <a name="example"></a>範例  
 輸入 **\\\\.\pipe\unit\app** 以接聽 **unit\app** 管道。  
  
 輸入 **\\\\.\pipe\acct** 以接聽 **acct** 管道。  
  
## <a name="see-also"></a>另請參閱  
 [啟用或停用伺服器網路通訊協定](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [選擇網路通訊協定](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [建立有效的連接字串使用具名的管道](http://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)  
  
  
