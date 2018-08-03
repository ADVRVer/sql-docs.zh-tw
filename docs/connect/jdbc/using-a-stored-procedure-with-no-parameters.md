---
title: 使用不含輸入參數的預存程序 | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e9470a6d-a758-4c56-96ec-7b37139e36a7
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 157d6f1b3948dbe697afc5af018b197ede9fec9b
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279129"
---
# <a name="using-a-stored-procedure-with-no-parameters"></a>使用沒有參數的預存程序
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  您可呼叫之最簡單的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 預存程序為不含任何參數並傳回單一結果集的預存程序。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 提供 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) 類別，您可以使用此類別，呼叫此種類的預存程序並處理其傳回的資料。  
  
 當使用 JDBC 驅動程式呼叫不含參數的預存程序時，您必須使用 `call` SQL 逸出序列。 不含參數之 `call` 逸出序列的語法如下：  
  
 `{call procedure-name}`  
  
> [!NOTE]  
>  如需有關 SQL 逸出序列的詳細資訊，請參閱[使用 SQL 逸出序列](../../connect/jdbc/using-sql-escape-sequences.md)。  
  
 例如，在 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] 範例資料庫中建立下列預存程序：  
  
```sql
CREATE PROCEDURE GetContactFormalNames   
AS  
BEGIN  
   SELECT TOP 10 Title + ' ' + FirstName + ' ' + LastName AS FormalName   
   FROM Person.Contact  
END  
```  
  
 此預存程序會傳回包含一個資料資料行的單一結果集，亦即 Person.Contact 資料表中前 10 位連絡人的職稱、名字與姓氏的組合。  
  
 在下列範例中，[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] 範例資料庫的開啟連線會傳入至函式，並使用 [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) 方法，以呼叫 GetContactFormalNames 預存程序。  
  
```java  
public static void executeSprocNoParams(Connection con) throws SQLException {  
    try(Statement stmt = con.createStatement();) {  

        ResultSet rs = stmt.executeQuery("{call dbo.GetContactFormalNames}");  
        while (rs.next()) {  
            System.out.println(rs.getString("FormalName"));  
        }  
    }  
}
```  
  
## <a name="see-also"></a>另請參閱  
 [搭配使用陳述式與預存程序](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  
