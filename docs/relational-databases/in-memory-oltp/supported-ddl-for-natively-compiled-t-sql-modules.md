---
title: 原生編譯 T-SQL 模組支援的 DDL | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9fde492554b52170602e5676fa8dcce018885053
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "68086255"
---
# <a name="supported-ddl-for-natively-compiled-t-sql-modules"></a>原生編譯 T-SQL 模組支援的 DDL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  本主題列出原生編譯 T-SQL 模組支援的 DDL 建構，如預存程序、純量 UDF、內嵌 TVF 和觸發程序。  
  
 如需可當作原生編譯 T-SQL 模組一部分之功能和 T-SQL 介面區的相關資訊，請參閱 [原生編譯的 T-SQL 模組支援的功能](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md)。  
  
 如需不受支援建構的相關資訊，請參閱 [記憶體中的 OLTP 不支援 Transact-SQL 建構](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)。  
  
 支援下列功能：  
  
-   [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)  
  
-   [DROP PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-procedure-transact-sql.md)  
  
-   [ALTER PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-procedure-transact-sql.md)  
  
-   [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md) 和 INSERT SELECT 陳述式  
  
-   SCHEMABINDING 和 BEGIN ATOMIC (原生編譯預存程序所需的)  
  
     如需詳細資訊，請參閱 [建立原生編譯的預存程序](../../relational-databases/in-memory-oltp/creating-natively-compiled-stored-procedures.md)。  
  
-   NATIVE_COMPILATION  
  
     如需詳細資訊，請參閱 [資料表和預存程序的原生編譯](../../relational-databases/in-memory-oltp/native-compilation-of-tables-and-stored-procedures.md)。  
  
-   參數和變數可宣告為 NOT NULL (僅適用於原生編譯模組︰原生編譯預存程序和原生編譯純量使用者定義函數)。  
  
-   資料表值參數。  
  
     如需詳細資訊，請參閱[使用資料表值參數 &#40;Database Engine&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)。  
  
-   EXECUTE AS OWNER、SELF、CALLER 和使用者。  
  
-   資料表和程序的 GRANT 和 DENY 權限。  
  
     如需詳細資訊，請參閱 [GRANT 物件權限 &#40;Transact-SQL&#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md) 和 [DENY 物件權限 &#40;Transact-SQL&#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)。  
  
## <a name="see-also"></a>另請參閱  
 [原生編譯的預存程序](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  
