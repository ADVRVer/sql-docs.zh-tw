---
title: SMO 物件模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], object model
- SQL Server Management Objects, object model
ms.assetid: bd6e59b6-ca46-42c0-adb2-c9d64cf6e00b
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 186343e4c9bc594593ff3efee40e6a09f68e5422
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86000304"
---
# <a name="smo-object-model"></a>SMO 物件模型
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  SMO 物件模型是由物件階層所組成。 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件是最上層的物件，而所有執行個體類別物件則位於 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件之下。  
  
 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 類別是包含個別物件階層的最上層類別。 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>物件代表 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可透過 WMI 提供者取得的服務和網路設定。  
  
 除了 <xref:Microsoft.SqlServer.Management.Smo.Server> 和 <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 物件之外，還有數個代表工作或或運算的數個公用程式類別，例如 <xref:Microsoft.SqlServer.Management.Smo.Transfer>、<xref:Microsoft.SqlServer.Management.Smo.Backup> 或 <xref:Microsoft.SqlServer.Management.Smo.Restore>  
  
 SMO 物件模型是由數個命名空間所組成。 如需詳細資訊，請參閱 [SMO 命名空間](../../relational-databases/server-management-objects-smo/smo-object-model-namespaces.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SMO 物件模型圖](../../relational-databases/server-management-objects-smo/smo-object-model-diagram.md)   
 [SMO 命名空間](../../relational-databases/server-management-objects-smo/smo-object-model-namespaces.md)   
 [組態管理的 WMI 提供者概念](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
