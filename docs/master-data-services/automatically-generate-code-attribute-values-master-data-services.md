---
title: 自動產生 Code 屬性值
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 19b354ee-2906-4cc7-ba2f-32b4543bddcf
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 85cfc3d3859712cdb53b7db58bb1729baca692b3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729731"
---
# <a name="automatically-generate-code-attribute-values-master-data-services"></a>自動產生 Code 屬性值 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中，當您希望每次建立新成員時，自動將整數指派給 Code 值，請自動為實體的 Code 屬性產生值。  
  
## <a name="prerequisites"></a>Prerequisites  
 若要執行此程序：  
  
-   您必須擁有存取 **[系統管理]** 功能區域的權限。  
  
-   您必須是模型管理員。 如需詳細資訊，請參閱 [管理員 &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)，您就可以在群組中加入及移除使用者。  
  
-   實體必須存在。 如需詳細資訊，請參閱[建立實體 &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)。  
  
### <a name="to-automatically-generate-code-values"></a>若要自動產生值字碼  
  
1.  在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。  
  
2.  在 [管理模型] **** 頁面上，選取含有您想要編輯之實體的模型資料列，然後按一下 [實體] ****。  
  
3.  在 [管理實體] **** 頁面上，選取您要為其產生程式碼之實體的資料列，然後按一下 [編輯] ****。  
  
4.  選取 **[自動建立字碼值]** 核取方塊。  
  
5.  在 **[開始]** 方塊中，輸入開始遞增的數字。 如果成員已存在，則將根據最大的現有值設定 Code。 例如，若最大的現有 Code 值為 299，則下一個成員的 Code 值將設為 300。  
  
6.  按一下 [檔案]  。  
  
## <a name="see-also"></a>另請參閱  
 [自動建立程式碼 &#40;Master Data Services&#41;](../master-data-services/automatic-code-creation-master-data-services.md)   
 [自動產生程式碼 &#40;Master Data Services 以外的屬性值&#41;](../master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)  
  
  
