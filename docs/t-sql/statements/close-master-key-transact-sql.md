---
title: "CLOSE MASTER KEY (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CLOSE MASTER KEY
- CLOSE_MASTER_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- encryption [SQL Server], Database Master Key
- CLOSE MASTER KEY statement
- database master key [SQL Server], closing
- cryptography [SQL Server], Database Master Key
- closing Database Master Keys
ms.assetid: bb04ef7a-9f3a-437e-a6f9-ba0204082cb9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0e33e1ba179e9cdfcf3076be8a8f4878048ef6e6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="close-master-key-transact-sql"></a>CLOSE MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  關閉目前資料庫的主要金鑰。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
CLOSE MASTER KEY  
```  
  
## <a name="arguments"></a>引數  
 不需要任何引數。  
  
## <a name="remarks"></a>備註  
 這個陳述式會反轉 OPEN MASTER KEY 執行的作業。 僅當使用 OPEN MASTER KEY 陳述式在目前工作階段中開啟資料庫主要金鑰時，執行 CLOSE MASTER KEY 才會成功。  
  
## <a name="permissions"></a>Permissions  
 不需要任何權限。  
  
## <a name="examples"></a>範例  
  
```  
USE AdventureWorks2012;  
CLOSE MASTER KEY;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```  
USE master;  
OPEN MASTER KEY DECRYPTION BY PASSWORD = '43987hkhj4325tsku7';  
GO   
CLOSE MASTER KEY;  
GO  
```  
  
## <a name="see-also"></a>請參閱＜  
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md)   
 [開啟主要金鑰 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/open-master-key-transact-sql.md)   
 [加密階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

