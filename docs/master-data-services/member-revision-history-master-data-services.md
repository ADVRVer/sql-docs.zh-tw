---
title: "成員修訂歷程記錄 (Master Data Services) |Microsoft 文件"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 113069c5-12e6-48ec-b443-b42e14f77308
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8397d82b231588457a85a65d1d9f19aaec1431f1
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="member-revision-history-master-data-services"></a>成員修訂歷程記錄 (Master Data Services)
  如果實體交易記錄類型是成員，則每次成員有所變更時，系統都會記錄成員修訂歷程記錄。  
  
 如需交易記錄類型的資訊，請參閱[變更實體交易記錄類型 &#40;Master Data Services&#41;](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)。  
  
 當發生下列變更時，系統即會記錄成員修訂歷程記錄。  
  
-   建立、刪除、重新啟動或清除成員。  
  
-   屬性值變更。  
  
-   在階層或集合中移動成員  
  
## <a name="view-and-manage-revision-history-by-entity"></a>依實體檢視及管理修訂歷程記錄  
 在 Explorer 功能區域中，您可以檢視實體中所有成員的修訂。 如果您有更新的權限，即可將成員復原回先前的修訂版本。  
  
 **若要檢視及管理修訂歷程記錄**  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，選取模型和版本，然後按一下 [Explorer] 。  
  
2.  從 [實體]  功能表中，選取實體。  
  
3.  按一下 [檢視歷程記錄]  ，可檢視實體的所有歷程記錄資料。  
  
4.  按一下 [篩選]  可篩選資料。  
  
5.  按一下資料行標頭可排序資料。  
  
6.  如果您有更新的權限，按一下 [Revert Member] \ (還原成員) 即可回復到選取的版本。  
  
## <a name="view-and-manage-revision-history-by-member"></a>依成員檢視及管理修訂歷程記錄  
 如果您擁有成員的讀取權限，即可在 Explorer 功能區域中，檢視實體中成員的修訂。 如果您有更新的權限，即可將成員復原回先前的修訂版本或加入修訂註解。  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，選取模型和版本，然後按一下 [Explorer] 。  
  
2.  從 [實體]  功能表中，選取實體。  
  
3.  選取成員。  
  
4.  按一下右窗格中的 [檢視歷程記錄]  。  
  
## <a name="log-retention-setting"></a>記錄保留設定  
 您可以設定 **資料庫系統設定中的 [Log retention in Days]**[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] (記錄保留天數) 屬性，以及在建立或編輯模型時設定 [Log Retention Days]  \(記錄保留天數)，以設定歷程記錄資料保留的時間長度。  
  
## <a name="related-task"></a>相關工作  
  
|工作描述|主題|  
|----------------------|-----------|  
|回復成員修訂歷程記錄|[回復成員修訂歷程記錄 &#40;Master Data Services&#41;](../master-data-services/rollback-member-revision-history-master-data-services.md)|  
  
## <a name="see-also"></a>另請參閱  
 [建立模型 &#40;Master Data Services&#41;](../master-data-services/create-a-model-master-data-services.md)   
 [系統設定 &#40;Master Data services&#41;](../master-data-services/system-settings-master-data-services.md)  
  
  
