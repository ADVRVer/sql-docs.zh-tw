---
title: 建立工作階段範圍導出成員 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CREATE MEMBER statement
- session-scoped calculated members [MDX]
ms.assetid: 2875ed89-2c26-4645-8ed9-8848479d110f
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 79e6466c7f514b3453f8840a72dc0028a215259b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249858"
---
# <a name="creating-session-scoped-calculated-members-mdx"></a>建立工作階段範圍導出成員 (MDX)
  若要建立可在整個多維度運算式 (MDX) 工作階段取得的導出成員，您可以使用 [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member) 陳述式。 使用 CREATE MEMBER 陳述式建立的導出成員，直到 MDX 工作階段結束後才會移除。  
  
 如同本主題所討論，CREATE MEMBER 陳述式的語法直接且使用簡單。  
  
> [!NOTE]  
>  如需建立導出成員的詳細資訊，請參閱[在 MDX 中建立導出成員 &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md)。  
  
## <a name="create-member-syntax"></a>CREATE MEMBER 語法  
 使用以下語法將 CREATE MEMBER 陳述式加入 MDX 陳述式：  
  
```  
CREATE [SESSION] MEMBER [<cube-name>.]<fully-qualified-member-name> AS <expression> [,<property-definition-list>]  
<cube name> ::= CURRENTCUBE | <Cube Name>  
<property-definition-list> ::= <property-definition>  
  | <property-definition>, <property-definition-list>  
<property-definition> ::= <property-identifier> = <property-value>  
<property-identifier> ::= VISIBLE | SOLVEORDER | SOLVE_ORDER | FORMAT_STRING | NON_EMPTY_BEHAVIOR <ole db member properties>  
```  
  
 在 CREATE MEMBER 陳述式的語法中， `fully-qualified-member-name` 值是導出成員的完整名稱。 完整名稱包括與導出成員相關的維度或層級。 `expression` 值會在評估過運算式後，傳回導出成員的值。  
  
## <a name="create-member-example"></a>CREATE MEMBER 範例  
 以下範例使用 CREATE MEMBER 陳述式來建立 `LastFourStores` 導出成員。 此導出成員會傳回最後四間商店銷售的單位量總和，而且將可在 Cube 的整個工作階段中使用。  
  
```  
Create Session Member [Store].[Measures].LastFourStores as   
sum(([Stores].[ByLocation].Lag(3) :  
[Stores].[ByLocation].NextMember), [Measures].[Units Sold])  
```  
  
## <a name="see-also"></a>另請參閱  
 [建立查詢範圍導出成員&#40;MDX&#41;](mdx-calculated-members-query-scoped-calculated-members.md)  
  
  
