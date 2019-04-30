---
title: 一般屬性頁面、 報表組件 （報表管理員） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 93ddce72-31f1-42f7-abd5-8191acbb00c5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 25dc3a8eb075f212728796465fe2d95c460cbebf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63260696"
---
# <a name="general-properties-page-report-parts-report-manager"></a>一般屬性頁面、報表組件 (報表管理員)
  使用 [屬性] 頁面來檢視及管理報表組件的一般屬性。  
  
 您無法從報表管理員檢視或變更報表組件的外觀和功能。 若要變更設計，您必須使用撰寫工具來開啟及修改設計，然後將該設計重新發行至伺服器。  
  
## <a name="navigation"></a>巡覽  
 您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。  
  
###### <a name="to-open-the-properties-page-for-a-report-part"></a>開啟報表組件的屬性頁面  
  
1.  開啟報表管理員，然後找出您想要設定屬性的報表組件。  
  
2.  將滑鼠停留在該報表組件上方，然後按下拉式箭號。  
  
3.  在下拉式清單中，按一下 **[管理]**， 就會開啟 [一般] 屬性頁面。  
  
## <a name="options"></a>選項。  
 **修改的日期**  
 上次在伺服器上修改報表組件屬性的日期和時間，或是新版本報表組件發行至伺服器的日期和時間。 唯讀。  
  
 **修改者**  
 上次修改報表組件的使用者名稱。 唯讀。  
  
 **建立日期**  
 報表組件最初發行至伺服器的日期和時間。 唯讀。  
  
 **所建立**  
 最初建立報表組件的使用者名稱。 唯讀。  
  
 **大小**  
 報表組件的檔案大小。 唯讀。  
  
 **名稱**  
 輸入名稱以識別報表組件。  
  
 **說明**  
 提供有關報表組件的資訊。 此描述會出現在報表管理員的 [內容] 頁面上。 當使用者從報表撰寫工具搜尋報表組件時，可搜尋描述文字。  
  
 **在清單檢視中隱藏**  
 選取此選項可以隱藏報表組件，避免在報表管理員中使用清單檢視模式的使用者看見。 清單檢視模式是您瀏覽報表伺服器資料夾階層時的預設檢視格式。 雖然在清單檢視中可以隱藏項目，但在詳細資料檢視中則不行。 如果想要限制項目的存取，您必須建立角色指派。  
  
 **型別**  
 報表組件的類型。 唯讀。  
  
 **Apply**  
 儲存變更。  
  
 **刪除**  
 從報表伺服器資料庫中移除報表組件。 從伺服器刪除報表組件不會防止已加入該報表組件的現有報表轉譯。  
  
 **[移動]**  
 按一下以開啟 [移動項目] 頁面，可在報表伺服器資料夾階層之中移動報表組件。 如需詳細資訊，請參閱 <<c0> [ 移動項目頁面&#40;報表管理員&#41;](../../2014/reporting-services/move-items-page-report-manager.md)。</c0>  
  
 **下載**  
 擷取報表組件定義複本，以儲存成 .rsc 檔。 .rsc 檔可以上傳至報表伺服器資料夾，或用來取代在報表伺服器資料夾中的現有報表組件。  
  
 **取代**  
 以 .rsc 檔中不同的定義取代報表組件定義。  
  
## <a name="see-also"></a>另請參閱  
 [管理報表組件](report-design/managing-report-parts.md)   
 [報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [內容頁面 &#40;報表管理員&#41;](../../2014/reporting-services/contents-page-report-manager.md)   
 [報表組件 &#40;報表產生器及 SSRS&#41;](report-parts-report-builder-and-ssrs.md)   
 [報表管理員 F1 說明](../../2014/reporting-services/report-manager-f1-help.md)   
 [報表產生器中的報表組件和資料集](report-data/report-parts-and-datasets-in-report-builder.md)  
  
  
