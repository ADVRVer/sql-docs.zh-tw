---
title: sys.schemas (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- schemas_TSQL
- sys.schemas_TSQL
- schemas
- sys.schemas
dev_langs:
- TSQL
helpviewer_keywords:
- sys.schemas catalog view
ms.assetid: 29af5ce5-2af7-4103-8f08-3ec92603ba05
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8519dc4846f148b1b4d1bc83589baf0cc6a81e12
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "65983140"
---
# <a name="schemas-catalog-views---sysschemas"></a>結構描述目錄檢視-sys.schemas
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  針對每個資料庫結構描述，各包含一個資料列。  
  
> [!NOTE]  
>  資料庫結構描述與 XML 結構描述不同，它是用來定義 XML 文件的內容模型。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|結構描述的名稱。 在資料庫中，這是唯一的。|  
|**schema_id**|**int**|結構描述的識別碼。 在資料庫中，這是唯一的。|  
|**principal_id**|**int**|擁有這個結構描述之主體的識別碼。|  
  
## <a name="remarks"></a>備註  
資料庫結構描述做為命名空間或容器物件，例如資料表、 檢視、 程序和函式，可以在中找到**sys.objects**目錄檢視。  

每個結構描述具有擁有者。 擁有者是安全[主體](../../relational-databases/security/authentication-access/principals-database-engine.md)。
  
## <a name="permissions"></a>Permissions  
 需要 **public** 角色的成員資格。 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
[主體](../../relational-databases/security/authentication-access/principals-database-engine.md)

[目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   

[結構描述目錄檢視&#40;Transact SQL&#41;](https://msdn.microsoft.com/library/c516fb1c-b6ed-48ae-99c7-a78bc4336c8e)   

[sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  
