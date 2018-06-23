---
title: 匯出資料 (Master Data Services) |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exporting data [Master Data Services]
- subscription views [Master Data Services]
- subscription views [Master Data Services], about subscription views
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 656578a35e70b8371056330e0edec69073816687
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36035011"
---
# <a name="exporting-data-master-data-services"></a>匯出資料 (Master Data Services)
  您可以匯出[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]資料至訂閱系統建立訂閱檢視。 然後，任何訂閱系統可以檢視 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫中的已發行資料。 如需檢視的詳細資訊，請參閱 [檢視](../relational-databases/views/views.md)。  
  
## <a name="subscription-view-formats"></a>訂閱檢視格式  
 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]當您在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中建立檢視時，可以從  提供的一組標準檢視格式中選擇。 您可以使用這些格式來建立顯示下列項目的檢視表：  
  
-   所有分葉成員及其屬性。  
  
-   所有合併成員及其屬性。  
  
-   所有集合及其屬性。  
  
-   明確加入至集合的成員。  
  
-   在衍生階層中的父子式或層級格式成員。  
  
-   在所有明確階層中，實體的父子式或層級格式成員。  
  
## <a name="subscription-views-can-become-out-of-date"></a>訂閱檢視可能過期  
 在建立實體或階層的訂閱檢視之後，檢視中未自動反映相關聯的模型物件變更。 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 您可能需要在 中重新產生訂閱檢視，以反映模型物件變更。 當模型物件變更時， **[匯出]** 頁面上的 **[已變更]** 欄會更新為 **True** 。 **True** 表示您應該編輯並儲存訂閱檢視，藉以重新產生訂閱檢視。  
  
## <a name="related-tasks"></a>相關工作  
  
|工作描述|主題|  
|----------------------|-----------|  
|建立主要資料的訂閱檢視。|[建立訂閱檢視&#40;Master Data Services&#41;](create-a-subscription-view-to-export-data-master-data-services.md)|  
|刪除現有的訂閱檢視。|[刪除訂閱檢視&#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-subscription-view-master-data-services.md)|  
  
## <a name="related-content"></a>相關內容  
  
-   [訂閱檢視格式&#40;Master Data Services&#41;](../../2014/master-data-services/subscription-view-formats-master-data-services.md)  
  
-   [檢視](../relational-databases/views/views.md)  
  
  