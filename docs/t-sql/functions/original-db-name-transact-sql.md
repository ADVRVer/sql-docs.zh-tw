---
title: ORIGINAL_DB_NAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ORIGINAL_DB_NAME
- ORIGINAL_DB_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ORIGINAL_DB_NAME function
ms.assetid: 7dadc40a-1287-4f31-8487-434ee477144d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 889cdb18a323e64cf1b94bcde57eaf77c37e89d4
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892553"
---
# <a name="original_db_name-transact-sql"></a>ORIGINAL_DB_NAME (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  傳回使用者在資料庫連接字串中指定的資料庫名稱。 此資料庫會使用 **sqlcmd-d** 選項 (使用 *database*) 來指定。 它也可以使用開放式資料庫連接 (ODBC) 資料來源運算式 (initial catalog =*databasename*) 來指定。  
  
 此資料庫與預設的使用者資料庫不同。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
ORIGINAL_DB_NAME ()  
```  
  
## <a name="remarks"></a>備註  
 如果未指定初始資料庫，函數就會傳回空字串。  
  
## <a name="see-also"></a>另請參閱  
 [sqlcmd 公用程式](../../tools/sqlcmd-utility.md)   
 [osql 公用程式](../../tools/osql-utility.md)   
 [SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
