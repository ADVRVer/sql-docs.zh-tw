---
title: IsEmpty （MDX） |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8b31b884e0f86bf2aebe4859cd1c7a441669e813
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905994"
---
# <a name="isempty-mdx"></a>IsEmpty (MDX)


  傳回評估的運算式是否為空白資料格值。  
  
## <a name="syntax"></a>語法  
  
```  
  
IsEmpty(Value_Expression)   
```  
  
## <a name="arguments"></a>引數  
 *Value_Expression*  
 一般會傳回成員或 Tuple 之資料格座標的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 如果評估的運算式是空的資料格值，則**IsEmpty**函數會傳回**true** 。 否則，此函數會傳回**false**。  
  
> [!NOTE]  
>  成員的預設屬性就是成員的值。  
  
 **IsEmpty**函數是可靠地測試空白儲存格的唯一方式，因為空的資料格值在中[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]有特殊意義。  
  
> [!IMPORTANT]  
>  如果值運算式的評估傳回錯誤，函數會傳回**false**。 例如，屬性參考所參考的是無效或不存在的屬性時，值運算式會傳回錯誤。  
  
 如需有關空的資料格的詳細資訊，請參閱 OLE DB 文件集。  
  
## <a name="example"></a>範例  
 如果 Date 維度 Fiscal 階層上目前成員的 Internet Sales Amount 傳回空資料格，下列範例會傳回 TRUE：  
  
 `WITH MEMBER MEASURES.ISEMPTYDEMO AS`  
  
 `IsEmpty([Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.ISEMPTYDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>另請參閱  
 [使用空白值](../mdx/working-with-empty-values.md)   
 [MDX 函數參考 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
