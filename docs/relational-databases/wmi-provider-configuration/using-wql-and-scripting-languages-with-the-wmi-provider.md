---
title: 使用 WQL 與指令碼語言的 WMI 提供者 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- scripts [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
- WMI Provider for Configuration Management, scripts
ms.assetid: c1e64905-3c2b-4974-88f4-abf17cf7e289
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 1e1090e1dcc94b37f4427b76199adcb14173acb6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47722266"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider"></a>搭配 WMI 提供者使用 WQL 與指令碼語言
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  管理應用程式會以兩種方式，使用組態管理物件的 Windows Management Instrumentation (WMI) 提供者，存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務與網路設定：  
  
-   使用 WQL 編輯器或查詢工具 (例如，WBEMTest.exe) 來查訊利用 Windows Management Instrumentation 語言 (WQL) 設定的物件。  
  
-   使用指令碼語言，例如 VBScript。  
  
 或者，可以使用 SMO 中的 WMI Managed 物件，以程式設計方式管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務與網路設定。 如需程式設計 WMI managed 物件，請參閱 <<c0> [ 管理的服務和網路設定，使用 WMI 提供者所](../../relational-databases/server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md)。  
  
 組態管理的 WMI 提供者可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console 來進行存取。 如需有關從使用者介面存取 WMI 提供者的詳細資訊，請參閱 <<c0> [ 管理服務的如何主題&#40;SQL Server 組態管理員&#41;](http://msdn.microsoft.com/library/78dee169-df0c-4c95-9af7-bf033bc9fdc6)。</c0>  
  
## <a name="see-also"></a>另請參閱  
 [存取 WMI 提供者使用 WQL 的組態管理](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-wql.md)   
 [使用 VBScript 修改 SQL Server 服務進階屬性](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  
