---
title: external_library_files (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 07/24/2019
ms.prod: sql
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- external_library_files
- external_library_files_TSQL
- sys.external_library_files
- sys.external_library_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_library_files catalog view
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d7af0a7fcb639ae3beab6216e77f9b7b95a398da
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68471089"
---
# <a name="sysexternallibraryfiles-transact-sql"></a>external_library_files (Transact-sql)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

列出組成外部程式庫之每個檔案的資料列。

|資料行名稱 |資料類型 |描述|
|------|------|-----|
|external_library_id | ssNoversion |外部程式庫物件的識別碼。 |
|content |varbinary(max) |外部程式庫檔案成品的內容。 |
|platform.object |TINYINT |安裝 SQL Server 之主機平臺的識別碼。 |
|platform_desc | nvarchar(60) |主機平臺的名稱。 有效的值為 ' WINDOWS '、' LINUX '。 |

### <a name="see-also"></a>另請參閱  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[建立外部程式庫](../../t-sql/statements/create-external-library-transact-sql.md)  
[SQL Server Machine Learning 服務的套件管理](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
