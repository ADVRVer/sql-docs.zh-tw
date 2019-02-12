---
title: 工作 4:將結果匯出比對活動到 Excel 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 644454c4-3c5a-469a-90ec-e51dc7fb99fc
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: c9424f2ba21fb4b93e359c8662974a82c62b4895
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2019
ms.locfileid: "56020439"
---
# <a name="task-4-exporting-the-results-from-matching-activity-to-an-excel-file"></a>工作 4:將比對活動的結果匯出到 Excel 檔案
  在這項工作中，您會將比對活動的結果匯出到 Excel 檔案。  
  
1.  在 **匯出**頁面上，選取**Excel 檔案**for**目的型別**。  
  
2.  選取 **生存結果**選項。 在生存程序中，DQS 會決定根據每個叢集的存活者記錄**存活規則**您已選取。  
  
3.  按一下 **瀏覽**並瀏覽至您要儲存輸出檔案的資料夾。  
  
4.  型別**Cleansed and Matched Suppliers.xls**的名稱，然後按一下**開啟**。  
  
5.  確認**樞紐記錄**選取**存活規則**。 當您選取此選項時，便會針對叢集的輸出挑選每個叢集的樞紐記錄。 存活規則的其他選項包括：  
  
    1.  **最完整的記錄：** 生存者記錄是已填入最多欄位的記錄。  
  
    2.  **最長的記錄：** 生存者記錄是在來源欄位中具有最多詞彙數目的記錄。  
  
    3.  **最完整且最長的記錄：** 生存者記錄是已填入最多欄位並且在每個欄位中具有最多詞彙的記錄。  
  
     ![匯出比對頁面結果](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "匯出比對頁面結果")  
  
6.  按一下 **匯出**將結果匯出到 Excel 檔案。  
  
7.  按一下 **關閉 **以關閉**比對匯出** 對話方塊。  
  
8.  按一下 **完成**完成比對活動。  
  
9. 開啟**Cleansed and Matched Suppliers.xlsx**檔案，並確認您未看到任何重複項 (SupplierID)。  
  
 現在，您的供應商資料已經清理和比對，以移除重複項。  
  
## <a name="next-step"></a>下一個步驟  
 [第 4 課：在 MDS 中儲存供應商資料](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)  
  
  
