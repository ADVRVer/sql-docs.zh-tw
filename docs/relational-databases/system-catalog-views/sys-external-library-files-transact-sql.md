---
title: sys.databases external_library_files （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/25/2020
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
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: 8068df01ade7361c542150a3ee1f98ac137110e8
ms.sourcegitcommit: a0ebbcb717f09d3614de5ce9eb9f3c00f0a45f81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85409357"
---
# <a name="sysexternal_library_files-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

列出組成外部程式庫之每個檔案的資料列。

|資料行名稱 |資料類型 |描述|
|------|------|-----|
|external_library_id | int |外部程式庫物件的識別碼。 |
|content |varbinary(max) |外部程式庫檔案成品的內容。 |
|平台 |TINYINT |安裝 SQL Server 之主機平臺的識別碼。 |
|platform_desc | nvarchar(60) |主機平臺的名稱。 有效的值為 ' WINDOWS '、' LINUX '。 |

### <a name="see-also"></a>另請參閱  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[建立外部程式庫](../../t-sql/statements/create-external-library-transact-sql.md)  
