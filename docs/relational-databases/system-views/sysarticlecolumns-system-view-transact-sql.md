---
title: "sysarticlecolumns （系統檢視） (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs: TSQL
helpviewer_keywords: sysarticlecolumns view
ms.assetid: a8dd8d13-c827-45c4-87ba-802725301382
caps.latest.revision: "10"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a7e5f8c29826bd37306fe2fc455b449ab6362c67
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="sysarticlecolumns-system-view-transact-sql"></a>sysarticlecolumns (系統檢視) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sysarticlecolumns**檢視會公開發行之發行項中的資料行的其他資訊。 這份檢視儲存在散發資料庫中。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|識別發行項。|  
|**colid**|**int**|識別發行項中的資料行。|  
|**is_udt**|**int**|指出資料行是否為使用者自訂資料類型 (UDT) 資料行。 值為**1**表示 UDT 資料行。|  
|**is_xml**|**int**|是資料行是否為**xml**資料行。 值為**1**指出**xml**資料行。|  
|**is_max**|**int**|是資料行是否為大數值資料類型資料行 (**varchar （max)**， **nvarchar （max)**或**varbinary （max)**)。 值為**1**表示大數值資料行。|  
  
## <a name="see-also"></a>請參閱＜  
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sysarticlecolumns &#40;TRANSACT-SQL &#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
