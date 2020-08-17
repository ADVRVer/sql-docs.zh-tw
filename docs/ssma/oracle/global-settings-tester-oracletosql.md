---
description: 全域設定 (測試器) (OracleToSQL)
title: " (測試人員)  (OracleToSQL) 的全域設定 |Microsoft Docs"
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4acc0f2a-85ba-4c99-856a-89030f5c418e
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: 789d2cbb22e03053ab8f03e0bdd50b6383ea788e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88320394"
---
# <a name="global-settings-tester-oracletosql"></a>全域設定 (測試器) (OracleToSQL)
使用 [ **通用設定** ] 對話方塊的 [測試人員] 頁面，即可指定 SSMA 測試人員的設定。  
  
若要存取測試人員設定，請在 [ **工具** ] 功能表上選取 [ **全域設定**]，然後按一下左窗格底部的 [ **測試人員** ]。  
  
## <a name="options"></a>選項。  
**可測試的物件分析**  
此設定指定是否要執行可測試物件的分析。 如果您想要讓 SSMA 測試人員分析和自動檢查相依物件，請選取 **[是]** 。 預設選項設定為 **[是]**。  
  
下列選項可用於此設定：  
  
1.  是  
  
2.  否  
  
**輔助資料表儲存模式**  
此設定會指定如何儲存在測試案例執行期間建立的內部輔助資料表。 您可以針對此特定設定設定下列選項：  
  
1.  一律刪除  
  
2.  一律儲存  
  
3.  資料表比較失敗時儲存  
  
4.  資料表比較失敗時詢問使用者  
  
預設選項組為： **一律刪除**。  
  
**執行資料復原**  
這項設定會指定是否要在每個測試案例執行之後，執行復原操作。 預設選項群組是 [ **否**]。  
  
下列選項可用於此設定：  
  
1.  是  
  
2.  否  
  
**在第一次失敗之後停止測試執行**  
如果執行時發生錯誤，此設定會指定是否要停止目前正在執行的測試案例。 預設選項設定為 **[是]**。  
  
下列選項可用於此設定：  
  
1.  是  
  
2.  否  
  
## <a name="see-also"></a>另請參閱  
[完成測試案例準備 &#40;OracleToSQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
  
