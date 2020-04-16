---
title: 建立模型
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], creating models
- creating models [Master Data Services]
ms.assetid: 9bb3b3b3-bde8-44aa-ad62-eaae21188141
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 730e18fca866891d62b68d321ec13e4be5da59bf
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "73728479"
---
# <a name="create-a-model-master-data-services"></a>建立模型 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，建立模型以包含模型物件。  
  
## <a name="prerequisites"></a>Prerequisites  
 若要執行此程序：  
  
-   您必須擁有存取 **[系統管理]** 功能區域的權限。  
  
-   您必須是模型管理員。 有關詳細資訊,請參閱[管理員&#40;主資料服務&#41;](../master-data-services/administrators-master-data-services.md)。  
  
### <a name="to-create-a-model"></a>若要建立模型  
  
1.  在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。  
  
2.  在 **[模型檢視]** 頁面上，從功能表列指向 **[管理]** ，然後按一下 **[模型]**。  
  
3.  在 [管理模型]**** 頁面上，按一下 [加入]****。 隨即會在右側顯示面板。  
  
4.  在 [名稱]**** 方塊中，輸入模型的名稱。  
  
5.  (選擇性) 在 [描述]**** 欄位中，輸入模型描述。  
  
6.  在 [Log Retention Days] (記錄保留天數) **** 欄位中，選取其中一個選項來保留記錄資料。 預設值為 [系統設定] ****，表示會從 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]中的系統設定繼承值。 如需詳細資訊，請參閱 [系統設定 &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md)。  
  
     若要覆寫系統設定而不移除交易記錄資料，請選取 [否] ****。 要僅保留今天的日誌資料並截留所有前幾天的日誌資料,請選擇 **「是**」並將 **「天」** 欄位設定為 0。 若要保留指定天數的記錄資料，請選取 [是] **** ，然後將 [天數] **** 欄位設為該天數。  
  
7.  (選擇性) 選取 [建立與模型同名的實體]****，建立與模型同名的實體。  
  
8.  按一下 **[儲存模型]**。  
  
 對於每個建立的模型，會將含有八個資料行的資料列加入方格中。 八個資料行如下：  
  
-   **狀態**︰模型狀態。 按下「**保存模型」** 按鈕時,將顯示![「更新](../master-data-services/media/mds-model-status-updating.png "Updating")」圖像,表示模型正在更新。 如果建立或編輯模型時出現錯誤,將顯示![「錯誤」](../master-data-services/media/mds-model-status-error.png "錯誤")影像。 否則,狀態為"確定![",並顯示"確定"](../master-data-services/media/mds-model-status-ok.png "[確定]")圖像。  
  
-   **名稱**：模型名稱。  
  
-   **描述**：模型描述。  
  
-   **記錄保留天數**：模型記錄保留天數。  
  
-   **建立者**：建立模型之使用者的使用者名稱。  
  
-   **建立日期和時間**：模型的建立日期和時間。  
  
-   **更新者**：上次更新模型之使用者的使用者名稱。  
  
-   **更新日期和時間**：取得上次更新模型的日期和時間。  
  
## <a name="next-steps"></a>後續步驟  
  
-   [建立實體 &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)  
  
## <a name="see-also"></a>另請參閱  
 [&#40;主数据服务&#41;](../master-data-services/models-master-data-services.md)   
 [實體&#40;主資料服務&#41;](../master-data-services/entities-master-data-services.md)   
 [刪除主資料服務&#40;模型&#41;](../master-data-services/delete-a-model-master-data-services.md)   
 [編輯模型&#40;主資料服務&#41;](../master-data-services/edit-model-master-data-services.md)   
 [交易 &#40;Master Data Services&#41;](../master-data-services/transactions-master-data-services.md)  
  
  
