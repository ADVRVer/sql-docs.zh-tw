---
title: 使用含更新計數的預存程序 | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 64cf4877-5995-4bfc-8865-b7618a5c8d01
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 851974955b9311efc149ecdff310bfbb1d8869fc
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2019
ms.locfileid: "69026932"
---
# <a name="using-a-stored-procedure-with-an-update-count"></a>使用含更新計數的預存程序

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

為了使用預存程序來修改 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中的資料，[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 提供 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) 類別。 使用 SQLServerCallableStatement 類別時，您可以呼叫會修改資料庫中所含資料的預存程序，並傳回受影響的資料列計數 (也稱為更新計數)。

使用 SQLServerCallableStatement 類別設定預存程序的呼叫之後，接著便可以使用 [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) 或 [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) 方法呼叫預存程序。 executeUpdate 方法會傳回 **int** 值，其中包含預存程序所影響的資料列數目，但是 execute 方法則不會傳回該值。 如果使用 execute 方法並想要取得受影響的資料列計數，則您可以在執行預存程序之後呼叫 [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) 方法。

> [!NOTE]  
> 如果想要 JDBC 驅動程式傳回所有更新計數 (包括任何可能已引發之觸發程序所傳回的更新計數)，請將 lastUpdateCount 連接字串屬性設為 "false"。 如需 lastUpdateCount 屬性的詳細資訊, 請參閱[設定連接屬性](../../connect/jdbc/setting-the-connection-properties.md)。

例如，您可以在 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] 範例資料庫中建立下列資料表和預存程序，同時插入範例資料：

```sql
CREATE TABLE TestTable
   (Col1 int IDENTITY,
    Col2 varchar(50),
    Col3 int);  

CREATE PROCEDURE UpdateTestTable  
   @Col2 varchar(50),  
   @Col3 int  
AS  
BEGIN  
   UPDATE TestTable  
   SET Col2 = @Col2, Col3 = @Col3  
END;  
INSERT INTO dbo.TestTable (Col2, Col3) VALUES ('b', 10);  
```

在下列範例中，[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] 範例資料庫的開啟連線會傳入至函式、將 execute 方法用於呼叫 UpdateTestTable 預存程序，接著會使用 getUpdateCount 方法傳回預存程序所影響的資料列計數。

[!code[JDBC#UsingSprocWithUpdateCount1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_0_1.java)]

## <a name="see-also"></a>另請參閱

[搭配預存程序使用陳述式](../../connect/jdbc/using-statements-with-stored-procedures.md)
