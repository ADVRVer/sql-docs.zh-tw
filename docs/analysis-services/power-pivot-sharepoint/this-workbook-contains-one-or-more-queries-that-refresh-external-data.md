---
title: "此活頁簿包含一或多個重新整理外部資料的查詢 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aa65c992-eb41-4032-9e11-a9ba871b6a3c
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 354c8c0baca1372c0bc6cb17e2acbfc74c45b9b4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="this-workbook-contains-one-or-more-queries-that-refresh-external-data"></a>此活頁簿包含一或多個重新整理外部資料的查詢
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]包含的 Excel 活頁簿[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]資料，Excel Services 會顯示這個警告，當它偵測到連接資訊，並提示您啟用或停用此活頁簿的查詢。  
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] for SharePoint|  
|產品版本|[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11_md](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14_md](../../includes/sssql14-md.md)]|  
|原因|Excel Services 設定為資料重新整理時警告。|  
|訊息文字|此活頁簿包含可重新整理外部資料的一個或多個查詢。 惡意使用者可以設計一個查詢來存取機密資訊，並將其散發給其他使用者或執行其他有害的動作。<br /><br /> 如果您信任此活頁簿的來源，按一下 [是]，啟用此活頁簿中對外部資料的查詢。 如果您不確定，按一下 [否]，變更就不會套用到您的活頁簿中。<br /><br /> 您要啟用此活頁簿中對外部資料的查詢嗎？|  
  
## <a name="explanation"></a>說明  
 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 活頁簿包含內嵌的資料連接字串，Excel 會使用這些連接字串與載入和計算資料的外部 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 伺服器進行通訊。 如果啟用資料重新整理時警告，Excel Services 會偵測此連接字串，並據此警告使用者。  
  
 若要篩選與配量活頁簿中的 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 資料，必須啟用查詢。 請務必僅針對您信任的 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 活頁簿啟用查詢。  
  
## <a name="user-action"></a>使用者動作  
 按一下 [是] 以啟用查詢。  
  
 您也可以變更組態設定，不再於重新整理時警告。  
  
1.  在 [管理中心] 的 [應用程式管理] 中，按一下 **[管理服務應用程式]**。  
  
2.  按一下 [Excel Services 應用程式]。  
  
3.  按一下 [信任的檔案位置]。  
  
4.  按一下 [http://] 或是您想要設定的位置。  
  
5.  在 [外部資料] 中，清除 [Warn on data refresh (資料重新整理時警告)] 的核取方塊。  
  
6.  按一下 [確定] 。  
  
 或者，您可以針對包含 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] 活頁簿的網站建立新的信任位置，然後只針對該網站修改組態設定。 如需詳細資訊，請參閱[在管理中心建立 Power Pivot 網站的信任位置](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)。  
  
  
