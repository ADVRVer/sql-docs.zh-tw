---
title: 變更實體交易記錄類型
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 75250b32-3384-43c2-9b5c-1607cc3aa7b3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fde8e314462846088c7c673524d6e6d8d29ee631
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "73729671"
---
# <a name="change-the-entity-transaction-log-type-master-data-services"></a>變更實體交易記錄類型 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  您可以將實體交易記錄類型變更成屬性、成員或無。  
  
|交易記錄類型|描述|  
|--------------------------|-----------------|  
|屬性|實體變更記錄儲存在屬性等級。<br /><br /> 交易記錄檔會儲存起來，就像[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]是一樣。|  
|member|實體變更記錄儲存在資料列等級。<br /><br /> 任何屬性變更都會觸發新的資料列修訂。<br /><br /> 使用資料列交易記錄類型時，實體會儲存為緩時變維度類型 4。 支援類型 2 訂閱檢視和類型 4 (記錄) 訂閱檢視。 如需詳細資訊，請參閱[訂閱檢視格式 &#40;Master Data Services&#41;](../master-data-services/subscription-view-formats-master-data-services.md)。<br /><br /> 提供更佳的效能。|  
|None|不儲存變更記錄。<br /><br /> 提供最佳效能。|  
  
## <a name="prerequisites"></a>Prerequisites  
 若要執行此程序：  
  
-   您必須擁有存取 [系統管理] 功能區域的權限。如需詳細資訊，請參閱[功能區域權限 &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md)。  
  
-   您必須是模型管理員。 如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)。  
  
-   實體必須存在。 如需詳細資訊，請參閱[建立實體 &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)。  
  
 **變更交易記錄類型。**  
  
1.  在主資料管理員中，按一下 [系統管理] ****。  
  
2.  在 [管理模型]**** 頁面上，選取您要編輯的實體模型資料列，然後按一下 [實體]****。  
  
3.  在 [管理實體]**** 頁面上，選取您要更新的實體資料列，然後按一下 [編輯]****。  
  
4.  選擇下拉式清單中的交易記錄類型。  
  
5.  按一下 [檔案]  。  
  
  
