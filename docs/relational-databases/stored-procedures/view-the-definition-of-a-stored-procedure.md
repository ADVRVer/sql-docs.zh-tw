---
title: "檢視預存程序的定義 | Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-stored-Procs
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedures [SQL Server], viewing
- definition of stored procedure
- viewing stored procedures
- displaying stored procedures
ms.assetid: 93318587-a0c5-4788-946f-3b5dc8372ea9
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: d05c919b5d532434c33c269d1c287871ff818ac9
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2018
---
# <a name="view-the-definition-of-a-stored-procedure"></a>檢視預存程序的定義
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
    
##  <a name="Top"></a> 您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中使用 [物件總管] 功能表選項，或在查詢編輯器中使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]，檢視預存程序的定義。 本主題描述如何在 [物件總管] 中，以及透過系統預存程序、系統函數和查詢編輯器中的物件目錄檢視，來檢視程序的定義。  
  
-   **開始之前**  [安全性](#Security)  
  
-   **To view the definition of a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 權限  
 系統預存程序： **sp_helptext**  
 需要 **public** 角色的成員資格。 系統物件定義是公開顯示的。 凡具有 ALTER、CONTROL、TAKE OWNERSHIP 或 VIEW DEFINITION 任一權限的物件擁有者或被授與者，都看得到使用者物件的定義。  
  
 系統函數： **OBJECT_DEFINITION**  
 系統物件定義是公開顯示的。 凡具有 ALTER、CONTROL、TAKE OWNERSHIP 或 VIEW DEFINITION 任一權限的物件擁有者或被授與者，都看得到使用者物件的定義。 **db_owner**、 **db_ddladmin**和 **db_securityadmin** 固定資料庫角色的成員隱含地擁有這些權限。  
  
 物件目錄檢視： **sys.sql_modules**  
 目錄檢視內中繼資料的可見性會限制在使用者所擁有的安全性實體，或已授與使用者某些權限的安全性實體。 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
##  <a name="Procedures"></a> 如何檢視預存程序的定義  
 您可以使用下列其中一項：  
  
-   [Transact-SQL](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
 **在物件總管中檢視程序的定義**  
  
1.  在物件總管中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體，然後展開該執行個體。  
  
2.  依序展開 [資料庫] 、程序所屬的資料庫，以及 [可程式性] 。  
  
3.  展開 **[預存程序]**，以滑鼠右鍵按一下程序，然後按一下 **[產生預存程序的指令碼為]**，再按一下下列其中一個選項： **[CREATE 至]**、 **[ALTER 至]**或 **[DROP 並 CREATE 至]**。  
  
4.  選取 **[新增查詢編輯器視窗]**。 這會顯示程序定義。  
  
###  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 **在查詢編輯器中檢視程序的定義**  
  
 系統預存程序： **sp_helptext**  
 1.  在 [物件總管] 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。  
  
2.  在工具列上，按一下 **[新增查詢]**。  
  
3.  在查詢視窗中，輸入下列使用 **sp_helptext** 系統預存程序的陳述式。 請變更資料庫名稱和預存程序名稱，使其參考您需要的資料庫和預存程序。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_helptext N'AdventureWorks2012.dbo.uspLogError';  
    ```  
  
 系統函數： **OBJECT_DEFINITION**  
 1.  在 [物件總管] 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。  
  
2.  在工具列上，按一下 **[新增查詢]**。  
  
3.  在查詢視窗中，輸入下列使用 **OBJECT_DEFINITION** 系統函數的陳述式。 請變更資料庫名稱和預存程序名稱，使其參考您需要的資料庫和預存程序。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
 物件目錄檢視： **sys.sql_modules**  
 1.  在 [物件總管] 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。  
  
2.  在工具列上，按一下 **[新增查詢]**。  
  
3.  在查詢視窗中，輸入下列使用 **sys.sql_modules** 目錄檢視的陳述式。 請變更資料庫名稱和預存程序名稱，使其參考您需要的資料庫和預存程序。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition  
    FROM sys.sql_modules  
    WHERE object_id = (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [建立預存程序](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [修改預存程序](../../relational-databases/stored-procedures/modify-a-stored-procedure.md)   
 [刪除預存程序](../../relational-databases/stored-procedures/delete-a-stored-procedure.md)   
 [重新命名預存程序](../../relational-databases/stored-procedures/rename-a-stored-procedure.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sp_helptext &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [OBJECT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/object-id-transact-sql.md)  
  
  
