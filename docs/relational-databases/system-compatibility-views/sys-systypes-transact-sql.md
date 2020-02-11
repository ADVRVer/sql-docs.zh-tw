---
title: systypes （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.systypes_TSQL
- systypes_TSQL
- sys.systypes
- systypes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.systypes compatibility view
- systypes system table
ms.assetid: 1b0b1d0c-5f7b-470b-bd52-8bfa922d7889
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5533e521ba28c0190a5be57ed7637632213d7447
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "68018085"
---
# <a name="syssystypes-transact-sql"></a>sys.systypes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  針對資料庫中所定義的每個系統提供資料類型和每個使用者自訂資料類型，各傳回一個資料列。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|資料類型名稱。|  
|**xtype**|**tinyint**|實體儲存類型。|  
|**狀態**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**smallint**|擴充使用者類型。 如果資料類型的數目超過 32,767，則會造成溢位或傳回 NULL。|  
|**長**|**smallint**|資料類型的實際長度。|  
|**xprec**|**tinyint**|符合伺服器所用的內部有效位數。 不會用在查詢中。|  
|**xscale**|**tinyint**|符合伺服器所用的內部小數位數。 不會用在查詢中。|  
|**tdefault**|**int**|包含這個資料類型之完整性檢查的預存處理序識別碼。|  
|**domain**|**int**|包含這個資料類型之完整性檢查的預存處理序識別碼。|  
|**uid**|**smallint**|類型擁有者的結構描述識別碼。<br /><br /> 如果是從舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升級而來的資料庫，結構描述識別碼會等於擁有者的使用者識別碼。<br /><br /> ** \* \*重要\*事項**如果您使用下列[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]任何一個 DDL 語句，就必須使用[sys.databases](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)目錄檢視，而不是**systypes**。<br /><br /> ALTER AUTHORIZATION ON TYPE<br /><br /> CREATE TYPE<br /><br /> 如果使用者和角色數目超過 32,767 個，則會造成溢位或傳回 NULL。|  
|**留**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**collationid**|**int**|如果是以字元為基礎， **collationid**就是目前資料庫的定序識別碼。否則，它會是 Null。|  
|**usertype**|**smallint**|使用者類型識別碼。 如果資料類型的數目超過 32,767，則會造成溢位或傳回 NULL。|  
|**變**|**bit**|可變長度資料類型。<br /><br /> 1 = True<br /><br /> 0 = False|  
|**allownulls**|**bit**|指出這項資料類型的預設 Null 屬性。 如果使用[CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md)或[ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)來指定 null 屬性，則會覆寫這個預設值。|  
|**type**|**tinyint**|實體儲存體資料類型。|  
|**printfmt**|**Varchar （255）**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**smallint**|這個資料類型的有效位數層級。<br /><br /> -1 = **xml**或大數數值型別。|  
|**尺度**|**tinyint**|這個資料類型的小數位數 (以有效位數為基礎)。<br /><br /> NULL = 資料類型是非數值。|  
|**定序**|**sysname**|如果是以字元為基礎，定**序**就是目前資料庫的定序。否則，它會是 Null。|  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的相容性檢視](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [將系統資料表對應至系統檢視 &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
