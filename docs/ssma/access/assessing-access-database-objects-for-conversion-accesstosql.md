---
title: 存取資料庫物件評估轉換 (AccessToSQL) |Microsoft 文件
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-access
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- assessing SQL
- assessing syntax
- assessment reports
- creating assessment reports
- estimating migration effort
- reports
- SQL, assessing
- syntax, assessing
ms.assetid: 8b9e23d6-da62-437a-8c05-8ad2628b9441
caps.latest.revision: 16
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: fb353f5906c1ed5cb45d6075f92cf183ba5e276b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="assessing-access-database-objects-for-conversion-accesstosql"></a>轉換 (AccessToSQL) 評估來存取資料庫物件
在您載入的物件，並將資料移轉至之前[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]或 SQL Azure，您應該先判斷多少的移轉將會成功，並轉換可能會花多少時間。 SSMA 可以建立顯示之物件的成功轉換為百分比的評估報告[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]或 SQL Azure 的語法和時間估計執行移轉。 SSMA 也可讓您檢視造成轉換失敗的特定問題。  
  
## <a name="creating-assessment-reports"></a>建立的評估報告  
SSMA 當它建立的評估報告時，將轉換至的選取的存取資料庫物件[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]或 SQL Azure 語法，然後顯示結果。  
  
**若要建立的評估報告**  
  
1.  在存取中繼資料總管，選取您想要評估的資料庫。  
  
2.  若要省略個別物件，請清除您不想要評估的物件旁邊的核取方塊。  
  
3.  以滑鼠右鍵按一下**資料庫**，然後選取**建立報表**。  
  
    您也可以分析個別物件，以滑鼠右鍵按一下物件，然後選取**建立報表**。  
  
    SSMA 會顯示在視窗底部的狀態列中的進度。 如果 [輸出] 窗格是可見的也會看到 [輸出] 窗格中的訊息。  
  
當評估完成時[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]移轉小幫手進行存取： 評估報表 視窗隨即出現。  
  
## <a name="using-assessment-reports"></a>使用評估報告  
評估報表視窗包含三個窗格: [總管]、 [詳細資料] 窗格中和訊息窗格。  
  
-   [總管] 窗格可讓您瀏覽所評估的物件。 您可以按一下此窗格向下鑽研至個別資料表、 索引和索引鍵中的項目。  
  
-   [詳細資料] 窗格會顯示所選物件的轉換統計資料。  
  
-   [訊息] 窗格會顯示錯誤、 警告和參考用訊息轉換，和時間估計執行移轉和個別錯誤的更正步驟。  
  
再次執行評估報表或將結構描述轉換之前，您應該修正錯誤。 若要尋找錯誤，請按一下**錯誤**按鈕訊息 窗格中，然後展開每個錯誤，若要檢視的物件發生錯誤的清單。 如果您按一下 [訊息] 窗格中的物件時，所有錯誤和警告，該物件會都出現在 [詳細資料] 窗格中。  
  
## <a name="next-step"></a>下一個步驟  
[轉換 Access 資料庫物件](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>另請參閱  
[將 Access 資料庫移轉至 SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
