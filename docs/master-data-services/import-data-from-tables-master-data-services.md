---
title: 從資料表匯入資料
description: 從資料表匯入資料，並對模型進行大量資料變更。 使用此程式來新增、更新和刪除 Master Data Services 資料庫中的資料。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ad5b83b1-8e40-4ef8-9ba8-4ea17a58b672
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6e10a3facdec9b5b412b1c9b93396d2d0a94886e
ms.sourcegitcommit: 7d6eb09588ff3477cf39a8fd507d537a603bc60d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/16/2020
ms.locfileid: "84796305"
---
# <a name="import-data-from-tables-master-data-services"></a>從資料表匯入資料 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  您可以將大量資料加入 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]的模型中，也可對模型中的資料進行大量變更。  
  
 **先決條件**  
  
-   您必須具有將資料插入 stg.< 的許可權。 \<name>_Leaf，stg.<。 \<name>_Consolidated，stg.<。 \<name>資料庫中 _Relationship 資料表 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 。  
  
-   您必須擁有在資料庫中執行 udp_ stg.< \<name> _Leaf、stg.< \_ \<name> _Consolidated 或 stg.< \_ \<name> _Relationship 預存 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 程式的許可權。  
  
-   模型的狀態不得為 [已認可] ****。  
  
 **若要加入、更新和刪除資料庫中的資料 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]**  
  
1.  準備要匯入 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫之適當暫存資料表中的成員，這包括為必要欄位提供值。 如需暫存資料表的概觀，請參閱[概觀︰從資料表匯入資料 &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)  
  
    -   對於分葉成員，資料表為 stg.<。 \<name>_Leaf，其中 \<name> 指的是對應的實體。 如需必要欄位的資訊，請參閱[分葉成員暫存資料表 &#40;Master Data Services&#41;](../master-data-services/leaf-member-staging-table-master-data-services.md)  
  
    -   若為合併成員，則資料表為 stg.<。 \<name>_Consolidated。 如需必要欄位的資訊，請參閱[合併成員暫存資料表 &#40;Master Data Services&#41;](../master-data-services/consolidated-member-staging-table-master-data-services.md)。  
  
    -   若要在明確階層中移動成員的位置，資料表是 stg.<。 \<name>_Relationship。 如需必要欄位的資訊，請參閱[合併成員暫存資料表 &#40;Master Data Services&#41;](../master-data-services/relationship-staging-table-master-data-services.md)。  
  
         如需在明確階層中移動成員的概觀，請參閱[概觀︰從資料表匯入資料 &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)。  
  
    -   使用 **ImportType** 欄位值，指定您要建立新成員、停用成員或刪除成員。 如需這些值的詳細資訊，請參閱[分葉成員暫存資料表 &#40;Master Data Services&#41;](../master-data-services/leaf-member-staging-table-master-data-services.md) 和[合併成員暫存資料表 &#40;Master Data Services&#41;](../master-data-services/consolidated-member-staging-table-master-data-services.md)。  
  
         如需停用和刪除成員的概觀，請參閱[概觀︰從資料表匯入資料 &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)。  
  
2.  開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 並連接到您 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫的 Database Engine 執行個體。  
  
     如需詳細資訊，請參閱[SQL Server Management Studio](https://msdn.microsoft.com/library/66a6b7b1-de6a-4161-82bd-98ded486947b)。  
  
3.  使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的 [匯入和匯出精靈]，將資料匯入暫存資料表。  
  
     如需詳細資訊，請參閱＜ [SQL Server Import and Export Wizard](~/integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md)＞。  
  
4.  執行下列其中一項作業，將資料從暫存資料表載入 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料表：  
  
    -   執行對應到資料所要移往之暫存資料表的暫存預存程序。  
  
         如需暫存預存程序和暫存資料表的概觀，請參閱[概觀︰從資料表匯入資料 &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)。 如需暫存預存程序之參數及程式碼範例的詳細資訊，請參閱[暫存預存程序 &#40;Master Data Services&#41;](../master-data-services/staging-stored-procedure-master-data-services.md)。  
  
    -   使用主資料管理的 **整合管理** 功能。  
  
         在 [暫存批次] **** 頁面上，從下拉式清單中，選取要接收您所加入之資料的模型，然後按一下 [啟動批次] ****。 批次處理的狀態會顯示在 [狀態] **** 欄位中。 如需狀態的詳細資訊，請參閱[匯入狀態 &#40;Master Data Services&#41;](../master-data-services/import-statuses-master-data-services.md)。  
  
         ![主資料管理員中的暫存批次頁面](../master-data-services/media/mds-stagingbatchespage.png "主資料管理員中的暫存批次頁面")  
  
         暫存程序的啟動間隔，由 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中的 [暫存批次間隔]**** 設定決定。 如需詳細資訊，請參閱 [系統設定 &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md)。  
  
5.  檢視暫存期間發生的錯誤。 如需詳細資訊，請參閱[檢視暫存期間發生的錯誤 &#40;Master Data Services&#41;](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md) 和[暫存處理序錯誤 &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md)。  
  
6.  依據商務規則驗證資料。  
  
     在主資料管理員中，瀏覽至模型的 **Explorer** 功能區域，然後套用商務規則，以驗證資料。 如需詳細資訊，請參閱[根據商務規則驗證特定成員 &#40;Master Data Services&#41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)。 您也可以使用預存程序來驗證資料。 如需詳細資訊，請參閱 [驗證預存程序 &#40;Master Data Services&#41;](../master-data-services/validation-stored-procedure-master-data-services.md)。  
  
     當您從暫存資料表載入資料時，不會自動依商務規則驗證該資料。 如需何謂驗證和其發生時機的詳細資訊，請參閱[驗證 &#40;Master Data Services&#41;](../master-data-services/validation-master-data-services.md)。  
  
  
