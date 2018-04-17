---
title: （除法）(DMX) |Microsoft 文件
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- / (divide)
- divide operator (/)
ms.assetid: 7afc06cd-054b-48c3-9c3c-9a0c17d15e63
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a972760985e93f61ffa813043ad6c4e58f7d1a28
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2018
---
# <a name="divide-dmx"></a>（除法）(DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  執行算術運算，將一個數字除以另一個數字。  
  
## <a name="syntax"></a>語法  
  
```  
  
Dividend / Divisor  
```  
  
#### <a name="parameters"></a>參數  
 *被除數*  
 有效的資料採礦延伸模組 (DMX) 運算式，會傳回數值。  
  
 *除數*  
 傳回數值的有效 DMX 運算式。  
  
## <a name="return-value"></a>傳回值  
 具有較高優先順序之參數資料類型的值。  
  
## <a name="remarks"></a>備註  
 這個運算子傳回的值是第一個運算式除以第二個運算式的商數。  
  
 兩個運算式的資料類型必須相同，或者其中一個運算式必須可以用隱含方式轉換為另一個運算式的資料類型。 如果除數評估為 Null 值，運算子就會引發錯誤。 如果除數與被除數都評估為 Null 值，運算子就會傳回 Null 值。  
  
## <a name="see-also"></a>請參閱  
 [算術運算子 &#40; DMX &#41;](../dmx/operators-arithmetic.md)   
 [資料採礦延伸模組 &#40; DMX &#41;運算子參考](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [運算子 &#40; DMX &#41;](../dmx/operators-dmx.md)   
 [除以 &#40;SSIS 運算式 &#41;](../integration-services/expressions/divide-ssis-expression.md)   
 [&#40; 除以 &#41;&#40;TRANSACT-SQL &#41;](../t-sql/language-elements/divide-transact-sql.md)  
  
  
