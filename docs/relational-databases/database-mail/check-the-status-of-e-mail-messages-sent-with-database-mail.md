---
description: 檢查使用 Database Mail 傳送之電子郵件訊息的狀態
title: 使用 Database Mail 所傳送電子郵件訊息的狀態
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- e-mail [SQL Server], status information
- mail [SQL Server], status information
- Database Mail [SQL Server], message status
- status information [Database Mail]
ms.assetid: eb290f24-b52f-46bc-84eb-595afee6a5f3
author: stevestein
ms.author: sstein
ms.custom: seo-dt-2019
ms.openlocfilehash: 245a50951896f923165e011fc51c09abd00f96e4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421242"
---
# <a name="check-the-status-of-e-mail-messages-sent-with-database-mail"></a>檢查使用 Database Mail 傳送之電子郵件訊息的狀態
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  本主題描述如何在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]來檢查透過 Database Mail 傳送之電子郵件訊息的狀態。  
  
-   **開始之前：**  
  
-   **若要檢視使用 Database Mail 傳送之電子郵件的狀態，請使用：**  [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> 開始之前  
 Database Mail 會保留外寄電子郵件訊息的副本，並在 **msdb**資料庫的 **sysmail_allitems**、 **sysmail_sentitems**、 **sysmail_unsentitems** 、 **sysmail_faileditems** 檢視中顯示它們。 Database Mail 外部程式會記錄活動，並透過「Windows 應用程式事件記錄檔」和 **msdb** 資料庫中的 **sysmail_event_log** 檢視來顯示記錄檔。 若要檢查電子郵件訊息的狀態，請對此檢視執行查詢。 電子郵件訊息狀態可為下列四種之一： **「已傳送」**、 **「未傳送」**、 **「正在重試」** 及 **「失敗」**。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> 使用 Transact-SQL  
 **若要檢視使用 Database Mail 傳送之電子郵件的狀態**  
  
1.  從 **sysmail_allitems** 資料表進行選取，按照 **mailitem_id** 或 **sent_status**指定所需的訊息。  
  
2.  若要檢查外部程式為電子郵件訊息所傳回的狀態，請將 **sysmail_allitems** 聯結到 **sysmail_event_log** 檢視的 **mailitem_id** 資料行，如下節所示。  
  
     依預設，外部程式不會記錄已成功傳送的訊息之相關資訊。 若要記錄所有訊息，請使用 **[Database Mail 組態精靈]** 的 **[設定系統參數]** 頁面，將記錄層級設為詳細資訊。  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> 範例 &#40;Transact-SQL&#41;  
 以下範例列出任何外部程式無法順利傳送而傳送至 `danw` 的電子郵件訊息相關資訊。 此陳述式會列出外部程式無法傳送之訊息的主旨、日期和時間，以及 Database Mail 記錄檔中的錯誤訊息。  
  
```  
USE msdb ;  
GO  
  
-- Show the subject, the time that the mail item row was last  
-- modified, and the log information.  
-- Join sysmail_faileditems to sysmail_event_log   
-- on the mailitem_id column.  
-- In the WHERE clause list items where danw was in the recipients,  
-- copy_recipients, or blind_copy_recipients.  
-- These are the items that would have been sent  
-- to danw.  
  
SELECT items.subject,  
    items.last_mod_date  
    ,l.description FROM dbo.sysmail_faileditems as items  
INNER JOIN dbo.sysmail_event_log AS l  
    ON items.mailitem_id = l.mailitem_id  
WHERE items.recipients LIKE '%danw%'    
    OR items.copy_recipients LIKE '%danw%'   
    OR items.blind_copy_recipients LIKE '%danw%'  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [Database Mail 記錄與稽核](../../relational-databases/database-mail/database-mail-log-and-audits.md)  
  
  
