---
title: 執行封裝對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.ssms.ispackageexecute.f1
- sql12.ssis.ssms.executepackage.f1
ms.assetid: 4f7a806d-4867-4d1f-bc65-b00c1caee7b6
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c2d9b2edb2c61982c954a4f84494ba8e10bbf2fa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36136463"
---
# <a name="execute-package-dialog-box"></a>Execute Package Dialog Box
  使用 **[執行封裝]** 對話方塊，即可執行儲存在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器上的封裝。  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝可能會包含參考儲存在環境變數中之值的參數。 在執行這種封裝前，您必須指定要使用何種環境來提供環境變數值。 專案可能包含多個環境，但是執行期間只能使用一個環境來繫結環境變數值。 如果封裝中沒有使用環境變數，就不需要環境。  
  
 您想要做什麼事？  
  
-   [開啟 [執行封裝] 對話方塊](#open_dialog)  
  
-   [設定 [一般] 頁面上的 [選項]](#general)  
  
-   [設定 [參數] 索引標籤上的 [選項]](#parameters)  
  
-   [設定[連接管理員] 索引標籤上的 [選項]](#connection)  
  
-   [設定 [進階] 索引標籤上的 [選項]](#advanced)  
  
-   [編寫執行封裝對話方塊中之選項的指令碼](#script)  
  
##  <a name="open_dialog"></a> 開啟 [執行封裝] 對話方塊  
  
1.  在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中，連接至 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器。  
  
     您正在連接到主控 SSISDB 資料庫之 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 的執行個體。  
  
2.  在 [物件總管] 中，展開樹狀目錄以顯示 **[Integration Services 目錄]** 節點。  
  
3.  展開 **[SSISDB]** 節點。  
  
4.  展開包含您要執行之封裝的資料夾。  
  
5.  以滑鼠右鍵按一下封裝，然後按一下 [執行]。  
  
##  <a name="general"></a> 設定 [一般] 頁面上的 [選項]  
 選取 **[環境]** 來指定適用於執行執行封裝的環境。  
  
##  <a name="parameters"></a> 設定 [參數] 索引標籤上的 [選項]  
 使用 **[參數]** 索引標籤來修改封裝執行時所使用的參數值。  
  
##  <a name="connection"></a> 設定[連接管理員] 索引標籤上的 [選項]  
 使用 [連接管理員] 索引標籤設定封裝連接管理員的屬性。  
  
##  <a name="advanced"></a> 設定 [進階] 索引標籤上的 [選項]  
 使用 [進階] 索引標籤管理屬性和其他封裝設定。  
  
 [加入]、[編輯]、[移除]  
 按一下可加入、編輯或移除屬性。  
  
 **記錄層級**  
 選取用於執行封裝的記錄層級。 如需詳細資訊，請參閱 [catalog.set_execution_parameter_value &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)。  
  
 **在發生錯誤時傾印**  
 指定在封裝執行期間發生錯誤時是否建立傾印檔。 如需相關資訊，請參閱 [產生封裝執行的傾印檔案](troubleshooting/generating-dump-files-for-package-execution.md)。  
  
 **32 位元執行階段**  
 指定封裝將會在 32 位元系統上執行。  
  
##  <a name="script"></a> 編寫執行封裝對話方塊中之選項的指令碼  
 當您位於 **[執行封裝]** 對話方塊時，也可以使用工具列上的 **[指令碼]** 按鈕來為您撰寫 [!INCLUDE[tsql](../includes/tsql-md.md)] 程式碼。 產生的指令碼會使用您在 [執行封裝] 對話方塊中已選取的相同選項來呼叫預存程序 [catalog.start_execution &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)。 指令碼會出現在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]的新指令碼視窗中。  
  
  
