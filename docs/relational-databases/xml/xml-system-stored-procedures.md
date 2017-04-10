---
title: "XML 系統預存程序 | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "系統預存程序 [SQL Server], XML"
  - "sp_xml_removedocument"
  - "OPENXML 陳述式, 系統預存程序"
  - "sp_xml_preparedocument"
  - "XML [SQL Server], 系統預存程序"
ms.assetid: e60c7f85-6823-4d28-93d6-b053d08cc830
caps.latest.revision: 27
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 27
---
# XML 系統預存程序
  SQL Server 提供以下系統預存程序，可與 OPENXML 一起使用：  
  
-   [sp_xml_preparedocument &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql.md)  
  
-   [sp_xml_removedocument &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql.md)  
  
 若要利用 OPENXML 來寫入查詢，您必須先呼叫 **sp_xml_preparedocument** 來建立 XML 文件的內部表示。 預存程序將控制代碼傳回 XML 文件的內部表示。 接著將此控制代碼傳遞至 OPENXML。 OPENXML 提供以 XPath 為基礎的文件之資料列集檢視。 具體而言，這是一個資料列模式以及一或多個資料行模式。  
  
> [!NOTE]  
>  由 **sp_xml_preparedocument** 傳回的文件控制代碼在工作階段持續時間內是有效的。  
  
 可呼叫 **sp_xml_removedocument** 系統預存程序來從記憶體中移除 XML 文件的內部表示法。  
  
## 另請參閱  
 [OPENXML &#40;Transact-SQL&#41;](../../t-sql/functions/openxml-transact-sql.md)   
 [OPENXML &#40;SQL Server&#41;](../../relational-databases/xml/openxml-sql-server.md)  
  
  