---
title: "停用複寫的外部索引鍵條件約束 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- constraints [SQL Server], foreign keys
- foreign keys [SQL Server], disabling constraints
- disabling constraints
ms.assetid: 4211f2fd-d16a-4081-995c-43f1f0827f0b
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a3c5723e388d1844c2c3af4401f87113c2dc2fd8
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="disable-foreign-key-constraints-for-replication"></a>停用複寫的外部索引鍵條件約束
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中停用複寫的外部索引鍵條件約束。 這有助於從舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]發行資料。  
  
> [!NOTE]  
>  如果使用複寫發行資料表，則會自動停用複寫代理程式所執行作業的外部索引鍵條件約束。 當複寫代理程式在訂閱者端執行插入、更新或刪除時，不會檢查條件約束；如果使用者執行插入、更新或刪除，則會檢查條件約束。 停用複製代理程式的條件約束，是因為原本插入、更新或刪除資料時，就已在發行者端檢查過條件約束。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [安全性](#Security)  
  
-   **使用下列方法，停用複寫的外部索引鍵條件約束：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 需要資料表的 ALTER 權限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a>停用複寫的外部索引鍵條件約束  
  
1.  在 **[物件總管]**中，展開您要修改其外部索引鍵條件約束的資料表，然後展開 **[索引鍵]** 資料夾。  
  
2.  以滑鼠右鍵按一下外部索引鍵條件約束，然後按一下 [修改]。  
  
3.  在 **[外部索引鍵關聯性]** 對話方塊中，針對 **[強制複寫]** 選取 **[否]**值。  
  
4.  按一下 [ **關閉**]。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a>停用複寫的外部索引鍵條件約束  
  
1.  若要在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中執行此工作，請卸除外部索引鍵條件約束。 然後加入新的外部索引鍵條件約束，並指定 NOT FOR REPLICATION 選項。  
  
 如需詳細資訊，請參閱 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)。  
  
###  <a name="TsqlExample"></a>  
