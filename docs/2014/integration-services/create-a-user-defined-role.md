---
title: 建立使用者定義的角色 |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4128993-2333-48c7-84b1-e51cdcea393d
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b8405be955cdfd4f0d8b9665665f8817c98b9d60
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144973"
---
# <a name="create-a-user-defined-role"></a>建立使用者定義角色
    
### <a name="to-create-a-user-defined-role"></a>建立使用者定義角色  
  
1.  開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]  
  
2.  在 **[檢視]** 功能表上，按一下 **[物件總管]** 。  
  
3.  在 [物件總管] 工具列上，按一下 **[連接]**，再按一下 **[Database Engine]**。  
  
4.  在 [連接到伺服器] 對話方塊中，提供伺服器名稱並選取驗證模式。 您可以使用句號 （.）、 (local)，或`localhost`表示本機伺服器。  
  
5.  按一下 **[連接]**。  
  
6.  展開 [資料庫]、[系統資料庫]、[msdb]、[安全性] 和 [角色]。  
  
7.  在 [角色] 節點中，以滑鼠右鍵按一下 [資料庫角色]，並按一下 [新增資料庫角色]。  
  
8.  在 [一般] 頁面上提供名稱，選擇性地指定擁有者和擁有的結構描述，並加入角色成員。  
  
9. 選擇性地按一下 [權限]，並設定物件權限。  
  
10. 選擇性地按一下 [擴充屬性]，並設定任何擴充屬性。  
  
11. 按一下 [確定] 。  
  
  