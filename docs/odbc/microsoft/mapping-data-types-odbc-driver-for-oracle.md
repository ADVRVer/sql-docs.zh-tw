---
title: "對應資料類型 （如 Oracle 的 ODBC 驅動程式） |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping data types [ODBC]
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: a5d9ce12-19da-4943-8493-e3d56fa08348
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dc140e389f114b2ea67f8628b537ad603eb51d72
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mapping-data-types-odbc-driver-for-oracle"></a>對應資料類型 （如 Oracle 的 ODBC 驅動程式）
> [!IMPORTANT]  
>  將移除這項功能，在未來的版本的 Windows。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 相反地，使用由 Oracle 提供的 ODBC 驅動程式。  
  
 在 Oracle 伺服器支援資料型別的集合。 Oracle 的 ODBC 驅動程式會將這些資料類型對應至適當的 ODBC SQL 資料類型。 下表列出 Oracle 7.3 Server 資料類型和其對應的 ODBC SQL 資料類型。  
  
 ODBC Driver for Oracle 支援 Oracle 7.3 和某些 Oracle8 資料類型。 如需支援 Oracle8 資料類型的詳細資訊，請參閱[Supported Data Types](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md)。  
  
|Oracle Server 資料類型|ODBC SQL 資料類型|  
|-----------------------------|------------------------|  
|CHAR|SQL_CHAR|  
|DATE|SQL_TIMESTAMP|  
|FLOAT|SQL_DOUBLE|  
|INTEGER|SQL_DECIMAL|  
|LONG|SQL_LONGVARCHAR|  
|LONG RAW|SQL_LONGVARBINARY|  
|NUMBER|SQL_DECIMAL|  
|RAW|SQL_VARBINARY|  
|VARCHAR2|SQL_VARCHAR|  
  
> [!NOTE]  
>  VARCHAR 資料行的允許大小的相關資訊，請參閱[VARCHAR 資料行大小](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md)本指南中。
