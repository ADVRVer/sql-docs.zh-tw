---
title: "設定警示以便向原則管理員通知原則失敗 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原則式管理, 設定警示"
ms.assetid: e8e60159-d5b0-49d5-91f3-af8e9cb994c1
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# 設定警示以便向原則管理員通知原則失敗
  當原則式管理原則在其中一種自動評估模式中執行時，如果發生原則違規，系統就會在事件記錄檔中寫入一則訊息。 若要在這則訊息寫入事件記錄檔時收到通知，您可以建立偵測訊息並執行動作的警示。 此警示應該會偵測到下表所列的訊息。  
  
|執行模式|訊息編號|  
|--------------------|--------------------|  
|變更時 - 避免<br /><br /> (若為自動)|34050|  
|變更時 - 避免<br /><br /> (若為視需要)|34051|  
|按排程時間|34052|  
|變更時|34053|  
  
 若要設定警示來回應原則式管理錯誤訊息，請參閱下列主題：  
  
-   [建立操作員](../../ssms/agent/create-an-operator.md)  
  
-   [使用錯誤號碼建立警示](../../ssms/agent/create-an-alert-using-an-error-number.md)  
  
-   [指派警示給操作員](../../ssms/agent/assign-alerts-to-an-operator.md)  
  
## Permissions  
 視需要評估原則時，這些原則就會在使用者的安全性內容中執行。 若要寫入錯誤記錄檔，使用者必須擁有 ALTER TRACE 權限或屬於系統管理員 (sysadmin) 固定伺服器角色的成員。 擁有較低權限之使用者所評估的原則不會寫入事件記錄檔，而且不會引發警示。  
  
 自動執行模式會以系統管理員 (sysadmin) 角色成員的身分執行。 這樣可讓原則寫入錯誤記錄檔並且引發警示。  
  
## 關於警示的其他考量  
 請注意下列關於警示的其他考量：  
  
-   系統只會針對啟用的原則引發警示。 由於無法啟用 [視需要] 原則，因此無法針對視需要執行的原則引發警示。  
  
-   如果您想要採取的動作包含傳送電子郵件訊息，就必須設定郵件帳戶。 我們建議您使用 Database Mail。 如需設定 Database Mail 的詳細資訊，請參閱[建立 Database Mail 帳戶](../../relational-databases/database-mail/create-a-database-mail-account.md)。  
  
  