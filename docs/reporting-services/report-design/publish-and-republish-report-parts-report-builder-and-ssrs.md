---
title: "發行與重新發行報表組件 （報表產生器及 SSRS） |Microsoft 文件"
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
ms.assetid: 92dce484-f39b-403c-9caf-d8772bc3aca3
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 03b06d981e4ff824fbdca3f598271fce666237af
ms.contentlocale: zh-tw
ms.lasthandoff: 08/09/2017

---
# <a name="publish-and-republish-report-parts-report-builder-and-ssrs"></a>發行與重新發行報表組件 (報表產生器及 SSRS)
  報表組件是指已經個別發行至報表伺服器，而且可以在其他分頁報表中重複使用的分頁報表項目。 您可以使用預設值在預設位置發行報表組件，或者您可以編輯報表組件中繼資料 (例如名稱和描述)，並將其儲存在報表伺服器的其他位置。 如果您有正確的權限，也可以將其儲存到與報表伺服器整合的 SharePoint 網站。  
  
 您可以只發行相依之資料集內嵌在其中的報表組件，或者您可以個別發行資料集。 如果個別發行資料集，它會變成共用資料集，而且報表組件會連結到該資料集。 如需詳細資訊，請參閱 [報表產生器中的報表組件和資料集](../../reporting-services/report-data/report-parts-and-datasets-in-report-builder.md)。  
  
 您可以重新發行現有的報表組件。 如果您有權限，即使您沒有建立報表組件，也可以加以儲存以覆寫伺服器上報表組件的原始執行個體。 您也可以將它發行為新的報表組件，並儲存在相同或不同的位置。  
  
## <a name="to-publish-a-report-part"></a>若要發行報表組件  
  
1.  在 報表產生器 功能表中，按一下 **發行報表組件**。  
  
     如果您沒有連接到報表伺服器，系統會提示您連接。 如果您無法連接到報表伺服器，就無法啊型報表組件。  
  
2.  若要將您的報表組件儲存到預設位置的預設設定，請按一下**發行使用預設設定的所有報表組件**。  
  
     否則，請按一下**檢閱及修改報表組件發行前的**。  
  
3.  編輯報表組件名稱和描述： 按兩下名稱加以編輯，然後按一下 在**描述**欄位可加入描述。  
  
    > [!NOTE]  
    >  最好提供報表組件名稱和描述，以協助使用者在搜尋時識別它。 若是完整路徑，報表組件名稱的最大長度為 260 個字元，包括伺服器上的資料夾名稱，後面接著報表組件的實際名稱。  
  
4.  若要將您的報表組件儲存至預設值以外的資料夾中，按一下**瀏覽** 按鈕。  
  
5.  當您已將所有報表組件的選項，報表中時，按一下 **發行**。  
  
     發行報表組件之後，對話方塊會顯示成功發行的報表組件，以及未成功發行的報表組件。 您可以檢視詳細資料中的**發行報表組件**對話方塊中，報表組件無法發佈。  
  
6.  按一下 [ **關閉**]。  
  
## <a name="to-republish-a-report-part"></a>重新發行報表組件  
  
1.  請遵循先前的程序發行報表組件。  
  
2.  在**發行報表組件**對話方塊中，如果您按一下**發佈一份新報表組件為**，透過現有的報表組件的報表產生器就不會在伺服器上，但會改為建立其他報表組件。  
  
> [!NOTE]  
>  如果您將其發行為新的報表組件，它將會擁有一個新的唯一識別碼。 如果原始報表組件變更，它不會再接收更新。  
  
## <a name="see-also"></a>請參閱＜  
 [報表組件 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/report-parts-report-builder-and-ssrs.md)   
 [報表組件和報表產生器中的資料集](../../reporting-services/report-data/report-parts-and-datasets-in-report-builder.md)   
 [疑難排解報表組件 (報表產生器及 SSRS)](http://msdn.microsoft.com/en-us/d9fe1932-46e7-421b-a8a9-4c54d9576e94)   
 [檢查更新或關閉更新 (報表產生器及 SSRS)](http://msdn.microsoft.com/en-us/9c69792d-d7c4-453b-ae2f-6d2d071d8606)   
 [瀏覽報表組件及設定預設資料夾 &#40;報表產生器及 SSRS&#41;](../../reporting-services/report-design/browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs.md)  
  
  
