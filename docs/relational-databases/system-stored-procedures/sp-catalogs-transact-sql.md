---
title: sp_catalogs (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_catalogs_TSQL
- sp_catalogs
dev_langs:
- TSQL
helpviewer_keywords:
- sp_catalogs
ms.assetid: ebb29ee2-be65-4e09-9c53-e3c6d12633e1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 25aae75151ada9ac38b35324f7c82d98f77d580b
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2018
ms.locfileid: "52535790"
---
# <a name="spcatalogs-transact-sql"></a>sp_catalogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回指定連結伺服器中的目錄清單。 這相當於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的資料庫。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_catalogs [ @server_name = ] 'linked_svr'  
```  
  
## <a name="arguments"></a>引數  
 [  **@server_name =**] **'**_linked_svr_**'**  
 這是連結伺服器的名稱。 *linked_svr*已**sysname**，沒有預設值。  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**Catalog_name**|**nvarchar(** 128 **)**|目錄的名稱。|  
|**說明**|**nvarchar (** 4000 **)**|目錄的描述|  
  
## <a name="permissions"></a>Permissions  
 需要結構描述的 SELECT 權限。  
  
## <a name="examples"></a>範例  
 下列範例會傳回 `OLE DB ODBC Linked Server #3` 這個連結伺服器的目錄資訊。  
  
> [!NOTE]  
>  針對**sp_catalogs**提供有用的資訊，`OLE DB ODBC Linked Server #3`必須已經存在。  
  
```  
USE master;  
GO  
EXEC sp_catalogs 'OLE DB ODBC Linked Server #3';  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_columns_ex &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-columns-ex-transact-sql.md)   
 [sp_column_privileges &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [< sp_indexes &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [idbschemarowset &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-primarykeys-transact-sql.md)   
 [idbschemarowset &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
