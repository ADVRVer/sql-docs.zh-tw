---
description: 使用預存程序 (MDX)
title: 使用預存程式 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2c9bd8f20ffae61656dd30f139ce12665ff57f4e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476970"
---
# <a name="using-stored-procedures-mdx"></a>使用預存程序 (MDX)


  您可以擴充 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 和多維度運算式 (MDX) 的功能，其方式是撰寫 .NET 預存程序或使用者定義函數。 如需詳細資訊，請參閱 [ADOMD.NET 伺服器程式設計](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
 當您要參考或呼叫預存程序時，必須指定函數的名稱，並在後面加上括號。 您可以在括號中指定稱為引數的運算式，它會提供要傳送給參數的資料。 當您呼叫函數時，必須提供所有參數的引數值，而指定引數值的順序必須跟使用者自訂函數中定義參數的順序相同。  
  
 下列範例查詢假設您在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 伺服器上已註冊一個名為 SampleAssembly 的組件：  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
> [!NOTE]  
>  *預存* 程式是用於 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 這些類型函數的術語。 舊版的會將 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 這些類型的函 *式稱為使用者定義函數*。  
  
## <a name="types-of-stored-procedures"></a>預存程序類型  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 支援 COM 及 CLR 兩種組件。 因為 CLR 組件具備進階的安全性，所以建議使用 CLR 組件。 如果伺服器上已安裝 Microsoft Office Excel，還可以使用 Excel 函數。  
  
> [!NOTE]  
>  Microsoft Visual Basic for Applications (VBA) COM 組件會自動註冊。  
  
## <a name="see-also"></a>另請參閱  
 [函數 &#40;MDX 語法&#41;](../mdx/functions-mdx-syntax.md)  
  
  
