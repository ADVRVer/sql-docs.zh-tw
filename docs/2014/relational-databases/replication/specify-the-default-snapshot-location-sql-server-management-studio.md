---
title: 指定預設快照集位置 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], default locations
- default snapshot locations
ms.assetid: 27c5d9ad-a915-4c59-a8b7-82e3af61ac4d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fc9734cb3da7c61da7c15ce108cd86f09be8ea1b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48148838"
---
# <a name="specify-the-default-snapshot-location-sql-server-management-studio"></a>指定預設快照集位置 (SQL Server Management Studio)
  在「設定散發精靈」的 **[快照集資料夾]** 頁面中指定預設快照集位置。 如需使用此精靈的詳細資訊，請參閱[設定發行和散發](configure-publishing-and-distribution.md)。 如果您在未設定為「散發者」的伺服器上建立發行集，則請在「新增發行集精靈」的 **[快照集資料夾]** 頁面中指定預設快照集位置。 如需使用此精靈的詳細資訊，請參閱[建立發行集](publish/create-a-publication.md)。  
  
 在 [散發者屬性 - \<散發者>] 對話方塊的 [發行者] 頁面上，修改預設快照集位置。 如需詳細資訊，請參閱[檢視及修改散發者和發行者屬性](view-and-modify-distributor-and-publisher-properties.md)。 在 [發行集屬性 - \<發行集>] 對話方塊中為每個發行集設定快照集資料夾。 如需詳細資訊，請參閱 [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md)。  
  
### <a name="to-modify-the-default-snapshot-location"></a>若要修改預設快照集位置  
  
1.  在 [散發者屬性 - \<散發者>] 對話方塊的 [發行者] 頁面上，按一下您要變更其預設快照集位置之發行者的屬性按鈕 (**…**)。  
  
2.  在 [發行者屬性 - \<發行者>] 對話方塊中，輸入 [預設快照集資料夾] 屬性的值。  
  
    > [!NOTE]  
    >  快照集代理程式必須有您指定之目錄的寫入權限，而散發代理程式或合併代理程式則必須有讀取權限。 如果使用提取訂閱，您必須指定一個共用目錄作為通用命名慣例 (UNC) 路徑，例如 \\\computername\snapshot。 如需詳細資訊，請參閱[保護快照集資料夾](security/secure-the-snapshot-folder.md)。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [替代快照集資料夾位置](alternate-snapshot-folder-locations.md)   
 [使用快照集初始化訂閱](initialize-a-subscription-with-a-snapshot.md)  
  
  
