---
description: 資料收集器檢視 (Transact-SQL)
title: " (Transact-sql) 的資料收集器視圖 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- data collector [SQL Server], views
ms.assetid: a005e885-7813-4c7e-b332-b01d9e9d4054
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b35f12b1ff06e417a01fafe6f4de1c012ee8f9fe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482211"
---
# <a name="data-collector-views-transact-sql"></a>資料收集器檢視 (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  資料收集器會提供下列檢視，以便顯示資料收集器組態的相關資訊，例如收集器型別屬性、收集組和收集組項目，以及在收集組執行時取得的執行統計資料。 這些位於 **msdb** 資料庫中的 views 也會提供基礎資料表的抽象層。 這個抽象層會防止他人直接存取資料表，同時允許對資料表進行變更，但不影響任何相關聯的應用程式，藉以強化安全性。  

:::row:::
    :::column:::
        [syscollector_collection_items &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-items-transact-sql.md)
        
        [syscollector_collector_types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collector-types-transact-sql.md)
        
        [syscollector_execution_log &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-execution-log-transact-sql.md)
        
        [syscollector_execution_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-execution-stats-transact-sql.md)
    :::column-end:::
    :::column:::
        [syscollector_collection_sets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)
        
        [syscollector_config_store &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-config-store-transact-sql.md)
        
        [syscollector_execution_log_full &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-execution-log-full-transact-sql.md)
    :::column-end:::
:::row-end:::
  
## <a name="see-also"></a>另請參閱  
 [資料收集](../../relational-databases/data-collection/data-collection.md)   
 [資料收集器預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
