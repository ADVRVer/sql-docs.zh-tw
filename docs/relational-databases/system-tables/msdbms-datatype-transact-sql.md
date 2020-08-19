---
description: MSdbms_datatype (Transact-SQL)
title: MSdbms_datatype (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdbms_datatype
- MSdbms_datatype_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_datatype system table
ms.assetid: 606168cc-79a8-442f-ab43-936f8f884d72
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3fcda5b5d0283f764fa2347b51d8f34dfb4cc53e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419112"
---
# <a name="msdbms_datatype-transact-sql"></a>MSdbms_datatype (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MSdbms_datatype**資料表包含在每個支援的資料庫管理系統上的原生資料類型完整清單 (DBMS) 用來作為異質資料庫複寫中的「發行者」或「訂閱者」。 此資料表儲存在 **msdb** 資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**datatype_id**|**int**|識別每個唯一資料類型。|  
|**dbms_id**|**int**|識別類型所屬的 DBMS。|  
|**type**|**sysname**|資料類型名稱 (原生)。|  
|**createparams**|**int**|用來描述每個資料類型所適用之長度、有效位數和小數位數組合的點陣圖，其中包括：<br /><br /> **0x1** = 有效位數。<br /><br /> **0x2** = 小數位數。<br /><br /> **0x4** = 長度。|  
  
## <a name="remarks"></a>備註  
 這份資料表包含 SQL Server 資料類型的項目，因為 SQL Server 的執行個體可以訂閱非 SQL Server 資料庫以及發行到非 SQL Server 訂閱者。  
  
## <a name="see-also"></a>另請參閱  
 [異質資料庫複寫](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [指定 Oracle 發行者的資料類型對應](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [複寫資料表 &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
