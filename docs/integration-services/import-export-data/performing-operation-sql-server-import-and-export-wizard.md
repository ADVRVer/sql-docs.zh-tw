---
title: "執行作業 （SQL Server 匯入和匯出精靈） |Microsoft 文件"
ms.custom: 
ms.date: 01/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.performingoperation.f1
ms.assetid: 83259509-71d6-4a64-a7f2-4e9603b30bd4
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 75dc26699071ee88bb0c05368b4bf36ba677c35b
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="performing-operation-sql-server-import-and-export-wizard"></a>正在執行作業 (SQL Server 匯入和匯出精靈)
檢閱您在精靈中所做的選擇，並在 [完成精靈]  頁面上按一下 [完成]  之後，[ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈] 會顯示 [正在執行作業] 。 在此頁面上，您會看到在前幾頁設定之作業的進度和結果。 您不需要在此頁面上採取任何動作。

## <a name="screen-shot---operation-in-progress"></a>螢幕擷取畫面 - 作業進行中 
 下列螢幕擷取畫面顯示當作業仍在進行中時，精靈的 [正在執行作業]  頁面。  
  
 ![執行作業 頁面的匯入和匯出精靈](../../integration-services/import-export-data/media/performing-operation1.png "執行作業 頁面的匯入和匯出精靈")  

## <a name="screen-shot---operation-completed"></a>螢幕擷取畫面 - 作業已完成 
 下列螢幕擷取畫面顯示當作業完成之後，精靈的 [正在執行作業]  頁面。 按一下 [訊息]  資料行中的項目，取得關於對應步驟的詳細資訊。  
  
 ![執行作業 頁面的匯入和匯出精靈](../../integration-services/import-export-data/media/performing-operation2.png "執行作業 頁面的匯入和匯出精靈")  
  
## <a name="watch-the-progress-of-the-operation"></a>查看作業進度
 **動作**  
 顯示作業的每個步驟。  
  
 **狀態**  
 顯示每個步驟是成功或失敗。  
  
 **訊息**  
 顯示關於步驟的資訊及錯誤訊息。 按一下此資料行中的項目，取得對應步驟的詳細資訊。

## <a name="interrupt-the-operation-or-save-the-results"></a>中斷作業或儲存結果
 **停止**  
 如有必要，請按一下 [停止]  按鈕中斷作業。  
  
 **報表**  
 檢視結果的報表、將報表儲存至檔案、將報表複製到剪貼簿，或透過電子郵件傳送報表。  
  
## <a name="whats-next"></a>下一步  
 您所設定的作業執行並順利完成之後，您便已完成執行 [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈]。  
-   如果您立即執行作業，則可以開啟您選取的目的地，檢閱精靈複製的資料。  
-   如果您儲存了精靈所建立的 SSIS 封裝，您可以在 SQL Server 資料工具中開啟它，並加以自訂和重複使用。 如需如何自訂已儲存的封裝，並稍後再執行它的詳細資訊，請參閱 [儲存 SSIS 封裝](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md)。

## <a name="see-also"></a>另請參閱
[透過匯入和匯出精靈的簡單範例開始使用](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)



