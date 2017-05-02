---
title: "啟動或停止收集組 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- collection sets [SQL Server], stopping
- collection sets [SQL Server], starting
ms.assetid: 48a7b2fe-6bc3-4278-a7ec-1babc1290345
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 91f96d4ac8b7403e0d214625925403950e386dc2
ms.lasthandoff: 04/11/2017

---
# <a name="start-or-stop-a-collection-set"></a>啟動或停止收集組
  此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中啟動或停止收集組。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [限制事項](#Restrictions)  
  
     [必要條件](#Prerequisites)  
  
     [建議](#Recommendations)  
  
     [安全性](#Security)  
  
-   **若要使用下列項目啟動或停止收集組：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Restrictions"></a> 限制事項  
  
-   資料收集器預存程序和目錄檢視儲存在 **msdb** 資料庫。  
  
-   不同於一般預存程序，資料收集器預存程序的參數會具備嚴格的類型，而且不支援資料類型的自動轉換。 如果沒有依照引數描述所指定，以正確的輸入參數資料類型來呼叫這些參數，預存程序會傳回錯誤。  
  
###  <a name="Prerequisites"></a> 必要條件  
  
-   SQL Server Agent 必須已啟動。  
  
###  <a name="Recommendations"></a> 建議  
  
-   若要取得收集組的相關資訊，請查詢 [syscollector_collection_sets](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md) 目錄檢視。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 需要 **dc_operator** 固定資料庫角色中的成員資格。 如果收集組沒有 Proxy 帳戶，就需要 **系統管理員 (sysadmin)** 固定伺服器角色中的成員資格。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-start-a-collection-set"></a>若要啟動收集組  
  
1.  在 [物件總管] 中，依序展開 **[管理]** 節點、 **[資料收集]**和 **[系統資料收集組]**。  
  
2.  以滑鼠右鍵按一下您要啟動的收集組，然後按一下 [啟動資料收集組]****。  
  
     訊息方塊會顯示此動作的結果，而此收集組圖示上的綠色箭頭會指示此收集組已經啟動。  
  
#### <a name="to-stop-a-collection-set"></a>若要停止收集組  
  
1.  在 [物件總管] 中，依序展開 **[管理]** 節點、 **[資料收集]**和 **[系統資料收集組]**。  
  
2.  以滑鼠右鍵按一下您要停止的收集組，然後按一下 [停止資料收集組]****。  
  
     訊息方塊會顯示此動作的結果，而此收集組圖示上的紅色圓圈會指示此收集組已經停止。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-start-a-collection-set"></a>若要啟動收集組  
  
1.  連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在標準列中，按一下 **[新增查詢]**。  
  
3.  將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]**。 此範例使用 [sp_syscollector_start_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql.md) 啟動識別碼為 `1`的收集組。  
  
```tsql  
USE msdb;  
GO  
EXEC sp_syscollector_start_collection_set @collection_set_id = 1;  
```  
  
#### <a name="to-stop-a-collection-set"></a>若要停止收集組  
  
1.  連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在標準列中，按一下 **[新增查詢]**。  
  
3.  將下列範例複製並貼入查詢視窗中，然後按一下 **[執行]**。 此範例使用 [sp_syscollector_stop_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql.md) 停止識別碼為 `1`的收集組。  
  
```tsql  
USE msdb;  
GO  
EXEC sp_syscollector_stop_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料收集器檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [[資料收集]](../../relational-databases/data-collection/data-collection.md)  
  
  
