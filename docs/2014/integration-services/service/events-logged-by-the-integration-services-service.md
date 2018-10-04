---
title: Integration Services 服務所記錄的事件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- service [Integration Services], events
- events [Integration Services], service
- Integration Services service, events
ms.assetid: d4122dcf-f16f-47a0-93a2-ffa3d0d4f9cf
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 52cb18c5828a2d72ef8a36082554425e7e3afb82
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48187088"
---
# <a name="events-logged-by-the-integration-services-service"></a>Integration Services 服務所記錄的事件
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服務會將各種訊息記錄至 Windows 應用程式事件記錄檔。 當服務啟動、停止以及發生特定問題時，此服務就會記錄這些訊息。  
  
 本主題會提供服務記錄至應用程式事件記錄檔之常見事件訊息的相關資訊。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服務會記錄這個主題所描述而且事件來源為 SQLISService 的所有訊息。  
  
 如需 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服務的詳細資訊，請參閱 [Integration Services 服務 &#40;SSIS 服務&#41;](integration-services-service-ssis-service.md)。  
  
## <a name="messages-about-the-status-of-the-service"></a>服務狀態的相關訊息  
 當您選取 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 進行安裝時，系統就會安裝並啟動 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服務，而且它的啟動類型會設定為自動。  
  
|事件識別碼|符號名稱|文字|注意|  
|--------------|-------------------|----------|-----------|  
|256|DTS_MSG_SERVER_STARTING|正在啟動 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] 服務。|服務即將啟動。|  
|257|DTS_MSG_SERVER_STARTED|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] 服務已啟動。|服務已啟動。|  
|260|DTS_MSG_SERVER_START_FAILED|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] 服務無法啟動。%n錯誤: %1|服務無法啟動。 無法啟動的原因可能是安裝已損毀或服務帳戶不正確。|  
|258|DTS_MSG_SERVER_STOPPING|正在停止 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] 服務。%n%n結束時停止所有執行中的封裝: %1|服務正在停止，而且如果您將此服務設定為這樣做，就會停止所有執行中的封裝。 您可以在組態檔中設定 True 或 False 值，以便決定在此服務本身停止時，是否會停止執行中封裝。 這個事件的訊息包括這項設定的值。|  
|259|DTS_MSG_SERVER_STOPPED|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] 服務已停止。%n伺服器版本 %1|服務已停止。|  
  
## <a name="messages-about-the-configuration-file"></a>組態檔的相關訊息  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 服務的設定會儲存在您可以修改的 XML 檔案中。 如需詳細資訊，請參閱[設定 Integration Services 服務 &#40;SSIS 服務&#41;](../configuring-the-integration-services-service-ssis-service.md)。  
  
|事件識別碼|符號名稱|文字|注意|  
|--------------|-------------------|----------|-----------|  
|274|DTS_MSG_SERVER_MISSING_CONFIG_REG|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] 服務: %n指定組態檔的登錄設定不存在。 %n嘗試載入預設組態檔。|包含組態檔路徑的登錄項目不存在或是空的。|  
|272|DTS_MSG_SERVER_MISSING_CONFIG|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] 服務組態檔不存在。%n載入預設值。|組態檔本身不存在指定的位置中。|  
|273|DTS_MSG_SERVER_BAD_CONFIG|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] 服務組態檔不正確。%n讀取組態檔時發生錯誤: %1%n%n以預設值來載入伺服器。|組態檔無法讀取或無效。 這個錯誤可能是由於檔案中的 XML 語法錯誤所造成。|  
  
## <a name="other-messages"></a>其他訊息  
  
|事件識別碼|符號名稱|文字|注意|  
|--------------|-------------------|----------|-----------|  
|336|DTS_MSG_SERVER_STOPPING_PACKAGE|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] 服務: 停止執行中的封裝。%n封裝執行個體識別碼: %1%n封裝識別碼: %2%n封裝名稱: %3%n封裝描述: %4%n封裝|服務正嘗試停止執行中的封裝。 您可以在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中監視並停止執行中的封裝。 如需如何在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中管理封裝的資訊，請參閱[封裝管理 &#40;SSIS 服務&#41;](package-management-ssis-service.md)。|  
  
## <a name="related-tasks"></a>相關工作  
 如需如何檢視記錄項目的資訊，請參閱 [檢視記錄事件視窗中的記錄項目](../view-log-entries-in-the-log-events-window.md)  
  
## <a name="see-also"></a>另請參閱  
 [Integration Services 套件所記錄的事件](../performance/events-logged-by-an-integration-services-package.md)  
  
  
