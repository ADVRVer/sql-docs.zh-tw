---
title: 套用及更新變更集 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 3a6a3cf2-1e77-43d3-a64a-855ae51258e7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 386bdbd2e7361567030a7d2a97e270172bdd21c7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68047756"
---
# <a name="apply-and-update-a-changeset-master-data-services"></a>套用及更新變更集 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  變更集是對主要資料所做的暫止變更集合。 您可以在本機套用變更集，以檢視、新增、更新及刪除變更集中的暫止變更。  
  
## <a name="prerequisites"></a>先決條件  
  
-   您必須擁有存取 **[總管]** 功能區域的權限。 如需詳細資訊，請參閱[功能區域權限 &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md)。  
  
-   您必須至少具有實體或其中一個屬性的更新存取權。  
  
-   您只能檢視您所擁有的變更集，或當您是實體系統管理員時所提交核准的變更集。  
  
-   您只能修改您所擁有的變更集，以及變更集狀態何時為開啟或已拒絕。  
  
## <a name="to-apply-and-update-a-changeset"></a>套用及更新變更集  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，選取模型和版本，然後按一下 [Explorer]  。  
  
2.  按一下 [實體]  功能表中的實體。  
  
3.  在右窗格中，選取 [變更集]  ，然後按兩下您要檢視及變更的變更集。  
  
4.  按一下 **[套用]** 。  
  
     暫止的變更會套用至方格中的實體成員。 暫止的變更會反白顯示。  
  
     建立、刪除及更新成員會在變更集中產生變更。  
  
5.  若要還原暫止的變更，請在 [變更集]  窗格中，以滑鼠右鍵按一下方格，然後按一下 [還原]  。  
  
## <a name="next-steps"></a>後續步驟  
 [認可或提交變更集 &#40;Master Data Services&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>另請參閱  
 [建立變更集 &#40;Master Data Services&#41;](../master-data-services/create-a-changeset-master-data-services.md)   
 [核准或拒絕變更集 &#40;Master Data Services&#41;](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
  
