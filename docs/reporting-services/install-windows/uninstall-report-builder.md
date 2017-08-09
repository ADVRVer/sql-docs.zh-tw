---
title: "解除安裝報表產生器 |Microsoft 文件"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 009538c6-4941-4393-b14b-9144cffdbdaf
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: ebfb5781c80cac35936dfdb9ad2e434ee5ca7f9e
ms.contentlocale: zh-tw
ms.lasthandoff: 08/09/2017

---

# <a name="uninstall-report-builder"></a>將報表產生器解除安裝

您可以從控制台或命令列解除安裝單機版本的報表產生器。

從命令列解除安裝報表產生器所用的語法與用來安裝報表產生器的語法完全相同，不過您會使用 /x 選項來取代 /i 選項。 解除安裝的命令列也可以包含 /quiet 選項和其他標準選項。 如果已經移除了報表產生器的 Windows Installer 套件 (ReportBuilder3_x86.msi)，您就無法輕鬆地使用命令列來解除安裝報表產生器。 若要深入了解如何使用 GUID 移除報表產生器，請參閱 [Command-Line Options](https://msdn.microsoft.com/library/windows/desktop/aa367988.aspx)(命令列選項)。  

如果報表產生器使用的資料夾包含自訂檔案，移除報表產生器時便會保留這些資料夾和檔案。 系統只會移除報表產生器的檔案。  

### <a name="to-uninstall-report-builder-from-the-control-panel"></a>若要從控制台解除安裝報表產生器

1.  在 **[開始]** 功能表上，按一下 **[控制台]**。  
  
2.  在 [控制台] 中，按一下 **[程式和功能]**。  
  
3.  找出[!INCLUDE[msCoName](../../includes/msconame-md.md)]SQL Server 2016 報表產生器中**名稱**清單，然後按一下它。  
  
4.  按一下 **[解除安裝]**。  
  
5.  如果出現確認解除安裝報表產生器的提示，請按一下 **[是]**。  
  
### <a name="to-uninstall-report-builder-from-the-command-line"></a>若要從命令列解除安裝報表產生器  
  
1.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
2.  在 [開啟]  文字方塊中，輸入 **cmd.**  
  
3.  在 [命令提示字元] 視窗中，導覽至包含 ReportBuilder3_x86.msi 的資料夾。  
  
4.  輸入如下的基本命令列：  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v install.log`  
  
 如果可以包含記錄功能，請使用如下所示的命令列：  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v c:\junk\install.log`  
  
5.  按 **Enter**鍵。  

## <a name="next-steps"></a>後續的步驟

[安裝報表產生器](../../reporting-services/install-windows/install-report-builder.md)  

更多問題嗎？ [請嘗試詢問 Reporting Services 論壇](http://go.microsoft.com/fwlink/?LinkId=620231)
