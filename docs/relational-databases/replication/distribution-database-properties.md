---
title: "散發資料庫屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.configdistwizard.distdbproperties.f1"
helpviewer_keywords: 
  - "散發資料庫屬性對話方塊"
ms.assetid: 0f404ab9-1237-4936-8df5-888baab6a245
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# 散發資料庫屬性
  **[散發資料庫屬性]** 對話方塊可讓您檢視許多屬性，並設定資料庫的交易保留期限和記錄保留期限。  
  
## 選項  
 **名稱**  
 散發資料庫的名稱，預設為「distribution」(唯讀)。  
  
 **檔案位置**  
 資料庫檔案和記錄檔的位置 (唯讀)。  
  
 **交易保留期限**  
 又稱為散發保留期限。 交易的儲存時間長度，適用於異動複寫。 如需詳細資訊，請參閱 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)。  
  
 **記錄保留期限**  
 記錄中繼資料的儲存時間長度，適用於所有類型的複寫。  
  
 **佇列讀取器代理程式安全性**  
 佇列讀取器代理程式會用於具有佇列更新訂閱的異動複寫。 如果您在新增發行集精靈的 **[發行集類型]** 頁面上選取 **[具更新訂閱的交易式發行集]** ，則會自動建立佇列讀取器代理程式。 按一下 **[安全性設定]** ，即可變更執行代理程式和連接散發者的帳戶。  
  
 您也可以藉由選取建立佇列讀取器代理程式 **建立佇列讀取器代理程式** 本頁 （如果尚未建立代理程式，此選項會停用）。  
  
 有兩個地方可以指定佇列讀取器代理程式的其他連接資訊：  
  
-   代理程式會使用 **[發行者屬性]** 對話方塊中指定的認證來連接發行者，該對話方塊可以從 **[散發者屬性]** 對話方塊的 **[發行者]** 頁面存取。  
  
-   代理程式會使用新增訂閱精靈中為散發代理程式指定的認證，來連接訂閱者。  
  
 如需詳細資訊，請參閱  \\[複寫代理程式安全性模型](../Topic/Replication%20Agent%20Security%20Model.md)。  
  
## 另請參閱  
 [設定散發](../../relational-databases/replication/configure-distribution.md)   
 [建立提取訂閱](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  