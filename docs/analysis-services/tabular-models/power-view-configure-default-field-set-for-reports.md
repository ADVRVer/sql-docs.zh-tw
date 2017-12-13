---
title: "設定 Power View 報表 (SSAS 表格式) 的預設欄位集 |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ql12.asvs.bidtoolset.deffieldset.f1
ms.assetid: 6836b42f-28b8-4a98-a86d-2c3c109f0189
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7e5a36f650081d5932e7100abc923b627a4aa47c
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2017
---
# <a name="power-view---configure-default-field-set-for-reports"></a>Power View-設定報表的預設欄位集
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]預設欄位集是預先定義的資料行和量值，會自動加入至清單[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]報表欄位清單中選取資料表時，報表畫布。 表格式模型作者可以建立預設欄位集，針對在報表中使用此模型的報表作者移除多餘的步驟。 例如，如果您知道使用客戶連絡資訊的大部分報表作者都想要看到連絡人的名稱、主要電話號碼、電子郵件地址和公司名稱，您可以預先選取這些資料行，這樣當報表作者按一下 [客戶連絡人] 資料表時，這些資料行就會固定加入到報表畫布上。  
  
> [!NOTE]  
>  預設欄位集只會套用至 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]中當做資料模型使用的表格式模型。 Excel 的樞紐分析報表不支援預設欄位集。  
  
## <a name="creating-a-default-field-set"></a>建立預設欄位集  
 您可以決定在 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]中選取特定資料表時，預設要包含哪些欄位 (如果有的話)。 您也可以決定欄位出現在清單上的順序。 若要指定預設欄位集，您必須在表格式模型專案中設定報表屬性。  
  
#### <a name="to-add-a-default-field-set"></a>若要加入預設欄位集  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，按一下您要設定預設欄位清單的資料表 (索引標籤)。  
  
2.  在 [屬性] 視窗中，於 [預設欄位集] 屬性上按一下 [按一下可編輯]。  
  
3.  在 [預設欄位集] 對話方塊中，選取一個或多個欄位。 您可以選擇資料表中的任何欄位，包括量值在內。 按住 SHIFT 鍵選取範圍，或按 CTRL 鍵選取個別欄位。  
  
4.  按一下 [加入] 將它們加入預設欄位集。  
  
5.  使用向上箭號與向下箭號按鈕，指定欄位清單中的順序。 欄位會依欄位集定義的順序加入至報告。  
  
6.  針對活頁簿中的其他資料表重複這些步驟。  
  
## <a name="next-step"></a>下一個步驟  
 您建立預設欄位集之後，可以透過指定預設標籤、預設影像、預設群組行為，或包含相同值的資料列是否群組在一資料列或是個別列出，進一步影響報表設計體驗。 如需詳細資訊，請參閱[設定 Power View 報表的資料表行為屬性 &#40;SSAS 表格式&#41;](../../analysis-services/tabular-models/power-view-configure-table-behavior-properties-for-reports.md)。  
  
  
