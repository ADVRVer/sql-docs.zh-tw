---
title: 瀏覽所有主體對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.ssms.browseprincipals.f1
ms.assetid: f11d2c5e-ee05-45f3-8dc2-0feb99b2f76f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 06f636c920ed86313a6e8954af9151fa401e8bf7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788806"
---
# <a name="browse-all-principals-dialog-box"></a>瀏覽所有主體對話方塊
  使用 **[瀏覽所有主體]** 對話方塊選取資料庫主體，以變更主體愛所選專案上的權限，或所選資料夾中包含之所有專案上的權限。  
  
 **您想要做什麼事？**  
  
-   [開啟 [瀏覽所有主體] 對話方塊](#open_dialog)  
  
-   [設定選項](#options)  
  
##  <a name="open_dialog"></a> 開啟 [瀏覽所有主體] 對話方塊  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器。  
  
     您正在連接到主控 SSISDB 目錄之 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體。  
  
2.  在 [物件總管] 中，展開樹狀目錄以顯示 **[Integration Services 目錄]** 節點。  
  
3.  展開 **[SSISDB]** 節點。  
  
4.  若要變更主體在所選資料中包含之所有專案上的權限，以滑鼠右鍵按一下資料夾，然後按一下 [屬性]。  
  
     若要變更主體在所選專案上的權限，展開包含專案的資料夾，以滑鼠右鍵按一下該專案，然後按一下 [屬性]。  
  
5.  選取 **[權限]** 頁面，然後按一下 **[瀏覽]**。  
  
##  <a name="options"></a> 設定選項  
 這個頁面會顯示來自 SSISDB 資料庫之目錄檢視 sys.database_principals 的主體。  
  
 若選取主體，在您按一下 **[確定]** 並關閉 **[瀏覽所有主體]** 對話方塊時，它們就會加入至父對話方塊中 **[權限]** 頁面上的 **[登入或角色]** 清單。 將主體加入至 **[登入或角色]** 清單後，您可以變更它們在所選專案上的權限。  
  
 **選取資料行**  
 選取此選項即可將主體加入至父對話方塊中 [權限] 頁面上的 [登入或角色] 清單。  
  
 **圖示資料行**  
 與主體之 [類型] 對應的圖示。  
  
 **名稱**  
 主體的名稱。  
  
 **型別**  
 主體的類型。 常見的類型如下：  
  
-   SQL 使用者  
  
-   Windows 使用者  
  
-   資料庫角色  
  
  
