---
title: DrillupMember (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 31981669d5d08e63a853b8daa530b886f9b7dfbe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "62690770"
---
# <a name="drillupmember-mdx"></a>DrillupMember (MDX)


  傳回指定之集合中的成員，而且該成員不是第二個指定集合中成員的下階。  
  
## <a name="syntax"></a>語法  
  
```  
  
DrillupMember(Set_Expression1, Set_Expression2)   
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression1*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *Set_Expression2*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 **DrillupMember**函式會傳回一組的第一個集合中指定子系的第二個集合中成員的成員為基礎的成員。 第一個集合可以是任何維度，但第二個集合只能包含一維集合。 會保留第一個集合中原始成員的順序。 此函數只會包含屬於第一個集合並且也是第二個集合中成員之直接下階的那些成員，來建構集合。 如果第一個集合中成員的直接上階沒有出現在第二個集合，則第一個集合中的該成員會包含在此函數傳回的集合中。 屬於第一個集合並且是在第二個集合中上階成員之前的下階，也會包含在此集合中。  
  
 第一個集合可以包含 Tuple，而非成員。 Tuple 向下鑽研是 OLE DB 的延伸模組，而且會傳回 Tuple 集合而不是傳回成員。  
  
> [!IMPORTANT]  
>  只有在成員是子系或下階的直接上階時，才能向上鑽研。 集合中成員的順序很重要，這兩種向下切入\*和向上切入\*系列的函式。 請考慮使用**Hierarchize**成適當的順序的第一個集合的成員函式。  
  
## <a name="example"></a>範例  
 下列三個範例中，只有第二個集合不相同。 在第一個範例中，第二個集合是 United States。 因此，Colorado 會從結果集中排除。 Colorado 是 United States 的子代。  
  
```  
SELECT DrillUpMember (   
  { [Geography].[Geography].[Country].[Canada]   
   ,[Geography].[Geography].[Country].[United States]   
   ,[Geography].[Geography].[State-Province].[Colorado]   
   ,[Geography].[Geography].[State-Province].[Alberta]   
   ,[Geography].[Geography].[State-Province].[Brunswick]    
 }   
 , {[Geography].[Geography].[Country].[United States]}   
 ) ON 0   
FROM [Adventure Works]  
```  
  
 範例二示範成員順序的重要性。 由於**DrillupMember**只會向上鑽研其後緊接第一個集合中的下階成員，所以不會向上鑽研 Canada 成員。 Canada 與其下階被 United States 及 Colorado 所分隔。 若您重新排序成員，讓 Canada 直接位於 Alberta 之上，則 Alberta 與 Brunswick 都會從資料列集中排除。  
  
```  
SELECT DrillUpMember (   
 {  [Geography].[Geography].[Country].[Canada]   
   ,[Geography].[Geography].[Country].[United States]   
   ,[Geography].[Geography].[State-Province].[Colorado]   
   ,[Geography].[Geography].[State-Province].[Alberta]   
   ,[Geography].[Geography].[State-Province].[Brunswick]    
 }   
 , {[Geography].[Geography].[Country].[Canada]}   
 )   
ON 0   
FROM [Adventure Works]  
```  
  
 範例三顯示如何使用**Hierarchize**可減緩成員順序及向上鑽研 Canada 成員。  
  
```  
SELECT DrillUpMember (   
 Hierarchize   
  (   
   { [Geography].[Geography].[Country].[Canada]   
    ,[Geography].[Geography].[Country].[United States]   
    ,[Geography].[Geography].[State-Province].[Colorado]   
    ,[Geography].[Geography].[State-Province].[Alberta]   
    ,[Geography].[Geography].[State-Province].[Brunswick]    
   }   
  ), {[Geography].[Geography].[Country].[Canada]}   
 )   
ON 0   
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
