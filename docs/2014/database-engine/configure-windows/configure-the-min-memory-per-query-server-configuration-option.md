---
title: 設定 min memory per query 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- memory [SQL Server], queries
- minimum query memory
- queries [SQL Server], memory
- min memory per query option
ms.assetid: ecd3fb79-b4a6-432f-9ef5-530e0d42d5a6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: dfee7265529419aecf2b05831503ed134b93f525
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "58529600"
---
# <a name="configure-the-min-memory-per-query-server-configuration-option"></a>設定 min memory per query 伺服器組態選項
  本主題描述如何設定`min memory per query`中的伺服器組態選項[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]利用[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或[!INCLUDE[tsql](../../includes/tsql-md.md)]。 `min memory per query`選項會指定執行查詢配置的記憶體 （以 kb 為單位） 的最小數量。 例如，如果`min memory per query`設定 2,048 kb，就可以保證查詢至少可以取得這些記憶體量。 預設值為 1,024 KB。 最小值是 512 KB，最大值則是 2,147,483,647 KB (2 GB)。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [限制事項](#Restrictions)  
  
     [建議](#Recommendations)  
  
     [Security](#Security)  
  
-   **使用下列方法設定 min memory per query 選項：**  
  
     [Transact-SQL](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **後續操作：**[設定 min memory per query 選項之後](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Restrictions"></a> 限制事項  
  
-   每個查詢的最小記憶體數量的優先順序高於 [索引建立記憶體選項](configure-the-index-create-memory-server-configuration-option.md)。 若您同時變更了兩個選項，且索引建立記憶體選項小於每個查詢的最小記憶體，您會看到警告訊息，但仍會設定該值。 執行查詢時，您會看到另一個類似的警告。  
  
###  <a name="Recommendations"></a> 建議  
  
-   這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查詢處理器會嘗試判斷要配置給查詢的最佳記憶體數量。 min memory per query 選項可讓系統管理員指定任何單一查詢所接收的最小記憶體數量。 若查詢中含有大量資料的雜湊和排序作業，則這些查詢通常會接收比此值更多的記憶體。 提高 min memory per query 的值也許可以改善一些小型至中型查詢的效能，但這樣做也可能導致競用記憶體資源的情形增加。 每個查詢的最小記憶體選項包含了為進行排序所配置的記憶體。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 權限  
 不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。 以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。 **系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>設定 min memory per query 選項  
  
1.  在 [物件總管] 中，以滑鼠右鍵按一下伺服器，然後選取 **[屬性]**。  
  
2.  按一下 **[記憶體]** 節點。  
  
3.  在 **[每個查詢的最小記憶體]** 方塊中，輸入將為執行查詢而配置的最小記憶體數量 (以 KB 為單位)。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-configure-the-min-memory-per-query-option"></a>設定 min memory per query 選項  
  
1.  連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在標準列中，按一下 **[新增查詢]**。  
  
3.  複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]**。 此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `min memory per query` 選項的值設定為 `3500` KB。  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'min memory per query', 3500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
##  <a name="FollowUp"></a> 後續操作：設定 min memory per query 選項之後  
 設定會立即生效，不需要重新啟動伺服器。  
  
## <a name="see-also"></a>另請參閱  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [設定 index create memory 伺服器組態選項](configure-the-index-create-memory-server-configuration-option.md)  
  
  
