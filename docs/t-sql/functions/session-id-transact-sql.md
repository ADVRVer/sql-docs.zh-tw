---
title: "SESSION_ID (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 2a0d500a-f6c8-490f-9abd-3ae824986404
caps.latest.revision: "9"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 07c52331f64cd9104deb8956b893cc2759371feb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="sessionid-transact-sql"></a>SESSION_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  傳回目前的識別碼[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]或[!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)]工作階段。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [TRANSACT-SQL 語法慣例 &#40;TRANSACT-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
SESSION_ID ( )  
```  
  
## <a name="return-value"></a>傳回值  
 傳回**nvarchar （32)**值。  
  
## <a name="general-remarks"></a>一般備註  
 連線時，工作階段識別碼被指派給每個使用者連接。 它會保存在連接持續時間。 連線結束時，會釋放工作階段識別碼。  
  
 工作階段識別碼的開頭依字母順序排列的字元 'SID'。 區分大小寫和工作階段識別碼中使用時必須大寫[!INCLUDE[DWsql](../../includes/dwsql-md.md)]命令。  
  
 您可以查詢檢視[sys.dm_pdw_exec_sessions](http://msdn.microsoft.com/en-us/5b656c55-427f-4306-8bd9-9d7987c203d9)擷取此函式相同的資訊。  
  
## <a name="examples"></a>範例  
 下列範例會傳回目前工作階段識別碼。  
  
```  
SELECT SESSION_ID();  
```  
  
## <a name="see-also"></a>另請參閱  
 [DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)   
 [版本 &#40;SQL 資料倉儲 &#41;](../../t-sql/functions/version-transact-sql-configuration-functions.md)
  
  
