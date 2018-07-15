---
title: 檢視暫存處理序 (Master Data Services) 期間發生的錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], viewing errors
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: f5a6dc218cdef2e30e8b25891dc38fe61f5e20bd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209398"
---
# <a name="view-errors-that-occur-during-the-staging-process-master-data-services"></a>檢視暫存處理序期間發生的錯誤 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以檢視暫存處理序期間發生的錯誤。 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫提供下列兩個用來顯示錯誤的檢視：  
  
-   分葉或合併成員更新適用的 stg.viw_name_MemberErrorDetails。  
  
-   階層關聯性更新適用的 stg.viw_name_RelationshipErrorDetails。  
  
## <a name="prerequisites"></a>先決條件  
 若要執行此程序：  
  
-   在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫中，您必須具有 stg.viw_name_MemberErrorDetails 或 stg.viw_name_RelationshipErrorDetails 檢視的 SELECT 權限。  
  
-   您必須是模型管理員。 如需詳細資訊，請參閱 [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md) (管理員 (Master Data Services))。  
  
### <a name="to-view-staging-errors"></a>檢視暫存錯誤  
  
1.  開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 並且連接到 [!INCLUDE[ssDE](../includes/ssde-md.md)] 資料庫的 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 執行個體。  
  
2.  開啟新的查詢。  
  
3.  輸入下列文字，以您的暫存資料表名稱取代名稱，例如 viw_Product_MemberErrorDetails。  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  執行查詢。 錯誤詳細資料會顯示在 **ErrorDescription** 欄位中。  
  
## <a name="next-steps"></a>後續步驟  
 如需錯誤訊息的詳細資訊，請參閱[暫存處理序錯誤 &#40;Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料匯入&#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [暫存處理序疑難排解 (Master Data Services)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  
