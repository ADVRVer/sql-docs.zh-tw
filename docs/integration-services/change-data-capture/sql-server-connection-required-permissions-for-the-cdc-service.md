---
title: "CDC 服務 SQL Server 連接所需的權限 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9e968f9-180c-4fa0-a849-98f2b1942330
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 406cb1233d871603a38dc2d904d7ecd894b5f0cd
ms.contentlocale: zh-tw
ms.lasthandoff: 09/28/2017

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
 [連接到 SQL Server 進行刪除](../../integration-services/change-data-capture/connection-to-sql-server-for-delete.md)  
  
  

