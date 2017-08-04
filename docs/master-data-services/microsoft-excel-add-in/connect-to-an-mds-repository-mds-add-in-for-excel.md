---
title: "連接到 MDS 儲存機制 （MDS 增益集的 Excel） |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f427312-4c09-4c8b-b9f9-8b235557a74b
caps.latest.revision: 12
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 87931c60b791fd106d0476ac037e1dfcd4041fb2
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="connect-to-an-mds-repository-mds-add-in-for-excel"></a>連接到 MDS 儲存機制 (適用於 Excel 的 MDS 增益集)
  在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，您必須先連接到 MDS 儲存機制，然後才能載入或發行資料。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序：  
  
-   您必須擁有存取 **[總管]** 功能區域的權限。  
  
### <a name="to-connect-to-an-mds-repository"></a>若要連接到 MDS 儲存機制  
  
1.  在 MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 的 [主要資料] 索引標籤上，於 [連接和載入] 群組中，按一下 [連接] 按鈕底下的箭號，然後按一下 [管理連接]。  
  
2.  在 [管理連接] 對話方塊的 [新增連接] 區段中，按一下 [建立新連接]。  
  
3.  按一下 **[新增]**。  
  
4.  在 [加入新連接] 對話方塊的 [描述] 欄位中，輸入連接的描述。 當您在工具列上按一下 [連接] 按鈕底下的箭號時，就會顯示這個連接。  
  
5.  在**MDS 伺服器位址**方塊中，輸入的 URL [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web 應用程式，例如`http://contoso/mds`。  
  
    > [!NOTE]  
    >  請確認您使用電腦名稱，不要使用 “localhost”。  
  
6.  按一下 **[確定]**。 此名稱就會顯示在 [現有連接] 區段中。  
  
7.  (選擇性) 按一下 [測試] 測試連接。 此時會顯示確認或錯誤對話方塊。 按一下 [確定] 關閉對話方塊。  
  
8.  按一下 **[連接]**。 [Master Data Services] 窗格隨即顯示。  
  
## <a name="next-steps"></a>後續步驟  
  
-   [將資料從 Master Data Services 匯入至 Excel](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)  
  
-   [在匯出之前篩選資料 &#40;適用於 Excel 的 MDS 增益集&#41;](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>另請參閱  
 [連接 &#40;適用於 Excel 的 MDS 增益集&#41;](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
  
