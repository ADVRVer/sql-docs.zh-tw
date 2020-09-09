---
description: sp_helpfile (Transact-SQL)
title: sp_helpfile (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpfile
- sp_helpfile_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpfile
ms.assetid: 1546e0ae-5a99-4e01-9eb9-d147fa65884c
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 7bb8c6ff5fe18393db1c08bae888d1479a7f2594
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89549640"
---
# <a name="sp_helpfile-transact-sql"></a>sp_helpfile (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  傳回目前資料庫之相關檔案的實體名稱和屬性。 請利用這個預存程序來判斷伺服器所要附加或卸離的檔案名稱。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helpfile [ [ @filename= ] 'name' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @filename = ] 'name'` 這是目前資料庫中任何檔案的邏輯名稱。 *名稱* 是 **sysname**，預設值是 Null。 如果未指定 *name* ，則會傳回目前資料庫中所有檔案的屬性。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|邏輯檔案名稱。|  
|**fileid**|**smallint**|檔案的數值識別碼。 如果指定 *名稱* ，則不會傳回 *。*|  
|**filename**|**Nchar (260) **|實體檔案名稱。|  
|**filegroup**|**sysname**|檔案所屬的檔案群組。<br /><br /> NULL = 檔案是記錄檔。 它永遠不在檔案群組中。|  
|**size**|**Nvarchar (15) **|檔案大小 (以 KB 為單位)。|  
|**maxsize**|**Nvarchar (15) **|檔案所能成長的大小上限。 這個欄位中的 UNLIMITED 值指出，檔案將成長到磁碟已滿。|  
|**增長**|**Nvarchar (15) **|檔案的成長遞增。 這表示每次需要新空間時，檔案所增加的空間量。<br /><br /> 0 = 檔案是固定大小，不會成長。|  
|**使用**|**Varchar (9) **|針對資料檔，此值為 [ **僅限資料** ]，而針對記錄檔，其值為 [ **僅限記錄**]。|  
  
## <a name="permissions"></a>權限  
 需要 **public** 角色的成員資格。  
  
## <a name="examples"></a>範例  
 下列範例會傳回 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 中之檔案的相關資訊。  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfile;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的資料庫引擎預存程式 ](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpfilegroup &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpfilegroup-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys. master_files &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [資料庫檔案與檔案群組](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  
