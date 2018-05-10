---
title: MSSQLSERVER_137 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 137 (Database Engine error)
ms.assetid: 47fb4212-2165-4fec-bc41-6d548465d7be
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6d581cb6eeeb0965143b4830f90c0c537d4db7db
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver137"></a>MSSQLSERVER_137
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|137|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|P_SCALAR_VAR_NOTFOUND|  
|訊息文字|必須宣告純量變數 "%.*ls"。|  
  
## <a name="explanation"></a>說明  
當您在 SQL 指令碼中使用某個變數，但卻沒有先宣告該變數時，就會發生這個錯誤。 下列範例會針對 SET 和 SELECT 陳述式傳回錯誤 137，因為未宣告 **@mycol**。  
  
SET @mycol = 'ContactName';  
  
SELECT @mycol;  
  
導致這個錯誤的其中一個更複雜原因包括使用了在 EXECUTE 陳述式外部宣告的變數。 例如，在 SELECT 陳述式中指定的變數 **@mycol** 是 SELECT 陳述式的本機變數。因此，這個變數就位於 EXECUTE 陳述式外部。  
  
USE AdventureWorks2012;  
  
GO  
  
DECLARE @mycol nvarchar(20);  
  
SET @mycol = 'Name';  
  
EXECUTE ('SELECT @mycol FROM Production.Product;');  
  
## <a name="user-action"></a>使用者動作  
請確認在 SQL 指令碼中使用的任何變數都已經過宣告，然後再用於指令碼的其他位置。  
  
重寫指令碼，讓它不會在 EXECUTE 陳述式中參考在該陳述式外部宣告的變數。 例如：  
  
USE AdventureWorks2012;  
  
GO  
  
DECLARE @mycol nvarchar(20) ;  
  
SET @mycol = 'Name';  
  
EXECUTE ('SELECT ' + @mycol + ' FROM Production.Product';) ;  
  
## <a name="see-also"></a>另請參閱  
[EXECUTE &#40;Transact-SQL&#41;](~/t-sql/language-elements/execute-transact-sql.md)  
[SET 陳述式 &#40;Transact-SQL&#41;](~/t-sql/statements/set-statements-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](~/t-sql/language-elements/declare-local-variable-transact-sql.md)  
  
