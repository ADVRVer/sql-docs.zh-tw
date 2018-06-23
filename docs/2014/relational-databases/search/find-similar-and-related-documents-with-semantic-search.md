---
title: 使用語意搜尋尋找相似及相關的文件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-search
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- semantic search [SQL Server], document similarity queries
ms.assetid: 9f527883-031b-442f-8e95-24bc0151ecbf
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b4158ae5c5647516c309f43bc5fa5e49caed4f5f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36035888"
---
# <a name="find-similar-and-related-documents-with-semantic-search"></a>使用語意搜尋尋找相似及相關的文件
  描述如何在設定進行統計語意索引的資料行中尋找相似或相關的文件或文字值，以及相似或相關程度的詳細資訊。  
  
##  <a name="BasicsQuerySimilar"></a> 尋找相似或相關文件  
  
###  <a name="HowToQuerySimilar"></a> 如何： 尋找相似或相關文件使用 SEMANTICSIMILARITYTABLE  
 若要識別特定資料行中的相似或相關文件，請查詢 [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql) 函數。  
  
 **SEMANTICSIMILARITYTABLE** 會傳回含有零個、一個或多個資料列的資料表，其中所指定資料行中的內容會與所指定文件的語意相似。 您可以在 SELECT 陳述式的 FROM 子句中參考這個資料列集函數，就像是一般資料表名稱一樣。  
  
 您不能跨資料行查詢類似文件。 **SEMANTICSIMILARITYTABLE** 函數只從與來源資料行相同的資料行中擷取結果，而來源資料行是透過 **source_key** 引數進行識別。  
  
 如需 **SEMANTICSIMILARITYTABLE** 函數所需參數及其所傳回結果資料表的詳細資訊，請參閱 [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql)。  
  
> [!IMPORTANT]  
>  您設定為目標的資料行必須已啟用全文檢索和語意索引。  
  
###  <a name="HowToIdentifySimilar"></a> 範例： 尋找類似於其他文件的最上層文件  
 下列範例從 AdventureWorks2012 範例資料庫的 HumanResources.JobCandidate 資料表中擷取類似於 *@CandidateID* 所指定候選人的前 10 個候選人。  
  
```scr  
SELECT TOP(10) KEY_TBL.matched_document_key AS Candidate_ID  
FROM SEMANTICSIMILARITYTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume,  
    @CandidateID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
##  <a name="BasicsQuerySimilarity"></a> 尋找程度的詳細文件相似或相關的資訊  
  
###  <a name="HowToQuerySimilarity"></a> 如何： 尋找程度的詳細文件相似或相關使用 SEMANTICSIMILARITYDETAILSTABLE 資訊  
 若要取得讓文件相似或相關之主要片語的詳細資訊，您可以查詢 [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql) 函數。  
  
 **SEMANTICSIMILARITYDETAILSTABLE** 會傳回含有零個、一個或多個資料列的資料表，表示其內容為語意相似之兩份文件 (來源文件和比對文件) 之間的共同主要片語。 您可以在 SELECT 陳述式的 FROM 子句中參考這個資料列集函數，就像是一般資料表名稱一樣。  
  
 如需 **SEMANTICSIMILARITYDETAILSTABLE** 函數所需參數及其所傳回結果資料表的詳細資訊，請參閱 [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql)。  
  
> [!IMPORTANT]  
>  您設定為目標的資料行必須已啟用全文檢索和語意索引。  
  
###  <a name="HowToSimilarPhrases"></a> 範例： 尋找前文件之間相似的主要片語  
 下列範例從 AdventureWorks2012 範例資料庫的 **HumanResources.JobCandidate** 資料表擷取所指定候選人之間相似度分數最高的 5 個主要片語。  
  
```tsql  
SELECT TOP(5) KEY_TBL.keyphrase, KEY_TBL.score  
FROM SEMANTICSIMILARITYDETAILSTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume, @CandidateID,  
    Resume, @MatchedID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
  
