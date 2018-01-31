---
title: "使用 sqlcmd 執行 Transact-SQL 指令碼檔案 | Microsoft Docs"
ms.custom: 
ms.date: 07/15/2016
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
caps.latest.revision: 
author: mightypen
ms.author: genemi
manager: craigg
ms.workload: Active
ms.openlocfilehash: 815b9a2deb8dd4c3f81e46257ae3756eeefe9512
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2018
---
# <a name="sqlcmd---run-transact-sql-script-files"></a>sqlcmd - 執行 Transact-SQL 指令碼檔案
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] 您可以使用 **sqlcmd** 來執行 Transact-SQL 指令碼檔案。 Transact-SQL 指令碼檔案是一個文字檔，可以包含 Transact-SQL 陳述式、 **sqlcmd** 命令和指令碼變數的組合。  

## <a name="create-a-script-file"></a>建立指令碼檔案  
 若要使用 [記事本] 建立簡單的 Transact-SQL 指令碼檔案，請遵循下列步驟：  
  
1.  按一下 [開始]，依序指向 [所有程式] 和 [附屬應用程式]，然後按一下 [記事本]。  
  
2.  將下列 Transact-SQL 程式碼複製並貼到 [記事本] 中：  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT p.FirstName + ' ' + p.LastName AS 'Employee Name',  
    a.AddressLine1, a.AddressLine2 , a.City, a.PostalCode   
    FROM Person.Person AS p   
       INNER JOIN HumanResources.Employee AS e   
            ON p.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.BusinessEntityAddress bea   
            ON bea.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.Address AS a   
            ON a.AddressID = bea.AddressID;  
    GO  
    ```  
  
3.  將檔案儲存成 C 磁碟機中的 **myScript.sql** 。  
  
## <a name="run-the-script-file"></a>執行指令碼檔案  
  
1.  開啟 [命令提示字元] 視窗。  
  
2.  在命令提示字元視窗中，輸入： **sqlcmd -S myServer\instanceName -i C:\myScript.sql**  
  
3.  按 ENTER 鍵。  
  
 此時會在命令提示字元視窗中，顯示一份 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] 員工姓名和地址的清單。  

## <a name="save-the-output-to-a-text-file"></a>將輸出儲存到文字檔
  
1.  開啟 [命令提示字元] 視窗。  
  
2.  在命令提示字元視窗中，輸入： **sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt**  
  
3.  按 ENTER 鍵。  
  
 此時在命令提示字元視窗中不會傳回任何輸出。 而是會將輸出送往 EmpAdds.txt 檔。 您可以開啟 EmpAdds.txt 檔來確認這份輸出。  
  
## <a name="see-also"></a>另請參閱  
 [啟動 sqlcmd 公用程式](../../relational-databases/scripting/sqlcmd-start-the-utility.md)   
 [sqlcmd 工用程式](../../tools/sqlcmd-utility.md)  
  
  
