---
title: DROP EXTERNAL LIBRARY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP EXTERNAL LIBRARY
- DROP_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP EXTERNAL LIBRARY
author: dphansen
ms.author: davidph
manager: cgronlund
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 129aafce2e270f85506d056d5d083d34176aa8a0
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018014"
---
# <a name="drop-external-library-transact-sql"></a>DROP EXTERNAL LIBRARY (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

刪除現有的套件程式庫。 支援的外部執行階段 (例如 R、Python 或 Java) 會使用套件程式庫。

> [!NOTE]
> 在 SQL Server 2017 中，支援 R 語言和 Windows 平台。 在 SQL Server 2019 CTP 2.3 中，支援 R、Python 和 Windows 平台上的 Java。 預計在稍後的版本中將會支援 Linux。

## <a name="syntax"></a>語法

```sql
DROP EXTERNAL LIBRARY library_name
[ AUTHORIZATION owner_name ];
```

### <a name="arguments"></a>引數

**library_name**

指定現有套件程式庫的名稱。

程式庫的範圍限制為使用者。 程式庫名稱在特定使用者或擁有者的內容中必須是唯一的。

**owner_name**

指定擁有外部程式庫的使用者或角色名稱。

資料庫擁有者可以刪除其他使用者建立的程式庫。

## <a name="permissions"></a>[權限]

若要刪除程式庫，需要 ALTER ANY EXTERNAL LIBRARY 權限。 根據預設，任何資料庫擁有者或物件的擁有者，也可刪除外部程式庫。

### <a name="return-values"></a>傳回值

如果陳述式執行成功，會傳回參考訊息。

## <a name="remarks"></a>Remarks

不同於 SQL Server 中的其他 `DROP` 陳述式，此陳述式支援指定選擇性授權子句。 這可讓 **db_owner** 角色中的 **dbo** 或使用者卸除資料庫中由一般使用者上傳的套件資料庫。

## <a name="examples"></a>範例

將自訂 R 套件 `customPackage` 加入資料庫：

```sql
CREATE EXTERNAL LIBRARY customPackage 
FROM (CONTENT = 'C:\temp\customPackage_v1.1.zip')
WITH (LANGUAGE = 'R');
GO
```

刪除 `customPackage` 程式庫。

```sql
DROP EXTERNAL LIBRARY customPackage;
```

## <a name="see-also"></a>另請參閱

[CREATE EXTERNAL LIBRARY (Transact-SQL)](create-external-library-transact-sql.md)  
[ALTER EXTERNAL LIBRARY (Transact-SQL)](alter-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  

