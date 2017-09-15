---
title: "命令資料流 |Microsoft 文件"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command streams [ADO]
- streams [ADO], command
ms.assetid: 0ac09dbe-2665-411e-8fbb-d1efe6c777be
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1be2cc9528e62e548feb242b06686ad50a1753c8
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="command-streams"></a>命令資料流
ADO 有一律支援所指定的字串格式的命令輸入**CommandText**屬性。 或者，使用 ADO 2.7 或更新版本，您也可以使用資訊的資料流命令輸入藉由指定的資料流**CommandStream**屬性。 您可以指派 ADO**資料流**物件或任何支援 COM 的物件**IStream**介面。  
  
 命令資料流的內容會只傳遞從 ADO 提供者，因此您的提供者必須支援命令輸入資料流，才能使用這項功能。 例如，SQL Server 支援查詢形式的 XML 範本或 TRANSACT-SQL OpenXML 擴充功能。  
  
 因為必須提供者所解譯資料流的詳細資料，您必須指定命令用語設定**方言**屬性。 值**方言**是包含您的提供者會定義 GUID 的字串。 如需有關有效值的資訊**方言**支援您的提供者，請參閱您的提供者文件。  
  
## <a name="xml-template-query-example"></a>XML 範本查詢範例  
 下列範例是以 VBScript 與 Northwind 資料庫。  
  
 首先，初始化並開啟**資料流**會用來包含查詢的資料流的物件：  
  
```  
Dim adoStreamQuery  
Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
adoStreamQuery.Open  
```  
  
 查詢資料流的內容會 XML 範本查詢。  
  
 範本查詢需要 sql 所識別的 XML 命名空間的參考： 前置詞\<sql:query > 標記。 SQL SELECT 陳述式包含做為 XML 範本的內容，且指派給字串變數，如下所示：  
  
```  
sQuery = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<sql:query> SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME </sql:query>  
</ROOT>"  
```  
  
 接下來，將字串寫入資料流：  
  
```  
adoStreamQuery.WriteText sQuery, adWriteChar  
adoStreamQuery.Position = 0  
```  
  
 指派至 adoStreamQuery **CommandStream**的 ADO 屬性**命令**物件：  
  
```  
Dim adoCmd  
Set adoCmd  = Server.CreateObject("ADODB.Command"")  
adoCmd.CommandStream = adoStreamQuery  
```  
  
 指定的命令語言**方言**，表示 SQL Server OLE DB 提供者應如何解譯命令資料流。 以特定提供者 GUID 指定的方言：  
  
```  
adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
```  
  
 最後，執行查詢，並將結果傳回**資料錄集**物件：  
  
```  
Set objRS = adoCmd.Execute  
```
