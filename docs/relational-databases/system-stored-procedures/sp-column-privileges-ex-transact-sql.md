---
title: sp_column_privileges_ex （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_column_privileges_ex
- sp_column_privileges_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_column_privileges_ex
ms.assetid: 98cb6e58-4007-40fc-b048-449fb2e7e6be
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd4251c4b47f67d348b6978c05c07d0ae64d16c8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "68070363"
---
# <a name="sp_column_privileges_ex-transact-sql"></a>sp_column_privileges_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回指定連結伺服器之指定資料表的資料行權限。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_column_privileges_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @column_name = ] 'column_name' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @table_server = ] 'table_server'`這是要傳回信息的連結伺服器名稱。 *table_server*是**sysname**，沒有預設值。  
  
`[ @table_name = ] 'table_name'`這是包含指定之資料行的資料表名稱。 *table_name*是**sysname**，預設值是 Null。  
  
`[ @table_schema = ] 'table_schema'`這是資料表架構。 *table_schema*是**sysname**，預設值是 Null。  
  
`[ @table_catalog = ] 'table_catalog'`這是指定之*table_name*所在的資料庫名稱。 *table_catalog*是**sysname**，預設值是 Null。  
  
`[ @column_name = ] 'column_name'`這是要提供許可權資訊的資料行名稱。 *column_name*是**sysname**，預設值是 Null （全部一般）。  
  
## <a name="result-sets"></a>結果集  
 下表會顯示結果集資料行。 傳回的結果會依**TABLE_QUALIFIER**、 **TABLE_OWNER**、 **TABLE_NAME**、 **COLUMN_NAME**和**許可權**來排序。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|資料表限定詞名稱。 各種 DBMS 產品都支援三部分的資料表命名（辨識_符號_**。**_擁有_者 **。**_名稱_）。 在[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，這個資料行代表資料庫名稱。 在某些產品中，它代表資料表之資料庫環境的伺服器名稱。 這個欄位可以是 NULL。|  
|**TABLE_SCHEM**|**sysname**|資料表擁有者名稱。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，這個資料行代表建立資料表的資料庫使用者名稱。 這個欄位一律會傳回值。|  
|**TABLE_NAME**|**sysname**|資料表名稱。 這個欄位一律會傳回值。|  
|**COLUMN_NAME**|**sysname**|資料行名稱，針對每個傳回的**TABLE_NAME**資料行。 這個欄位一律會傳回值。|  
|**授權**|**sysname**|已將此**COLUMN_NAME**的許可權授**與列出之**被授與者的資料庫使用者名稱。 在[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，這個資料行一律與**TABLE_OWNER**相同。 這個欄位一律會傳回值。<br /><br /> 「**授與者」資料行可以**是資料庫擁有者（**TABLE_OWNER**），或資料庫擁有者利用 GRANT 語句中之 WITH GRANT OPTION 子句來授與許可權的使用者。|  
|**者**|**sysname**|**列出的**授與者已授與此**COLUMN_NAME**之許可權的資料庫使用者名稱。 這個欄位一律會傳回值。|  
|**PRIVILEGE**|**Varchar （** 32 **）**|可用的資料行權限之一。 資料行權限可以是下列值之一 (或定義實作時，資料來源所支援的其他值)：<br /><br /> SELECT =**被**授與者可以抓取資料行的資料。<br /><br /> INSERT =**被****授與者可以在將新**資料列插入資料表時，提供此資料行的資料。<br /><br /> UPDATE =**被**授與者可以修改資料行中的現有資料。<br /><br /> REFERENCES =**被**授與者可以在主鍵/外鍵關聯性中，參考外部資料表中的資料行。 主索引鍵/外部索引鍵關聯性是利用資料表條件約束來定義的。|  
|**IS_GRANTABLE**|**Varchar （** 3 **）**|指出是否允許**被授與者**將許可權授與其他使用者（通常稱為「授與授與」許可權）。 它可以是 YES、NO 或 NULL。 未知 (或 NULL) 值是指不適用 "grant with grant" 的資料來源。|  
  
## <a name="permissions"></a>權限  
 需要結構描述的 SELECT 權限。  
  
## <a name="examples"></a>範例  
 下列範例會從 `HumanResources.Department` 連結伺服器的 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫之 `Seattle1` 資料表中，傳回資料行權限資訊。  
  
```  
EXEC sp_column_privileges_ex @table_server = 'Seattle1',   
   @table_name = 'Department',   
   @table_schema = 'HumanResources',  
   @table_catalog ='AdventureWorks2012';  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_table_privileges_ex &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-ex-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
