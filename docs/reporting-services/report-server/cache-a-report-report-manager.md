---
title: "快取報表 （報表管理員） |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- report execution properties [Reporting Services]
- cache [Reporting Services]
- cached reports [Reporting Services]
- schedules [Reporting Services], report expiration
- expiration [Reporting Services]
ms.assetid: 723d1cb0-c2e7-4763-8690-a6a7a8bbbb90
caps.latest.revision: 42
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: af00978c2afb28937a008f22eebe76f1a3f78eb1
ms.contentlocale: zh-tw
ms.lasthandoff: 08/09/2017

---
# <a name="cache-a-report-report-manager"></a>快取報表 (報表管理員)
  改善效能的其中一種方式就是設定報表的快取屬性。 快取報表時，系統就會在一段短時間內儲存已轉譯報表的副本。 要求報表的第一位使用者必須等候所有處理都完成，然後才能檢視該報表。 在快取期間內要求該報表的後續使用者可以立即檢視報表，因為處理已經進行了。  
  
 您可以快取的報表類型有所限制。 例如，如果報表輸出會因使用者識別而不同，或者資料是使用要求報表之使用者的安全性 Token 擷取的，系統就無法快取該報表。 如需詳細資訊，請參閱 [快取報表 &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)。  
  
### <a name="to-schedule-the-expiration-of-a-cached-report"></a>若要排程快取報表的逾期  
  
1.  啟動[報表管理員 &#40;SSRS 原生模式&#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)。  
  
2.  在報表管理員中，導覽至 **[內容]** 頁面。 導覽至您想要設定快取屬性的報表、將滑鼠停留在該項目上，然後按一下下拉箭號。  
  
3.  在下拉式功能表中，按一下 **[管理]**。  
  
4.  在左框架內，按一下**處理選項**。  
  
5.  在頁面上，選取**永遠以最新的資料執行此報表**。  
  
6.  選取下列兩個快取選項的其中之一，並設定逾期如下：  
  
    -   若要設定快取副本在特定時間週期之後過期，請按一下 **快取報表的暫存副本。讓報表副本過期的分鐘數之後**。 輸入報表過期的分鐘數。  
  
    -   若要設定排程時間過期的快取的副本，請按一下**快取報表的暫存副本。讓下列排程上的報表副本過期。** 按一下**設定**，或選取共用的排程來控制報表逾期  
  
7.  按一下 **[套用]**。  
  
## <a name="see-also"></a>另請參閱  
 [設定報表處理屬性](../../reporting-services/report-server/set-report-processing-properties.md)   
 [快取報表 &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)  
  
  
