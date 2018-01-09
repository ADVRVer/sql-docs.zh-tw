---
title: "使用 WQL 與指令碼語言的 WMI 提供者 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f86bfa3cb0c8adaf178641bbeadf2c74c48bc65d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider"></a>使用 WQL 與指令碼語言的 WMI 提供者
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]管理應用程式存取[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]服務和組態管理物件，有兩種使用 Windows Management Instrumentation (WMI) 提供者的網路設定：  
  
-   使用 WQL 編輯器或查詢工具 (例如，WBEMTest.exe) 來查訊利用 Windows Management Instrumentation 語言 (WQL) 設定的物件。  
  
-   使用指令碼語言，例如 VBScript。  
  
 或者，可以使用 SMO 中的 WMI Managed 物件，以程式設計方式管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務與網路設定。 如需程式設計 WMI managed 物件，請參閱[管理服務和網路設定，使用 WMI 提供者所](../../relational-databases/server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md)。  
  
 組態管理的 WMI 提供者可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console 來進行存取。 如需從使用者介面存取 WMI 提供者的詳細資訊，請參閱[管理服務的如何主題 &#40;SQL Server 組態管理員 &#41;](http://msdn.microsoft.com/library/78dee169-df0c-4c95-9af7-bf033bc9fdc6).  
  
## <a name="see-also"></a>請參閱  
 [存取 WMI 提供者使用 WQL 的組態管理](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-wql.md)   
 [修改 SQL Server 服務進階屬性使用 VBScript](../../relational-databases/wmi-provider-configuration/access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  
