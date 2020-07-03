---
title: IHpublishercolumnindexes （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublishercolumnindexes
- IHpublishercolumnindexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumnindexes system table
ms.assetid: 95b95a1d-b502-4838-825f-82a456487e25
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b1a5a045bb2e1024a9ccaf953621ea0e3c926adf
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890270"
---
# <a name="ihpublishercolumnindexes-transact-sql"></a>IHpublishercolumnindexes (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **IHpublishercolumnindexes**系統資料表會將[IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md)系統資料表中非 SQL Server 發行集的資料行，對應至[IHpublisherindexes](../../relational-databases/system-tables/ihpublisherindexes-transact-sql.md)系統資料表中的索引。 這份資料表儲存在散發資料庫中。  
  
## <a name="definition"></a>定義  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|使用相關聯的索引，識別[IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md)中的資料行。|  
|**publisherindex_id**|**int**|從與資料行相關聯的[IHpublisherindexes](../../relational-databases/system-tables/ihpublisherindexes-transact-sql.md)資料表中，識別索引。|  
|**indid**|**int**|指出該資料行在已發行資料表中的位置。|  
  
## <a name="see-also"></a>另請參閱  
 [異質資料庫複寫](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [複寫資料表 &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
