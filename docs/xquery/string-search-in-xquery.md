---
title: XQuery 中的字串搜尋 |Microsoft Docs
description: 瞭解如何在 XQuery 中查看字串搜尋的範例，以在 XML 檔中搜尋文字。
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- strings [SQL Server], search
- XML [SQL Server], searching text
- searches [SQL Server], XML documents
- XQuery, string search
ms.assetid: edc62024-4c4c-4970-b5fa-2e54a5aca631
author: rothja
ms.author: jroth
ms.openlocfilehash: 33f68a55cb627099150ec14941fe5de81de53fc8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "81388057"
---
# <a name="string-search-in-xquery"></a>XQuery 中的字串搜尋
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  本主題提供範例查詢，以顯示如何搜尋 XML 文件中的文字。  
  
## <a name="examples"></a>範例  
  
### <a name="a-find-feature-descriptions-that-contain-the-word-maintenance-in-the-product-catalog"></a>A. 在產品目錄中尋找包含 "maintenance" 文字的功能描述  
  
```  
SELECT CatalogDescription.query('  
     declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
    for $f in /p1:ProductDescription/p1:Features/*  
     where contains(string($f), "maintenance")  
     return  
           $f ') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 在上一個查詢中， `where` FLOWR 運算式中的會篩選`for`運算式的結果，並只傳回符合**contains （）** 條件的元素。  
  
 以下是結果：  
  
```  
<p1:Maintenance     
      xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
 <p1:NoOfYears>10</p1:NoOfYears>  
 <p1:Description>maintenance contact available through your   
               dealer or any AdventureWorks retail store.</p1:Description>  
</p1:Maintenance>  
```  
  
## <a name="see-also"></a>另請參閱  
 [XML 資料 &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [XQuery 語言參考 &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
