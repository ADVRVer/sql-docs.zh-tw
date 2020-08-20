---
description: 建立索引 (Master Data Services)
title: 建立索引
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: d694a105-69b1-4ff6-99d3-1f408b916b81
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 48d78cffb116996848035e3675e707994226f080
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461820"
---
# <a name="create-an-index-master-data-services"></a>建立索引 (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  在您經常查詢的屬性清單上建立自訂索引，以提升查詢效能。  
  
## <a name="prerequisites"></a>先決條件  
 若要執行此程序：  
  
-   您必須擁有存取系統管理功能區域的權限。 如需詳細資訊，請參閱[功能區域權限 &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md)。  
  
-   您必須是模型管理員。 如需詳細資訊，請參閱系統 [管理員 &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)。  
  
 **建立索引**  
  
1.  在主資料管理員中，按一下 [系統管理] ****。  
  
2.  在 [管理模型]**** 頁面上，從方格中選取模型，然後按一下 [實體]****。  
  
3.  在 [管理實體]**** 頁面上，從 [方格]**** 中選取含有您想要為其建立索引之實體的資料列。  
  
4.  按一下 [索引]****。  
  
5.  在 [名稱]**** 方塊中，輸入此索引的名稱。  
  
6.  若您想要建立唯一索引，請選取 [是唯一的]****。 如需索引類型的詳細資訊，請參閱 [自訂索引 &#40;Master Data Services&#41;](../master-data-services/custom-index-master-data-services.md)。  
  
7.  按一下 [可用屬性]**** 方塊中的屬性，然後按一下 [加入]**** 箭號。 若要加入所有屬性，請按一下 [全部加入]**** 箭號。  
  
8.  按一下 [檔案] 。  
  
 對於每個建立的索引，含有四個資料行的資料列會加入格線中。 下表描述該資料行。  
  
|資料行名稱|描述|  
|-----------------|-----------------|  
|狀態|索引狀態。<br /><br /> 當您按一下 [ **儲存**] 時，會顯示 ![更新狀態](../master-data-services/media/mds-statusicon-updating.png "更新狀態的圖示") 影像的圖示，指出正在更新索引。<br /><br /> 如果建立或編輯索引時發生錯誤，則會顯示 ![錯誤狀態](../master-data-services/media/mds-statusicon-error.png "錯誤狀態圖示") 影像的圖示。<br /><br /> 否則，狀態會是 [確定]，而且會顯示 [ ![確定] 狀態](../master-data-services/media/mds-statusicon-ok.png "[確定] 狀態的圖示") 影像的圖示。|  
|名稱|索引名稱。|  
|是唯一的|指定索引是否是唯一的。|  
|依據屬性|顯示定義索引的屬性顯示名稱。|  
  
 當您按一下索引時，則會顯示下列資訊。  
  
-   **建立者**：建立索引的使用者名稱。  
  
-   **於**：建立索引的日期與時間。  
  
-   **更新者**：上次更新索引的使用者名稱。  
  
-   **於**：建立索引的日期與時間。  
  
## <a name="next-steps"></a>後續步驟  
 [編輯和刪除索引 &#40;Master Data Services&#41;](../master-data-services/edit-and-delete-an-index-master-data-services.md)  
  
## <a name="see-also"></a>另請參閱  
 [自訂索引 &#40;Master Data Services&#41;](../master-data-services/custom-index-master-data-services.md)  
  
  
