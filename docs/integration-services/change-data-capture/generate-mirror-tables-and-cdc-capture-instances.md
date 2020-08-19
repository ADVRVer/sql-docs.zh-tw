---
description: 產生鏡像資料表和 CDC 擷取執行個體
title: 產生鏡像資料表和 CDC 擷取執行個體 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- mirTab
ms.assetid: 260c1617-eecc-4007-a84d-3c5778ce46b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9f8340ef153f815d3073edaf4f9a13e99e1e9f67
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88394804"
---
# <a name="generate-mirror-tables-and-cdc-capture-instances"></a>產生鏡像資料表和 CDC 擷取執行個體

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  使用 [產生鏡像資料表] 頁面，針對 CDC 執行個體中包含的資料表產生鏡像資料表。  
  
 按一下 **[執行]** ，建立鏡像資料表。 隨即顯示每一個資料表的建立進度，而且會顯示一則訊息，讓您知道每一個鏡像資料表是否已順利完成還是發生錯誤。 如果出現任何錯誤，請按一下 **[詳細資料]** ，查看包含錯誤說明的對話方塊。  
  
 如果有任何資料表建立失敗，您可以選擇繼續或刪除任何失敗的資料表，然後再繼續進行。 當精靈執行完之後，您可以決定是否要在 Oracle 來源資料庫中修正資料表，或者不要在 CDC 執行個體中使用此資料表。 如果您修正此資料表，當您 [Edit Tables](../../integration-services/change-data-capture/edit-tables.md)時可以將它加入。  
  
 按 **[下一步]** ，開啟 [Finish](../../integration-services/change-data-capture/finish.md) 頁面。  
  
## <a name="see-also"></a>另請參閱  
 [如何建立 SQL Server 變更資料庫執行個體](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)  
  
  
