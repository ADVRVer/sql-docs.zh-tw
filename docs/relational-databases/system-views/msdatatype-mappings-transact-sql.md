---
title: MSdatatype_mappings （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdatatype_mappings
- MSdatatype_mappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdatatype_mappings view
ms.assetid: 13cdabb3-6e07-4e8d-ae80-4235022ccc7f
author: stevestein
ms.author: sstein
ms.openlocfilehash: ee1a0cc83b55fc265ae2bb490fd9d5e11fd73f22
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68129617"
---
# <a name="msdatatype_mappings-transact-sql"></a>MSdatatype_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSdatatype_mappings**視圖會將 SQL Server 的資料類型對應至非 SQL Server 的資料庫管理系統（DBMS）所使用的資料類型。 此資料表會儲存在**msdb**資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**dbms_name**|**nvarchar(128)**|這是 DBMS 的名稱。 以下是可能的值及其描述。<br /><br /> **MSSQLSERVER**：目的地是 SQL Server 資料庫。<br />**Oracle**：目的地是 oracle 資料庫。<br />**DB2**：目的地是 IBM DB2 資料庫。<br />**Sybase**：目的地是 SYBASE 資料庫。|  
|**sql_type**|**nvarchar(128)**|這是 SQL Server 資料類型。|  
|**dest_type**|**nvarchar(128)**|這是非 SQL Server 資料類型的名稱。|  
|**dest_prec**|**Bigint**|這是非 SQL Server 資料類型的有效位數。|  
|**dest_create_params**|**int**|僅供內部使用。|  
|**dest_nullable**|**bit**|這是指非 SQL Server 資料類型是否支援 NULL 值。|  
  
## <a name="see-also"></a>另請參閱  
 [異質資料庫複寫](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [指定 Oracle 發行者的資料類型對應](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [複寫資料表 &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
