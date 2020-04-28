---
title: 需要核准
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b475a53d-269d-49f3-bb42-965c555f80be
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 61d03410e5217175335caf0ca37241b28c887989
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "73729753"
---
# <a name="approval-required-master-data-services"></a>需要核准 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]內，系統管理員可以將實體設定為需要核准。 對此實體的所有變更都需要一個實體系統管理員檢閱並核准變更。  
  
> [!NOTE]  
>  分葉成員上所做的變更需要核准。 已被取代的明確階層和集合上之變更會略過核准。  
>   
>  暫存資料表的處理序所做的變更會略過核准。  
>   
>  商務規則所做的變更會略過核准。  
  
## <a name="prerequisites"></a>Prerequisites  
 若要執行此程序：  
  
-   您必須擁有存取 [系統管理] 功能區域的權限。  
  
-   您必須是模型管理員。 如需詳細資訊，請參閱[管理員 &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)  
  
-   實體必須存在。 如需詳細資訊，請參閱[建立實體 &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)  
  
## <a name="to-enable-approval-required-for-an-entity"></a>啟用實體所需的核准  
  
1.  在 [ [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]] 中，按一下 **[系統管理]**。  
  
2.  在 [**管理模型**] 頁面上，從方格中選取模型，然後按一下 [**實體**]。  
  
3.  在 [管理實體]**** 頁面上，從方格中選取含有您想要啟用 [需要核准]**** 之實體的資料列。  
  
4.  按一下 [編輯]****，並選取 [需要核准]****，然後按一下 [儲存]****。  
  
## <a name="see-also"></a>另請參閱  
 [變更集 &#40;Master Data Services&#41;](../master-data-services/changesets-master-data-services.md)  
  
  
