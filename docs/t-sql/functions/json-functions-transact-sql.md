---
title: JSON 函式 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: genemi
ms.technology: t-sql
ms.topic: language-reference
helpviewer_keywords:
- JSON functions
ms.assetid: ec97d451-06af-44a3-8304-305d410cfc8e
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: = azuresqldb-current||= azure-sqldw-latest||>= sql-server-2016||>= sql-server-linux-2017||= sqlallproducts-allversions
ms.openlocfilehash: bd5ea0433b1cbdee6adf97dbab9a2dcdddcb8389
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "65577464"
---
# <a name="json-functions-transact-sql"></a>JSON 函式 (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

使用此章節頁面上描述的函式來驗證或變更 JSON 文字，或擷取簡單或複雜的值。  
  
|函數|Description|  
|--------------|-----------------|  
|[ISJSON](../../t-sql/functions/isjson-transact-sql.md)|測試字串是否包含有效的 JSON。|  
|[JSON_VALUE](../../t-sql/functions/json-value-transact-sql.md)|從 JSON 字串擷取純量值。|  
|[JSON_QUERY](../../t-sql/functions/json-query-transact-sql.md)|從 JSON 字串擷取物件或陣列。|  
|[JSON_MODIFY](../../t-sql/functions/json-modify-transact-sql.md)|更新 JSON 字串中的屬性值，並傳回更新後的 JSON 字串。|

 如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中內建 JSON 支援的詳細資訊，請參閱 [JSON 資料 &#40;SQL Server&#41;](../../relational-databases/json/json-data-sql-server.md)。  

## <a name="see-also"></a>另請參閱

 - [使用內建函數，驗證、查詢以及變更 JSON 資料 &#40;SQL Server&#41;](../../relational-databases/json/validate-query-and-change-json-data-with-built-in-functions-sql-server.md)
 - [JSON 路徑運算式 &#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)
 - [JSON 資料 &#40;SQL Server&#41;](../../relational-databases/json/json-data-sql-server.md)  
