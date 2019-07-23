---
title: 使用多個結果集 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ab6a3cfa-073b-44e9-afca-a8675cfe5fd1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c471f74fc8e1029cfeaad06b564ea4a9b6641171
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68005968"
---
# <a name="using-multiple-result-sets"></a>使用多個結果集

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

使用會傳回多個結果集的內嵌 SQL 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預存程序時，[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 會在 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) 類別中提供 [getResultSet](../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md) 方法，可用於擷取每一組傳回的資料。 此外，執行會傳回多個結果集的陳述式時，您還可以使用 SQLServerStatement 類別的 [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) 方法，因為它會傳回**布林值**值，指出所傳回的值是結果集還是更新計數。

如果 execute 方法傳回 **true**，表示執行的陳述式傳回的是一或多個結果集。 呼叫 getResultSet 方法，即可存取第一個結果集。 若要判斷是否有多個結果集可供使用，可呼叫 [getMoreResults](../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md) 方法，如果有多個可用的結果集，則這個方法會傳回值為 **true** 的**布林值**值。 如果有多個結果集可供使用，您可以再次呼叫 getResultSet 方法進行存取，持續進行這個處理序一直到處理完所有結果集為止。 如果 getMoreResults 方法傳回**false**, 則沒有其他要處理的結果集。

如果 execute 方法傳回 **false**，表示執行的陳述式傳回的是更新計數值，而您可以呼叫 [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) 方法來擷取該值。

> [!NOTE]  
> 如需更新計數的詳細資訊, 請參閱[使用具有更新計數的預存](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md)程式。

在下列範例中，[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] 範例資料庫的開啟連線會傳遞至函式，並建構一個 SQL 陳述式，以在執行時傳回兩個結果集：

[!code[JDBC#UsingMultipleResultSets1](../../connect/jdbc/codesnippet/Java/using-multiple-result-sets_1.java)]

在此例中，已知傳回的結果集數量為二。 不過，即使傳回未知數量的結果集 (例如呼叫預存程序時)，此程式碼的撰寫方式仍可處理所有的結果集。 若要查看呼叫會傳回多個結果集與更新值的預存程序範例，請參閱[處理複雜陳述式](../../connect/jdbc/handling-complex-statements.md)。

> [!NOTE]  
> 當您對 SQLServerStatement 類別的 getMoreResults 方法進行呼叫時, 先前傳回的結果集會隱含地關閉。

## <a name="see-also"></a>另請參閱

[搭配使用陳述式與 JDBC Driver](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)
