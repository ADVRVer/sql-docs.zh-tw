---
title: SMO 命名空間 |Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], namespaces
- namespaces [SMO]
- SQL Server Management Objects, namespaces
ms.assetid: 7bfabe4d-9f4c-4bc9-b998-93bd2b50ee8a
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5e606844d031bb4ab2c29d9dfd012c97601ca12f
ms.sourcegitcommit: b4962530f90234017073b3fdd2248936b2de4e69
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71077545"
---
# <a name="smo-object-model-namespaces"></a>SMO 物件模型命名空間
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理物件 (SMO) 具有多種命名空間。 不同的命名空間代表 SMO 內不同的功能區域。  
  
 在[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，SMO 元件位於 C:\Program Files\Microsoft SQL Server\130\SDK\Assemblies 資料夾中。  
  
## <a name="namespaces"></a>命名空間  
 SMO 命名空間有：  
  
|類別|函數|  
|-----------|--------------|  
|<xref:Microsoft.SqlServer.Management.Smo>|包含實例類別、公用程式類別和用來以程式設計方式操作[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的列舉。|  
|<xref:Microsoft.SqlServer.Management.Common>|包含 Replication Management Objects (RMO) 和 SMO 通用的類別，例如連接類別。|  
|<xref:Microsoft.SqlServer.Management.Smo.Agent>|包含表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的類別。|  
|<xref:Microsoft.SqlServer.Management.Smo.Wmi>|包含表示 WMI 提供者的類別。|  
|<xref:Microsoft.SqlServer.Management.Smo.RegisteredServers>|包含表示已註冊的伺服器的類別。|  
|<xref:Microsoft.SqlServer.Management.Smo.Mail>|包含表示 Database Mail 的類別。|  
|<xref:Microsoft.SqlServer.Management.Smo.Broker>|包含表示 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 的類別。|  
  
  
