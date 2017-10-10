---
title: "卸除的外部程式庫 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 08/17/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP EXTERNAL LIBRARY
- DROP_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP EXTERNAL LIBRARY
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: ac2814f7c0b0d1bf6de60d52ea65e54caab0f72d
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="drop-external-library-transact-sql"></a>卸除的外部程式庫 (TRANSACT-SQL)  
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]  

刪除現有的封裝程式庫。

## <a name="syntax"></a>語法  

```
DROP EXTERNAL LIBRARY library_name  
[ AUTHORIZATION owner_name ];  
```

### <a name="arguments"></a>引數

**library_name**

指定現有的封裝程式庫名稱。

程式庫的範圍給使用者。 也就是程式庫名稱會視為特定使用者或擁有者的內容中唯一的。

**owner_name**

指定使用者或角色擁有外部的程式庫的名稱。

資料庫擁有者可以刪除其他使用者所建立的文件庫。

### <a name="return-values"></a>傳回值

如果陳述式執行成功，則會傳回參考用訊息。

## <a name="remarks"></a>備註

不同於其他`DROP`指定選擇性的 authorization 子句中 SQL Server 陳述式，這個陳述式支援。 這可讓**dbo**中的使用者或**db_owner**一般使用者資料庫中卸除封裝程式庫的角色上傳。

## <a name="examples"></a>範例

加入自訂的 R 封裝，名為`customPackage`，資料庫：

```sql
CREATE EXTERNAL LIBRARY customPackage 
FROM 'C:\Users\Username\CustomPackages\customPackage.zip';
```

刪除`customPackage`程式庫。

```sql
DROP EXTERNAL LIBRARY customPackage <user_name>;
```

## <a name="see-also"></a>另請參閱  
[建立外部程式庫 (TRANSACT-SQL)](create-external-library-transact-sql.md)  
[ALTER 外部程式庫 (TRANSACT-SQL)](alter-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  


