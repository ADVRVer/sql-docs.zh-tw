---
title: sp_helpstats (TRANSACT-SQL) |Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helpstats
- sp_helpstats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpstats
ms.assetid: 00ab3cfd-2736-4fc0-b1b2-16dd49fb2fe5
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: eda430dedf39538c27f85d0ea11ca59bbfdc5e20
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33251634"
---
# <a name="sphelpstats-transact-sql"></a>sp_helpstats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回指定資料表之資料行和索引的統計資料資訊。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)] 若要取得統計資料的相關資訊，請查詢[sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)和[sys.stats_columns](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md)目錄檢視。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helpstats[ @objname = ] 'object_name'   
     [ , [ @results = ] 'value' ]  
```  
  
## <a name="arguments"></a>引數  
 [  **@objname=**] **'***object_name***'**  
 指定要提供統計資料資訊的資料表。 *object_name*是**nvarchar(520)** ，不能是 null。 可以指定一部分名稱或兩部分名稱。  
  
 [  **@results=**] **'***值***'**  
 指定要提供的資訊範圍。 有效的項目是**所有**和**STATS**。 **所有**列出所有索引和也具有; 上建立統計資料的資料行的統計資料**STATS**只會列出與索引無關的統計資料。 *值*是**nvarchar （5)** 預設值是 STATS。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
 下表描述結果集中的資料行。  
  
|資料行名稱|Description|  
|-----------------|-----------------|  
|**statistics_name**|統計資料的名稱。 傳回**sysname** ，不能是 null。|  
|**statistics_keys**|統計資料的基礎索引鍵。 傳回**nvarchar(2078)** ，不能是 null。|  
  
## <a name="remarks"></a>備註  
 請利用 DBCC SHOW_STATISTICS 來顯示任何特定索引或統計資料的詳細統計資訊。 如需詳細資訊，請參閱[DBCC SHOW_STATISTICS &#40;TRANSACT-SQL&#41; ](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)和[sp_helpindex &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md)。  
  
## <a name="permissions"></a>Permissions  
 需要 **public** 角色中的成員資格。  
  
## <a name="examples"></a>範例  
 下列範例會執行 `sp_createstats` 來建立 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中所有使用者資料表之所有適用資料行的單一資料行統計資料。 之後，便會執行 `sp_helpstats` 來尋找在 `Customer` 資料表上建立的結果統計資料。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_createstats;  
GO  
EXEC sp_helpstats   
@objname = 'Sales.Customer',  
@results = 'ALL';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `statistics_name               statistics_keys`  
  
 `----------------------------  ----------------`  
  
 `_WA_Sys_00000003_22AA2996     AccountNumber`  
  
 `AK_Customer_AccountNumber     AccountNumber`  
  
 `AK_Customer_rowguid           rowguid`  
  
 `CustomerType                  CustomerType`  
  
 `IX_Customer_TerritoryID       TerritoryID`  
  
 `ModifiedDate                  ModifiedDate`  
  
 `PK_Customer_CustomerID        CustomerID`  
  
## <a name="see-also"></a>另請參閱  
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Database Engine 預存程序&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
