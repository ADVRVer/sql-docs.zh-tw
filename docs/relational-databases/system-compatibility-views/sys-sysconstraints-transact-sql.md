---
title: "sys.sysconstraints (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysconstraints
- sys.sysconstraints
- sysconstraints_TSQL
- sys.sysconstraints_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.sysconstraints compatibility view
- sysconstraints system table
ms.assetid: f2b2e2ad-ba24-48a1-913c-8ee4e0895dc4
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 99b213b6b385a1551dda2daeac21c856b70d0284
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2017
---
# <a name="syssysconstraints-transact-sql"></a>sys.sysconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  包含條件約束到擁有資料庫條件約束之物件的對應。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**constid**|**int**|條件約束編號。|  
|**id**|**int**|擁有條件約束的資料表識別碼。|  
|**colid**|**smallint**|定義條件約束的資料行識別碼。<br /><br /> 0 = 資料表條件約束|  
|**spare1**|**tinyint**|已保留|  
|**status**|**int**|指出狀態的虛擬位元遮罩。 可能的值如下：<br /><br /> 1 = PRIMARY KEY 條件約束<br /><br /> 2 = UNIQUE KEY 條件約束<br /><br /> 3 = FOREIGN KEY 條件約束<br /><br /> 4 = CHECK 條件約束<br /><br /> 5 = DEFAULT 條件約束<br /><br /> 16 = 資料行層級條件約束<br /><br /> 32 = 資料表層級條件約束|  
|**動作**|**int**|已保留|  
|**錯誤**|**int**|已保留|  
  
## <a name="see-also"></a>請參閱  
 [將系統資料表對應至系統檢視 &#40;TRANSACT-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [相容性檢視 &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
