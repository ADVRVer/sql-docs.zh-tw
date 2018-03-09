---
title: "SET STATISTICS XML (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_STATISTICS_XML_TSQL
- SET STATISTICS XML
dev_langs:
- TSQL
helpviewer_keywords:
- statistical information [SQL Server], statement processing
- STATISTICS XML option
- SET STATISTICS XML statement
- statements [SQL Server], statistical information
- XML [SQL Server], statement execution information
ms.assetid: 2b6d4c5a-a7f5-4dd1-b10a-7632265b1af7
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 99ef0199258d6d4a87a041979dd0f75bbc6b835f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="set-statistics-xml-transact-sql"></a>SET STATISTICS XML (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  使 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，且會以妥善定義的 XML 文件格式來產生陳述式執行狀況的詳細資料。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
SET STATISTICS XML { ON | OFF }  
```  
  
## <a name="remarks"></a>備註  
 SET STATISTICS XML 的設定是在執行階段進行設定，而不是在剖析階段進行設定。  
  
 當 SET STATISTICS XML 是 ON 時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會在執行每個陳述式之後，傳回它的執行資訊。 在這個選項設為 ON 之後，會傳回所有後續 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的相關資訊，直到這個選項設為 OFF 為止。 請注意，SET STATISTICS XML 不必是批次中的唯一陳述式。  
  
 SET STATISTICS XML 會傳回做為輸出**nvarchar （max)**對於應用程式，例如**sqlcmd**公用程式，其中 XML 輸出後續可由其他工具來顯示和處理查詢計劃資訊。  
  
 SET STATISTICS XML 會將資訊當作一組 XML 文件傳回。 SET STATISTICS XML ON 陳述式之後的每個陳述式都會反映在單一文件的輸出中。 每份文件都包含陳述式的文字，後面接著執行步驟的詳細資料。 輸出會顯示各種執行階段資訊，如成本、存取的索引、執行的作業類型、聯結順序、實體作業的執行次數、每個實體運算子所產生的資料列數等。  
  
 在安裝期間，會將包含 SET STATISTICS XML 的 XML 輸出之 XML 結構描述的文件，複製到安裝了 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之電腦的本機目錄中。 您可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝檔所在的磁碟機中找到它，位置如下：  
  
 \Microsoft SQL Server\100\Tools\Binn\schemas\sqlserver\2004\07\showplan\showplanxml.xsd  
  
 顯示計畫結構描述也可以在找到[這個網站](http://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409)。  
  
 SET STATISTICS PROFILE 和 SET STATISTICS XML 彼此是對應的項目。 前者會產生文字輸出；後者會產生 XML 輸出。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 未來的版本中，只會透過 SET STATISTICS XML 陳述式來顯示新的查詢執行計畫資訊，不會使用 SET STATISTICS PROFILE 陳述式。  
  
> [!NOTE]  
>  如果**包括實際執行計畫**中選取[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，這個 SET 選項不會產生 XML 執行程序表輸出。 清除**包括實際執行計畫**按鈕才能使用這個 SET 選項。  
  
## <a name="permissions"></a>Permissions  
 若要使用 SET STATISTICS XML 和檢視輸出，使用者必須有下列權限：  
  
-   執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的適當許可權。  
  
-   包含 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式所參考的物件之所有資料庫的 SHOWPLAN 權限。  
  
 如果 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式不會產生 STATISTICS XML 結果集，就只需要執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的適當權限。 如果 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式會產生 STATISTICS XML 結果集，檢查 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式執行權限和 SHOWPLAN 權限都必須成功，否則，便會中止執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，且不會產生任何顯示計畫資訊。  
  
## <a name="examples"></a>範例  
 隨後的兩個陳述式使用 SET STATISTICS XML 設定來顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 分析及最佳化查詢中使用索引的方法。 第一個查詢在索引資料行的 WHERE 子句中，使用等於 (=) 比較運算子。 第二個查詢在 WHERE 子句中使用 LIKE 運算子。 這會強制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 利用叢集索引掃描來尋找符合 WHERE 子句條件的資料。 中的值**EstimateRows**和**EstimatedTotalSubtreeCost**屬性會指出它的處理速度，並使用較少的資源比第一個索引查詢非索引查詢。  
  
```  
USE AdventureWorks2012;  
GO  
SET STATISTICS XML ON;  
GO  
-- First query.  
SELECT BusinessEntityID   
FROM HumanResources.Employee  
WHERE NationalIDNumber = '509647174';  
GO  
-- Second query.  
SELECT BusinessEntityID, JobTitle   
FROM HumanResources.Employee  
WHERE JobTitle LIKE 'Production%';  
GO  
SET STATISTICS XML OFF;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [SET SHOWPLAN_XML &#40;Transact-SQL&#41;](../../t-sql/statements/set-showplan-xml-transact-sql.md)   
 [sqlcmd 公用程式](../../tools/sqlcmd-utility.md)  
  
  
