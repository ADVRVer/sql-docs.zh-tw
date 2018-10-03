---
title: 檢視預存程序的相依性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], dependencies
- displaying stored procedure dependencies
- viewing stored procedure dependencies
ms.assetid: 6ae0a369-1bc7-4ae4-be89-2b483697cd1f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 14f380f510070da1b8fa77f7f5440640ce37452b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224418"
---
# <a name="view-the-dependencies-of-a-stored-procedure"></a>檢視預存程序的相依性
    
##  <a name="Top"></a> 本主題描述如何檢視預存程序中的相依性[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]利用[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或[!INCLUDE[tsql](../../includes/tsql-md.md)]。  
  
-   **開始之前**  [安全性](#Security)  
  
-   使用 [SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure) **檢視程序的相依性**  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 權限  
 系統函數：`sys.dm_sql_referencing_entities`  
 需要受參考實體的 CONTROL 權限和 sys.dm_sql_referencing_entities 的 SELECT 權限。 當受參考實體為資料分割函數時，便需要資料庫的 CONTROL 權限。 根據預設，SELECT 權限會授與 public。  
  
 系統函數：`sys.dm_sql_referenced_entities`  
 需要 sys.dm_sql_referenced_entities 的 SELECT 權限和參考實體的 VIEW DEFINITION 權限。 根據預設，SELECT 權限會授與 public。 當參考實體為資料庫層級 DDL 觸發程序時，便需要資料庫的 VIEW DEFINITION 權限，或資料庫的 ALTER DATABASE DDL TRIGGER 權限。 當參考實體為伺服器層級 DDL 觸發程序時，便需要伺服器的 VIEW ANY DEFINITION 權限。  
  
 物件目錄檢視：`sys.sql_expression_dependencies`  
 需要資料庫的 VIEW DEFINITION 權限和資料庫之 sys.sql_expression_dependencies 的 SELECT 權限。 根據預設，SELECT 權限只授與 db_owner 固定資料庫角色的成員。 當 SELECT 和 VIEW DEFINITION 權限授與其他使用者時，被授與者就可以檢視資料庫中的所有相依性。  
  
##  <a name="Procedures"></a> 如何檢視預存程序的相依性  
 您可以使用下列其中一項：  
  
-   [Transact-SQL](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
 **在物件總管中檢視程序的相依性**  
  
1.  在物件總管中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。  
  
2.  依序展開 **[資料庫]**、程序所屬的資料庫，以及 **[可程式性]**。  
  
3.  展開 [預存程序]，以滑鼠右鍵按一下程序，然後按一下 [檢視相依性]。  
  
4.  檢視相依於程序的物件清單。  
  
5.  檢視程序所相依的物件清單。  
  
6.  按一下 [確定] 。  
  
###  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 **在查詢編輯器中檢視程序的相依性**  
  
 系統函數：`sys.dm_sql_referencing_entities`  
 此函數用來顯示相依於程序的物件。  
  
1.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。  
  
2.  展開 **[資料庫]**，展開程序所屬的資料庫。  
  
3.  按一下 **[檔案]** 功能表下的 **[新增查詢]** 。  
  
4.  將下列範例複製並貼入查詢編輯器中。 第一個範例會建立 `uspVendorAllInfo` 程序，它會傳回 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 資料庫中的所有供應商名稱，以及他們提供的產品、他們的信用等級，以及是否能聯繫到他們。  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  建立程序之後，第二個範例會使用 sys.dm_sql_referencing_entities 函數顯示相依於程序的物件。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');   
    GO  
  
    ```  
  
 系統函數：`sys.dm_sql_referenced_entities`  
 此函數用來顯示程序所相依的物件。  
  
1.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。  
  
2.  展開 **[資料庫]**，展開程序所屬的資料庫。  
  
3.  按一下 **[檔案]** 功能表下的 **[新增查詢]** 。  
  
4.  將下列範例複製並貼入查詢編輯器中。 第一個範例會建立 `uspVendorAllInfo` 程序，它會傳回 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 資料庫中的所有供應商名稱，以及他們提供的產品、他們的信用等級，以及是否能聯繫到他們。  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  建立程序之後，第二個範例會使用 sys.dm_sql_referenced_entities 函數顯示程序相依的物件。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referenced_schema_name, referenced_entity_name,  
    referenced_minor_name,referenced_minor_id, referenced_class_desc,  
    is_caller_dependent, is_ambiguous  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');  
    GO  
    ```  
  
 物件目錄檢視：`sys.sql_expression_dependencies`  
 此檢視可用來顯示程序相依的物件或相依於程序的物件。  
  
 顯示相依於程序的物件。  
 1.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。  
  
2.  展開 **[資料庫]**，展開程序所屬的資料庫。  
  
3.  按一下 **[檔案]** 功能表下的 **[新增查詢]** 。  
  
4.  將下列範例複製並貼入查詢編輯器中。 第一個範例會建立 `uspVendorAllInfo` 程序，它會傳回 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 資料庫中的所有供應商名稱，以及他們提供的產品、他們的信用等級，以及是否能聯繫到他們。  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  建立程序之後，第二個範例會使用 sys.sql_expression_dependencies 檢視顯示相依於程序的物件。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_SCHEMA_NAME ( referencing_id ) AS referencing_schema_name,  
        OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referenced_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
 顯示程序所相依的物件。  
 1.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。  
  
2.  展開 **[資料庫]**，展開程序所屬的資料庫。  
  
3.  按一下 **[檔案]** 功能表下的 **[新增查詢]** 。  
  
4.  將下列範例複製並貼入查詢編輯器中。 第一個範例會建立 `uspVendorAllInfo` 程序，它會傳回 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 資料庫中的所有供應商名稱，以及他們提供的產品、他們的信用等級，以及是否能聯繫到他們。  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  建立程序之後，第二個範例會使用 sys.sql_expression_dependencies 檢視顯示程序相依的物件。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referencing_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [重新命名預存程序](rename-a-stored-procedure.md)   
 [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)   
 [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)   
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
  
