---
title: MSdbms_datatype （Transact-sql） |Microsoft Docs
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
ms.openlocfilehash: 62efb2fa9bf434af4cb9b237b133d3f705eaa7eb
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890024"
---
# <a name="msdbms_datatype-transact-sql"></a>MSdbms_datatype (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MSdbms_datatype**表包含在異質資料庫複寫中，當做發行者或訂閱者使用之每個支援的資料庫管理系統（DBMS）的原生資料類型完整清單。 此資料表會儲存在**msdb**資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**datatype_id**|**int**|識別每個唯一資料類型。|  
|**dbms_id**|**int**|識別類型所屬的 DBMS。|  
|**type**|**sysname**|資料類型名稱 (原生)。|  
|**createparams**|**int**|用來描述每個資料類型所適用之長度、有效位數和小數位數組合的點陣圖，其中包括：<br /><br /> **0x1** = PRECISION。<br /><br /> **0x2** = SCALE。<br /><br /> **0x4** = 長度。|  
  
## <a name="remarks"></a>備註  
 這份資料表包含 SQL Server 資料類型的項目，因為 SQL Server 的執行個體可以訂閱非 SQL Server 資料庫以及發行到非 SQL Server 訂閱者。  
  
## <a name="see-also"></a>另請參閱  
 [異質資料庫複寫](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [指定 Oracle 發行者的資料類型對應](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [複寫資料表 &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
