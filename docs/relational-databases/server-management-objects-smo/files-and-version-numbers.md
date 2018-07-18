---
title: 檔案和版本號碼 |Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 10e11076ce023a3d969b4ba95a30c15de43eafa6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38046226"
---
# <a name="files-and-version-numbers"></a>檔案和版本號碼
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  所有必要的 SQL Server 管理物件 (SMO) 元件包含在 Microsoft.SqlServer.SqlManagementObjects NuGet 套件。 SMO 是實作於數個 Managed 組件中。 您可以在用戶端或伺服器上開發 SMO 應用程式。  

>>[!Important]
SMO 組件的檔案版本會顯示為主要。**0**。Build.Revision。 但內嵌組件的版本為主要。**100**。Build.Revision。 這是為了讓其中一個更新並不會影響任何其他人將 SMO 在每個應用程式中使用的版本是分開。
>>
>>因此您應該**不**安裝這些版本的組件至全域組件快取 (GAC) 中。 這樣可能會造成其他應用程式，例如[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Management Studio 中，若要中斷。 
  
|檔案|描述|  
|-----------|-----------------|  
|Microsoft.SqlServer.ConnectionInfo.dll|包含與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體進行連接的支援。|  
|Microsoft.SqlServer.ServiceBrokerEnum.dll|包含 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker 程式設計的支援。 只有在存取 Service Broker 的程式中才需要此檔案。|  
|Microsoft.SqlServer.Smo.dll|包含大部分的 SMO 類別。|  
|Microsoft.SqlServer.SmoExtended.dll<br /><br /> Microsoft.SqlServer.Management.Sdk.Sfc.dll<br /><br /> Microsoft.SqlServer.SqlEnum.dll|包含 SMO 類別的支援。|  
|Microsoft.SqlServer.WmiEnum.dll|包含 Windows Management Instrumentation (WMI) 提供者類別。 這只有在使用 WMI 提供者類別的程式中才需要此檔案。|  
|Microsoft.SqlServer.RegSvrEnum.dll|包含已註冊的伺服器的類別。 這只有在使用已註冊伺服器類別的程式中才需要此檔案。|  
  
  
