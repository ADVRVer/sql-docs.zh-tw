---
title: sys.sysdepends (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysdepends_TSQL
- sysdepends
- sysdepends_TSQL
- sys.sysdepends
dev_langs:
- TSQL
helpviewer_keywords:
- sysdepends system table
- sys.sysdepends compatibility view
ms.assetid: f9c182cb-386f-4e72-859f-9f1115b389f9
author: rothja
ms.author: jroth
ms.openlocfilehash: 5d928926294bb3e80f860a535a266b5c106e3f18
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053504"
---
# <a name="syssysdepends-transact-sql"></a>sys.sysdepends (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  包含資料庫物件 (檢視、程序和觸發程序) 及其定義所含物件 (資料表、檢視和程序) 之間的相依性資訊。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**id**|**int**|物件識別碼。|  
|**depid**|**int**|相依物件識別碼。|  
|**number**|**smallint**|程序編號。|  
|**depnumber**|**smallint**|相依程序編號。|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**deptype**|**tinyint**|識別相依物件類型：<br /><br /> 0 = 物件或資料行 (只限於非結構描述繫結參考)<br /><br /> 1 = 物件或資料行 (結構描述繫結參考)|  
|**depdbid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**depsiteid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**selall**|**bit**|1 = 物件用於 SELECT * 陳述式中。<br /><br /> 0 = 否。|  
|**resultobj**|**bit**|1 = 正在更新物件。<br /><br /> 0 = 否。|  
|**readobj**|**bit**|1 = 正在讀取物件。<br /><br /> 0 = 否。|  
  
## <a name="see-also"></a>另請參閱  
 [將系統資料表對應至系統檢視表&#40;Transact SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [相容性檢視&#40;Transact SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [sp_depends &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-depends-transact-sql.md)   
 [sys.sql_dependencies &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md)  
  
  
