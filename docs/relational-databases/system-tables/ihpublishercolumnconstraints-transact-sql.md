---
title: IHpublishercolumnconstraints （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublishercolumnconstraints
- IHpublishercolumnconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumnconstraints system table
ms.assetid: d7a41da6-e067-430a-8da2-3f6745b8a4f3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 58ef9c5e68e7d209262ebf43891ba5c1bcc4174f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "67990291"
---
# <a name="ihpublishercolumnconstraints-transact-sql"></a>IHpublishercolumnconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublishercolumnconstraints**系統資料表會將[IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md)系統資料表中非 SQL Server 發行集的資料行，對應至[IHpublisherconstraints](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md)系統資料表中的條件約束。 這份資料表儲存在散發資料庫中。  
  
## <a name="definition"></a>定義  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|使用相關聯的條件約束，識別[IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md)中的資料行。|  
|**publisherconstraint_id**|**int**|從與資料行相關聯的[IHpublisherconstraints](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md)中，識別條件約束。|  
|**indid**|**int**|指出該資料行在已發行資料表中的位置。|  
  
## <a name="see-also"></a>另請參閱  
 [異質資料庫複寫](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [複寫資料表 &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
