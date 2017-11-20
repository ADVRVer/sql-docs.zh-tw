---
title: "SET NULL 命令 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- set nullSET NULL
ms.assetid: 410c5a6e-e957-4ecc-9e2d-e591cbc0bc4f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 14cade223de7014dd4a0c27295d3ff742d18af17
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="set-null-command"></a>SET NULL 命令
決定如何 ALTER TABLE SQL、 CREATE TABLE SQL 和插入-支援 null 值的 SQL 命令。  
  
## <a name="syntax"></a>語法  
  
```  
  
SET NULL ON | OFF  
```  
  
## <a name="arguments"></a>引數  
 ON  
 （預設的驅動程式，Visual FoxPro 的預設值是 OFF）。指定 ALTER TABLE 和 CREATE TABLE 所建立的資料表中的所有資料行允許 null 值。 在資料行的定義包含 NOT NULL 子句，您可以覆寫資料表中的資料行的 null 值支援。  
  
 也會指定，插入的 SQL 會插入 null 值插入-SQL VALUE 子句中不包含任何資料行。 插入的 SQL 會插入 null 值只允許 null 值的資料行。  
  
 OFF  
 指定 ALTER TABLE 和 CREATE TABLE 所建立的資料表中的所有資料行不會允許 null 值。 您可以指定 ALTER TABLE 和 CREATE TABLE 中的資料行的 null 值支援在資料行的定義中包含 NULL 子句。  
  
 也會指定，插入的 SQL 會插入空白值插入-SQL VALUE 子句中不包含任何資料行。  
  
## <a name="remarks"></a>備註  
 ALTER TABLE、 CREATE TABLE 和 INSERT-SQL 支援 SET NULL 會影響如何只在 null 值。 其他命令會受到 NULL 設定。  
  
## <a name="see-also"></a>另請參閱  
 [ALTER TABLE 的 SQL 命令](../../odbc/microsoft/alter-table-sql-command.md)   
 [建立資料表的 SQL 命令](../../odbc/microsoft/create-table-sql-command.md)   
 [插入的 SQL 命令](../../odbc/microsoft/insert-sql-command.md)

