---
title: MSreplication_options （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSreplication_options
- MSreplication_options_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_options system table
ms.assetid: 23cf10d7-8bc1-4368-b5eb-e5576421e776
author: stevestein
ms.author: sstein
ms.openlocfilehash: c48a57b876cde41d6bb514c522bcaa241eec11fd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "68062997"
---
# <a name="msreplication_options-transact-sql"></a>MSreplication_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSreplication_options**資料表會儲存複寫在內部使用的中繼資料。 此資料表會儲存在**master**資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**optname**|**sysname**|僅供內部使用。|  
|**值**|**bit**|僅供內部使用。|  
|**major_version**|**int**|僅供內部使用。|  
|**minor_version**|**int**|僅供內部使用。|  
|**修正**|**int**|僅供內部使用。|  
|**install_failures**|**int**|僅供內部使用。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表 &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
