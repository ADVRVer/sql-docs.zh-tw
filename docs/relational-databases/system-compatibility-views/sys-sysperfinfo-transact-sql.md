---
title: sysperfinfo （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysperfinfo_TSQL
- sys.sysperfinfo_TSQL
- sys.sysperfinfo
- sysperfinfo
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysperfinfo compatibility view
- sysperfinfo system table
ms.assetid: e22a81cd-27de-4690-9443-6aad6393bd3c
author: rothja
ms.author: jroth
ms.openlocfilehash: e6ce86e7be7d54e95c2336691b53ea12ff0d8575
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076500"
---
# <a name="syssysperfinfo-transact-sql"></a>sys.sysperfinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]包含可以透過 Windows 系統監視器顯示之內部效能計數器的標記法。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**object_name**|**Nchar （128）**|效能物件名稱，例如**sqlserver： LockManager**或**sqlserver： BufferManager**。|  
|**counter_name**|**Nchar （128）**|物件內效能計數器的名稱，例如要求的**頁面要求**或**鎖定**。|  
|**instance_name**|**Nchar （128）**|計數器的具名執行個體。 例如，針對每個鎖定類型（例如**資料表**、**頁面**、索引**鍵**等等）維護了計數器。 相似計數器的執行個體名稱各不相同。|  
|**cntr_value**|**Bigint**|實際的計數器值。 這通常都是一個層級計數器或單純增加的計數器，用來計算執行個體事件的出現次數。|  
|**cntr_type**|**int**|Windows 效能架構所定義的計數器類型。|  
  
## <a name="see-also"></a>另請參閱  
 [將系統資料表對應至系統檢視 &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [&#40;Transact-sql&#41;的相容性檢視](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
