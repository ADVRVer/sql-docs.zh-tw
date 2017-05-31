---
title: "修改唯一的條件約束 | Microsoft Docs"
ms.custom: 
ms.date: 10/12/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying constraints
- UNIQUE constraints [SQL Server], modifying
- constraints [SQL Server], modifying
- constraints [SQL Server], unique
ms.assetid: fddbdc9e-958b-4614-8e88-6ca205d64a4e
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2eb829d6362e39096134906442d6c4c0adf44f2a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/11/2017

---
# <a name="modify-unique-constraints"></a>修改唯一的條件約束
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改唯一條件約束。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [安全性](#Security)  
  
-   **若要使用下列項目來修改唯一條件約束：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 需要資料表的 ALTER 權限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-modify-a-unique-constraint"></a>若要修改唯一條件約束  
  
1.  在 [物件總管] 中，以滑鼠右鍵按一下包含唯一條件約束的資料表，然後選取 [設計]。  
  
2.  在 [資料表設計工具] 功能表中，按一下 [索引/索引鍵]。  
  
3.  在 [索引/索引鍵] 對話方塊的 [選取的主/唯一索引鍵或索引] 底下，選取您想要編輯的條件約束。  
  
4.  完成下表中的動作：  
  
    |若要|請依照下列步驟：|  
    |--------|------------------------|  
    |變更與條件約束有關的資料行|1) 在 [(一般)] 底下的方格中，按一下 [資料行]，然後按一下屬性右邊的省略符號 **(…)**。<br /><br /> 2) 在 [索引資料行] 對話方塊中，指定索引的新資料行或排序次序，同時指定這兩者。|  
    |重新命名條件約束|在 **[識別]**底下的方格中，於 **[名稱]** 方塊中輸入新的名稱。 確定新名稱不會與 [選取的主/唯一索引鍵或索引] 清單中的名稱重複。|  
    |設定叢集選項|在 [資料表設計工具] 底下的方格中，選取 [建立成 CLUSTERED]，然後從下拉式清單中，選擇 [是] 建立叢集索引，或選擇 [否] 建立非叢集索引。 每個資料表只能存在一個叢集索引。 如果叢集索引已經存在這個資料表中，您就必須清除原始索引的這項設定。|  
    |定義填滿因數|在 **[資料表設計工具]**底下的方格中，展開 **[填滿規格]** 類別目錄，然後在 **[填滿因數]** 方塊中輸入 0 到 100 之間的整數。|  
  
5.  在 [檔案]  功能表上，按一下 [儲存] *table name*。  
  
##  <a name="TsqlProcedure"></a> **若要修改唯一條件約束**  
  
 若要使用 Transact-SQL 來修改 UNIQUE 條件約束，您必須先刪除現有的 UNIQUE 條件約束，然後使用新的定義來重新建立。 如需相關資訊，請參閱 [Delete Unique Constraints](../../relational-databases/tables/delete-unique-constraints.md) 及 [Create Unique Constraints](../../relational-databases/tables/create-unique-constraints.md)。  
  
###  <a name="TsqlExample"></a>  

