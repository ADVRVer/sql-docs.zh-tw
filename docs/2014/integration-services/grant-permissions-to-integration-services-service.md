---
title: 權限授與 Integration Services 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c2caa68-7834-4ea0-bd77-4f3a7c86d634
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 32b8ee36951ec828340de5c6d581f0b8d8bc919a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36132913"
---
# <a name="grant-permissions-to-integration-services-service"></a>授予 Integration Services 服務的權限
  在舊版 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]中，當您安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 時，Users 群組中的所有使用者預設都能存取 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務。 當您安裝目前版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]時，使用者無法存取 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務。 因此，服務預設是安全的。 安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 之後，管理員必須授與該服務的存取權。  
  
### <a name="to-grant-access-to-the-integration-services-service"></a>授與 Integration Services 服務的存取權  
  
1.  執行 Dcomcnfg.exe。 Dcomcnfg.exe 提供使用者介面，可供修改登錄中的某些設定。  
  
2.  在 [元件服務] 對話方塊中，展開 [元件服務] > [電腦] > [我的電腦] > [DCOM 組態] 節點。  
  
3.  以滑鼠右鍵按一下**Microsoft SQL Server Integration Services 12.0**，然後按一下 **屬性**。  
  
4.  在 **[安全性]** 索引標籤上，按一下 **[啟動和啟用權限]** 區域中的 **[編輯]** 。  
  
5.  加入使用者並指派適當的權限，然後按一下 [確定]。  
  
6.  重複步驟 4 - 5，以設定存取權限。  
  
7.  啟動 SQL Server Management Studio。  
  
8.  重新啟動 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務。  
  
  