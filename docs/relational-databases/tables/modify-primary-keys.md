---
title: "修改主索引鍵 | Microsoft Docs"
ms.custom: 
ms.date: 07/25/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying primary keys
- primary keys [SQL Server], modifying
ms.assetid: 8e2a15ba-1cd1-4408-b860-16c3ee37d635
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8e3c601f497bd6abf4a27a6ce8dd5f0762687526
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="modify-primary-keys"></a>修改主索引鍵
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改主索引鍵。 您可以透過變更資料行順序、索引名稱、叢集選項或填滿因數，修改資料表的主索引鍵。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [安全性](#Security)  
  
-   **若要使用下列項目來修改主索引鍵：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 需要資料表的 ALTER 權限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-modify-a-primary-key"></a>若要修改主索引鍵  
  
1.  針對您想要修改其主索引鍵的資料表開啟 [資料表設計工具]，在 [資料表設計工具] 中按一下滑鼠右鍵，然後從捷徑功能表選擇 [索引/索引鍵]。  
  
2.  在 [索引/索引鍵] 對話方塊中，從 [選取的主索引鍵/唯一索引鍵或索引] 清單中選取主索引鍵索引。  
  
3.  完成下表中的動作：  
  
    |若要|請依照下列步驟：|  
    |--------|------------------------|  
    |重新命名主索引鍵|在 [ **名稱** ] 方塊中輸入新的名稱。 確定新名稱不會與 [選取的主索引鍵/唯一索引鍵或索引] 清單中的名稱重複。|  
    |設定叢集選項|若要建立主索引鍵的叢集索引，請選取 [建立成 CLUSTERED]，然後從下拉式清單方塊中選取選項。 每個資料表只能存在一個叢集索引。 如果您的索引無法使用此選項，則必須先清除現有叢集索引的這個設定。<br /><br /> 如果沒有選取此選項，就會建立唯一非叢集索引。|  
    |定義填滿因數|展開 **[填滿規格]** 類別目錄，然後在 **[填滿因數]** 方塊中輸入 0 到 100 的整數。 如需填滿因數的詳細資訊以及使用方法，請參閱 [指定索引的填滿因素](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)。|  
    |變更資料行順序|選取 [資料行]，然後按一下屬性右邊的省略符號 **(…)**。 在  **[索引資料行]** 對話方塊中，從主索引鍵移除資料行。 然後將資料行以所要的順序加回去。 若要從索引鍵移除資料行，只要從 **[資料行]** 名稱清單中移除資料行名稱即可。|  
  
4.  在 [檔案]  功能表上，按一下 [儲存] *table name*。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 **若要修改主索引鍵**  
  
 若要使用 Transact-SQL 來修改 PRIMARY KEY 條件約束，您必須先刪除現有的 PRIMARY KEY 條件約束，然後以新的定義來重新建立。 如需相關資訊，請參閱 [Delete Primary Keys](../../relational-databases/tables/delete-primary-keys.md) 及 [Create Primary Keys](../../relational-databases/tables/create-primary-keys.md)。  
  
###  <a name="TsqlExample"></a>  

