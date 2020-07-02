---
title: 刪除商務規則
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting business rules [Master Data Services]
- business rules [Master Data Services], deleting
ms.assetid: b97aa4f9-569f-451d-ad62-65b81f980299
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 475af6465a5e79e6577c60ac88a312fb5d0d4cf9
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85812770"
---
# <a name="delete-a-business-rule-master-data-services"></a>刪除商務規則 (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，刪除不再需要的商務規則。  
  
> [!NOTE]  
>  您可以避免資料使用商務規則來加以驗證，其方式是排除該商務規則，而不是將它刪除。 如需詳細資訊，請參閱 [排除商務規則 &#40;Master Data Services&#41;](../master-data-services/exclude-a-business-rule-master-data-services.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序：  
  
-   您必須擁有存取 **[系統管理]** 功能區域的權限。  
  
-   您必須是模型管理員。 如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)。  
  
### <a name="to-delete-a-business-rule"></a>若要刪除商務規則  
  
1.  在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。  
  
2.  從功能表列，指向 **[管理]** ，然後按一下 **[商務規則]**。  
  
3.  在 [**商務規則**] 頁面上，從 [**模型**] 下拉式清單中選取模型。  
  
4.  從 [實體] **** 下拉式清單選取實體。  
  
5.  從 [成員類型] **** 下拉式清單中，選取要套用商務規則的成員類型。  
  
6.  在方格中，按一下您想要刪除之商務規則的資料列。  
  
7.  按一下 **[刪除]** 。  
  
8.  在確認對話方塊中按一下 **[確定]**。 [商務規則狀態]**** 資料行中的值是 [刪除暫止]****。  
  
9. 按一下 [全部發行] ****。  
  
10. 在確認對話方塊中按一下 **[確定]**。 刪除的商務規則將不再顯示在方格中。  
  
## <a name="see-also"></a>另請參閱  
 [排除商務規則 &#40;Master Data Services&#41;](../master-data-services/exclude-a-business-rule-master-data-services.md)   
 [建立和發佈商務規則 &#40;Master Data Services&#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [商務規則 &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
  
