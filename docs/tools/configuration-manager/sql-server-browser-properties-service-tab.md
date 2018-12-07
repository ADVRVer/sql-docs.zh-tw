---
title: SQL Server Browser 屬性 (服務索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 98ace9b0-72d5-4b72-9b7b-11fbc490981a
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 77286e4bb4ed04a61e6949c4834e242bfac4be66
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2018
ms.locfileid: "52534653"
---
# <a name="sql-server-browser-properties-service-tab"></a>SQL Server Browser 屬性 (服務索引標籤)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 程式會以伺服器服務的方式執行。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 會接聽 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源的內送要求，並提供有關電腦上所安裝之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的資訊。  
  
 您可以使用 **[SQL Server Browser 內容]** 對話方塊上的 **[服務]** 索引標籤來檢視下列選項。 除了 [啟動模式] 之外的所有屬性都是唯讀的。  
  
## <a name="options"></a>選項。  
 **二進位路徑**  
 顯示這個服務使用之程式檔案的位置。  
  
 **錯誤控制**  
 1 表示 `SERVICE_ERROR_NORMAL`。 如果在電腦啟動過程中，服務無法啟動，啟動程式就會記錄錯誤並顯示快顯訊息方塊，但是仍會繼續啟動作業。 這項值不能被改變。  
  
 **結束碼**  
 發生錯誤時，錯誤號碼會在這個方塊中顯示。 請使用這個號碼進行疑難排解，方法是在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知識庫中搜尋該號碼，或者將號碼提供給技術支援人員。  
  
 **Host Name**  
 顯示執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務之電腦或叢集的名稱。  
  
 **名稱**  
 表示服務的顯示名稱。  
  
 **處理序識別碼**  
 顯示 Windows 處理序識別碼。  
  
 **服務類型**  
 顯示為呼叫處理序所提供的服務類型。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會安裝數個服務。  
  
 **啟動模式**  
 將這個服務設定為下列選擇：  
  
-   手動：電腦啟動時，這項服務不會自動啟動。 您必須使用「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」或其他工具來啟動服務。  
  
-   自動：這部電腦啟動時，這項服務會嘗試啟動。  
  
-   停用：這項服務無法啟動。  
  
 **State**  
 表示這項服務為執行中、已停止或已停用。 "**...**" 表示狀態變更已暫止。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Browser 服務](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
