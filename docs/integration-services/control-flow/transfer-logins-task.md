---
title: "傳送登入工作 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.transferloginstask.f1
helpviewer_keywords:
- Transfer Logins task [Integration Services]
ms.assetid: 1df60fd6-c019-405d-8155-c330dbac2cc1
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 02215c15fbbbcb4f7fd5ee5638afa4e0092e86c9
ms.contentlocale: zh-tw
ms.lasthandoff: 08/03/2017

---
# <a name="transfer-logins-task"></a>傳送登入工作
  「傳送登入」工作會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體之間傳送一個或多個登入。  
  
## <a name="transfer-logins-between-instances-of-sql-server"></a>在 SQL Server 的執行個體之間傳送登入  
 傳送登入工作支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 來源和目的地。  
  
## <a name="events"></a>事件  
 「傳送登入」工作會引發報告已傳送登入數目的資訊事件，並在覆寫登入時引發警告事件。  
  
 該工作並不報告登入傳送的累加進度，它只報告 0% 和 100 % 完成。  
  
## <a name="execution-value"></a>執行值  
 工作之 **ExecutionValue** 屬性中定義的執行值會傳回已傳送的登入數目。 透過將使用者定義變數指派給「傳送登入」工作的 **ExecValueVariable** 屬性，可將與登入傳送相關的資訊用於封裝中的其他物件。 如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](../../integration-services/integration-services-ssis-variables.md)和[在封裝中使用變數](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)。  
  
## <a name="log-entries"></a>記錄項目  
 「傳送登入」工作包含下列自訂記錄項目：  
  
-   TransferLoginsTaskStarTransferringObjects   此記錄項目報告傳送已開始。 記錄項目會包含開始時間。  
  
-   TransferLoginsTaskFinishedTransferringObjects   此記錄項目報告傳送已完成。 記錄項目會包含結束時間。  
  
 此外， **OnInformation** 事件的記錄項目會報告已傳送的登入數目，並會為在目的地上覆寫的每個登入，寫入 **OnWarning** 事件的記錄項目。  
  
## <a name="security-and-permissions"></a>安全性和權限  
 若要瀏覽來源伺服器上的登入，並在目的地伺服器上建立登入，使用者必須同時是兩個伺服器上 sysadmin 伺服器角色的成員。  
  
## <a name="configuration-of-the-transfer-logins-task"></a>設定傳送登入工作  
 「傳送登入」工作可以設定為傳送所有登入、只傳送指定的登入，或只傳送具有指定之資料庫存取權的所有登入。 無法傳送 sa 登入。 可能已重新命名 SA 登入，不過，重新命名的 SA 登入仍然無法傳送。  
  
 您還可以指出工作是否複製與登入相關聯的安全性識別碼 (SID)。 如果將「傳送登入」工作與「傳送資料庫」工作一起使用，則必須將 SID 複製到目的地，否則，目的地資料庫將無法辨識傳送的登入。  
  
 在目的地上，會停用傳送的登入，並為其指派隨機密碼。 目的地伺服器上 sysadmin 角色的成員必須變更密碼，並啟用登入，才可以使用這些登入。  
  
 要傳送的登入可能已存在於目的地上。 可以設定「傳送登入」工作以下列方式處理現有的登入：  
  
-   覆寫現有的登入。  
  
-   存在重複的登入時讓工作失敗。  
  
-   略過重複的登入。  
  
 在執行階段，「傳送登入」工作會使用兩個 SMO 連接管理員，連接到來源和目的地伺服器。 SMO 連接管理員會在「傳送登入」工作以外另行設定，然後在「傳送登入」工作中參考。 存取伺服器時，SMO 連接管理員會指定要使用的伺服器和驗證模式。 如需詳細資訊，請參閱 [SMO Connection Manager](../../integration-services/connection-manager/smo-connection-manager.md)。  
  
 您可以透過「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」或以程式設計方式設定屬性。  
  
 如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：  
  
-   [傳送登入工作編輯器 &#40;一般頁面&#41;](../../integration-services/control-flow/transfer-logins-task-editor-general-page.md)  
  
-   [傳送登入工作編輯器 &#40;登入頁面&#41;](../../integration-services/control-flow/transfer-logins-task-editor-logins-page.md)  
  
-   [運算式頁面](../../integration-services/expressions/expressions-page.md)  
  
 如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：  
  
-   [設定工作或容器的屬性](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="programmatic-configuration-of-the-transfer-logins-task"></a>以程式設計方式設定傳送登入工作  
 如需有關以程式設計方式設定這些屬性的詳細資訊，請按下列主題：  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferLoginsTask.TransferLoginsTask>  
  
  
