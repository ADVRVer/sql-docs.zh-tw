---
title: "檢視或變更資料及記錄檔的預設位置 | Microsoft Docs"
ms.custom: 
ms.date: 06/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: e1afb149a8b3348660e4e21c879598436eaaedfa
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files"></a>檢視或變更資料及記錄檔的預設位置
  
 保護資料檔和記錄檔的最佳作法是確定它們受到存取控制清單 (ACL) 所保護。 在建立這些檔案的根目錄下設定 ACL。  
 
  
## <a name="view-or-change-the-default-locations-for-database-files"></a>檢視或變更資料庫檔案的預設位置  
  
1.  在物件總管中，以滑鼠右鍵按一下伺服器，然後按一下 [屬性]。  
  
2.  在該 [屬性] 頁面的左面板中，按一下 [資料庫設定] 索引標籤。  
  
3.  在 **[資料庫預設位置]**中，您可以檢視新資料檔和新記錄檔的目前預設位置。 若要變更預設位置，在 **[資料]** 或 **[記錄]** 欄位中輸入新的預設路徑名稱，或按一下 [瀏覽] 按鈕來尋找並選取路徑名稱。  
  
>**注意：** 變更預設位置之後，您必須停止並啟動 SQL Server 服務，才能完成變更。  
  
## <a name="see-also"></a>另請參閱  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [建立資料庫](../../relational-databases/databases/create-a-database.md)  
  
  
