---
title: "永遠加密 (用戶端開發) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "07/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
caps.latest.revision: 33
author: "stevestein"
manager: "jhubbard"
caps.handback.revision: 33
---
# 永遠加密 (用戶端開發)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

[永遠加密](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)是一項用戶端加密技術，可確保敏感性資料 (及相關的加密金鑰) 永遠不會洩漏給 SQL Server 或 Azure SQL Database。 透過永遠加密，用戶端驅動程式可以明確地加密敏感性資料，再將資料傳遞至資料庫引擎，而且可以將擷取自已加密資料庫資料行的資料明確地解密。

如需開發使用受永遠加密保護之資料庫的應用程式，以及哪些用戶端驅動程式和驅動程式版本支援永遠加密的詳細資訊，請參閱：

- [搭配 .NET Framework Data Provider for SQL Server 使用 [永遠加密]](../../../relational-databases/security/encryption/develop using always encrypted with .net framework data provider.md)
- [搭配使用一律加密與 JDBC 驅動程式](https://msdn.microsoft.com/library/mt591987.aspx)
- [搭配使用一律加密與 Windows ODBC 驅動程式](https://msdn.microsoft.com/library/mt637351.aspx)



## 另請參閱

[一律加密 (Database Engine)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
