---
title: SQL Server 連線所需的 CDC 服務權限 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d9e968f9-180c-4fa0-a849-98f2b1942330
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c766ff574855f4ec3ffe6828fc6ca36b775d3d95
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47599416"
---
# <a name="sql-server-connection-required-permissions-for-the-cdc-service"></a>SQL Server 連接所需的 CDC 服務權限
  CDC 服務組態主控台需要與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之間的連接資訊，才能執行其工作。 本主題描述可以在 [連接到 SQL Server] 對話方塊中提供的資訊，以便設定與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的連接。  
  
 必要時會開啟 [連接到 SQL Server] 對話方塊，例如當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連接資訊無法取得時，或是當資訊存在但是連接沒有必要的權限時。  
  
 下表描述需要連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的各種工作以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入/使用者的必要權限。  
  
|工作|最小權限|  
|----------|-------------------------|  
|準備 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。|`dbcreator` 固定伺服器角色|  
|建立 Oracle CDC 服務 SQL Server 登入，以供 Oracle CDC 服務使用。|`public` 固定伺服器角色|  
|建立 Oracle CDC 服務登入，以供在 MSXDBCDC 中註冊新服務使用。|`db_datareader` 和 `db_datawriter` 角色|  
|編輯 Oracle CDC 服務登入，以供在 MSXDBCDC 中更新服務註冊使用。|`db_datareader` 和 `db_datawriter` 角色|  
|刪除 Oracle CDC 服務登入，以供在 MSXDBCDC 中更新服務註冊使用。|`db_datareader` 和 `db_datawriter` 角色|  
  
## <a name="see-also"></a>另請參閱  
 [連接到 SQL Server](../../integration-services/change-data-capture/connection-to-sql-server.md)   
 [連接到 SQL Server 以進行刪除作業](../../integration-services/change-data-capture/connection-to-sql-server-for-delete.md)  
  
  
