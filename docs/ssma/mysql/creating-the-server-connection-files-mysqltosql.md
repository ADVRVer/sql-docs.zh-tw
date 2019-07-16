---
title: 建立伺服器連線檔案 (MySQLToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Server connection file validation
- Server connection files
ms.assetid: df0e970c-da0b-4118-b359-c9dcbbad16d6
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 1df2c474afa5e062dfa22cf05af6b0edf036f768
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68103041"
---
# <a name="creating-the-server-connection-files-mysqltosql"></a>建立伺服器連線檔案 (MySQLToSQL)
伺服器一節的指令碼檔案或不同的伺服器連線檔案中，可以指定伺服器的資訊。 伺服器連接檔案的命令列參數即`-c <serverconnectionfile>`。 如果存在於指令碼檔案與伺服器連線檔案相同的伺服器識別碼，則會視為在指令碼檔案中的伺服器定義。  
  
**範例:**  
  
```xml  
<!--Sample of server connection file commands -->  
  
<mysql name ="<source-server-unique-name>">  
  
   <standard-mode>  
  
      <server value ="<server-name>"/>  
  
      <user-id value ="<user-name>"/>  
  
      <password value ="<password>"/>  
  
      <port value ="<port>"/>  
  
   </standard-mode>  
  
</mysql>  
```  
  
```xml  
<!--Connection to SQL Server-->  
  
<sql-server name="<target-server-unique-name>">  
  
   <sql-server-authentication>  
  
      <server value="<server-name>"/>  
  
      <database value="<database-name>"/>  
  
      <user-id value="<user-name>"/>  
  
      <password value="<password>"/>  
  
      <encrypt value="<true/false>"/>  
  
      <trust-server-certificate value="<true/false>"/>  
  
   </sql-server-authentication>  
  
</sql-server>  
```  
  
```xml  
<!--Connection to SQL Azure-->  
  
<sql-azure name="<target-server-unique-name>">  
  
   <server value="<server-name>"/>  
  
   <database value="<database-name>"/>  
  
   <user-id value="<user-name>"/>  
  
   <password value="<password>"/>  
  
</sql-azure>  
```  
  
## <a name="server-connection-file-validation"></a>伺服器連線檔案驗證  
使用者可以輕鬆地驗證他/她伺服器連線檔案對結構描述定義檔 **'M2SSConsoleScriptServersSchema.xsd'** 可用 [結構描述] 資料夾中。  
  
## <a name="next-step"></a>下一個步驟  
操作主控台的下一個步驟是[執行 SSMA 主控台&#40;MySQLToSQL&#41;](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md)  
  
## <a name="see-also"></a>另請參閱  
[執行 SSMA 主控台 (MySQL)](https://msdn.microsoft.com/e3e9f7e4-0619-4861-a202-3d5d39953b26)  
  
