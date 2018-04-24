---
title: 合併衝突 (適用於 Excel 的 MDS 增益集) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: ''
ms.component: microsoft-excel-add-in
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf95978f-a2c5-4325-8606-dbd4e88741b8
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fd0eb09c16ca108270b69669825e2ced4dd28631
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="merge-conflicts-mds-add-in-for-excel"></a>合併衝突 (適用於 Excel 的 MDS 增益集)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  在適用於 Excel 的 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 增益集中，如果資料已由另一位使用者在伺服器上變更的話，則該發行將會失敗並會出現衝突錯誤。 若要解決此錯誤，可以執行合併衝突，然後重新發佈所做的變更。  
  
## <a name="prerequisites"></a>Prerequisites  
 若要執行此程序：  
  
-   您必須擁有存取 **[總管]** 功能區域的權限。  
  
-   針對要更新的實體分葉模型物件，您必須至少擁有最小的更新權限。  
  
-   使用中工作表必須有 MDS 管理的資料。  
  
-   在您嘗試發行變更之後，使用中工作表一定會有衝突錯誤。  
  
### <a name="to-merge-conflicts"></a>合併衝突  
  
1.  在工作表中，選取具有衝突錯誤的資料列或資料格。  
  
2.  在 [發行和驗證] 功能表群組中，選取 [合併衝突] 以開啟 [合併衝突] 對話方塊。  
  
3.  在 [合併衝突] 對話方塊中，您可以︰  
  
    -   選擇 [最新]，並按一下 [套用] 復原暫止的變更，然後重新載入來自伺服器的最新版本。  
  
    -   選擇 [原始]，並按一下 [套用] 套用工作表中的原始版本。  
  
    -   選擇 [您的]，並按一下 [套用] 保留現有的本機變更。  
  
4.  按一下 [套用] 之後，您可以進行其他變更，並重新發佈。 或是按一下 [取消] 取消更新，並重新載入來自伺服器的最新版本。  
  
## <a name="see-also"></a>另請參閱  
 [概觀：從 Excel 匯入資料 &#40;適用於 Excel 的 MDS 增益集&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
