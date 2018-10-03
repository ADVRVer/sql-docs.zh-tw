---
title: 存取 WMI 提供者使用 WQL 的組態管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
ms.assetid: 26499530-d93b-452b-bbe4-217ef1d11e68
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 0b19bf27cdc94e70908f81523a092ba022c41601
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48157678"
---
# <a name="access-wmi-provider-for-configuration-management-using-wql"></a>使用 WQL 存取組態管理的 WMI 提供者
  本節描述如何針對電腦管理的 WMI 提供者執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Management Instrumentation 查詢語言 (WQL) 陳述式。  
  
 此範例使用 WQL 編輯器 WBEMtest.exe 來針對 WMI 提供者執行 WQL 查詢，以列舉 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務、網路通訊協定和別名。  
  
### <a name="querying-services-using-wbemtest"></a>使用 WBEMtest 查詢服務  
  
1.  從**開始**功能表上，按一下**執行**，然後輸入`WBEMtest`。  
  
2.  [WBEMtest.exe] 對話方塊隨即出現。 按一下 **[連接]**。  
  
3.  在第一個文字欄位中，輸入電腦管理的 WMI 提供者命名空間：root\Microsoft\SqlServer\ComputerManagement11。 按一下 **[連接]**。  
  
4.  按一下 **查詢**。 輸入查詢，以傳回本機電腦上執行的目前服務：**選取\*從 SqlService。** 按一下 **[套用]**。  
  
5.  加入 `WHERE ServiceName = "MSSQLSERVER"` 來進一步精簡查詢。  
  
  
