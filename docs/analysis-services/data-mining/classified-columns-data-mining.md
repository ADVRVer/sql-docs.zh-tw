---
title: 分類資料行 （資料採礦） |Microsoft 文件
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b014f82376b15d9d29834103d8827bf31231ef90
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2018
---
# <a name="classified-columns-data-mining"></a>分類資料行 (資料採礦)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  當您定義分類資料行時，您可以建立目前資料行與採礦結構中另一個資料行之間的關聯性。 您指定為分類資料行之採礦結構資料行中的資料包含類別目錄的資訊，該資訊描述採礦結構中另一個資料行的值。  
  
 例如，假設您有兩個具有數值資料的資料行：其中一個資料行為 [Yearly Purchases]，包含每個客戶在特定日曆年度的每年總購買量；另一個資料行為 [Standard Deviations]，包含這些值的標準差。 在本例中，您可以將 [Yearly Purchases] 資料行指定為分類資料行，讓模型能夠在分析中使用此關聯性。  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中提供的演算法不支援使用分類資料行；此功能是為了用來建立自訂演算法所提供。  
  
## <a name="defining-a-classified-column"></a>定義分類資料行  
 分類資料行的資料類型必須為 **Long** 或 **Double**。  
  
 下列清單描述 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 支援的分類資料行之內容類型。  
  
 **PROBABILITY**  
 資料行中的值是關聯值的機率，且是介於 0 和 1 之間的數字。  
  
 **VARIANCE**  
 資料行中的值是關聯值的變異數。  
  
 **STDEV**  
 資料行中的值是關聯值的標準差。  
  
 **PROBABILITY_VARIANCE**  
 資料行中的值是關聯值之機率的變異數。  
  
 **PROBABILITY_STDEV**  
 資料行中的值是關聯值之機率的標準差。  
  
 **SUPPORT**  
 資料行中的值是關聯值的加權或案例複寫因數。  
  
## <a name="see-also"></a>另請參閱  
 [內容類型 & #40; 資料採礦 & #41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [採礦結構 & #40;Analysis Services-資料採礦 & #41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [資料類型 & #40; 資料採礦 & #41;](../../analysis-services/data-mining/data-types-data-mining.md)  
  
  
