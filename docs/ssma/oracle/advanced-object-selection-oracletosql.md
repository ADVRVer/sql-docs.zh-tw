---
title: 進階物件選取項目 (OracleToSQL) |Microsoft 文件
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c978fba4-c953-4ed0-a21d-1b38e7225552
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: v-pelars
ms.openlocfilehash: 01fcdf57e6c9b99537ab40ffa54db9e0414eebad
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="advanced-object-selection--oracletosql"></a>進階的物件選取項目 (OracleToSQL)
**進階物件部分**對話方塊可讓您篩選資料庫物件，使用字串和子字串中的物件名稱，然後選取或取消選取這些物件。 SSMA 會執行轉換並移轉作業選取的物件。  
  
若要存取此對話方塊中，在 [中繼資料總管] 上按一下滑鼠右鍵，然後選取**進階物件選取項目**。  
  
當您第一次開啟對話方塊中時，按一下 **顯示子類別目錄項目**顯示所有已載入專案的中繼資料的物件。 然後，您可以輸入字串以篩選的項目。 例如，輸入的字串 「 公司 」 顯示名稱中包含該字串的所有項目。  
  
使用此對話方塊之前，您可以強制 SSMA 載入轉換結構描述，或儲存專案的所有中繼資料。  
  
## <a name="options"></a>選項  
**請檢查所有的項目**  
將所有項目旁的核取記號。 在 [中繼資料總管] 會立即選取這些項目。  
  
**取消選取所有項目**  
移除所有項目旁的核取記號。 在 [中繼資料總管] 會立即清除這些項目。  
  
**清單檢視模式**  
顯示篩選清單項目。  
  
**資料表檢視模式**  
顯示篩選資料表中的項目。  
  
**顯示只載入的項目**  
切換顯示分類或項目。 選取此按鈕時，SSMA 會顯示符合篩選準則與先前已載入的所有項目。 如果沒有選取此按鈕，SSMA 會顯示類別目錄資料夾。  
  
**篩選**  
輸入您想要篩選項目使用的字串。 例如，尋找所有可用的項目包含字串"ID"項目名稱中，輸入字串 「 識別碼 」 中**篩選**方塊。  
  
如果項目相符的篩選準則，分類或項目會隨著您的輸入字串。 若要查看相符的項目，我們建議您按一下**顯示只有載入的項目** 按鈕。  
  
**清除篩選**  
清除**篩選**方塊。  
  
