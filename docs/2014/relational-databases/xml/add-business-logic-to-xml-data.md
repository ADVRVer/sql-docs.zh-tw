---
title: 將商務邏輯新增至 XML 資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business logic [XML]
ms.assetid: 0877fb38-f1a2-43d8-86cf-4754be224dc1
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: bf3e24dd3fe06a06b26adcbfcbf9da57d5b6916a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36030724"
---
# <a name="add-business-logic-to-xml-data"></a>將商務邏輯加入至 XML 資料
  將商務邏輯加入至 XML 資料的方法有好幾種：  
  
-   您可以撰寫資料列或資料行條件約束，以在插入及修改 XML 資料時，強制執行網域專屬的條件約束。  
  
-   您可以在 XML 資料行上撰寫觸發程序，當您在資料行中插入或更新值時，即引發該觸發程序。 觸發程序可包含網域專屬的驗證規則，或是擴展屬性資料表。  
  
-   Database Engine 包含執行 Managed 程式碼的能力。 您可以使用這項 Common Language Runtime (CLR) 整合功能來撰寫要接收 XML 值的 Managed 程式碼函數，並使用 System.Xml 命名空間所提供的 XML 處理功能。 例如，將 XSL 轉換套用至 XML 資料。 或者，您可以將 XML 還原序列化成一個或多個 Managed 類別，並使用 Managed 程式碼來加以操作。  
  
-   您可以撰寫 Transact-SQL 預存程序及函數，以針對您的商業需求開始處理 XML 資料行。  
  
## <a name="example-applying-xsl-transformation"></a>範例：套用 XSL 轉換  
 CLR 函數，請考慮**transformxml （)** 接受`xml`資料類型執行個體和儲存在檔案中的 XSL 轉換該轉換套用至 XML 資料之後，，然後在結果中傳回已轉換的 XML。 以下是用 C# 來撰寫的基本架構函數：  
  
```  
public static SqlXml TransformXml (SqlXml XmlData, string xslPath) {  
   // Load XSL transformation  
   XslCompiledTransform xform = new XslCompiledTransform();  
   XPathDocument xslDoc = new XPathDocument (xslPath);  
   xform.Load(xslDoc);  
  
   // Load XML data   
   XPathDocument xDoc = new XPathDocument (XmlData.CreateReader());  
  
   // Return the transformed value  
   MemoryStream xsltResult = new MemoryStream();  
   xform.Transform(xDoc, null, xsltResult);  
   SqlXml retSqlXml = new SqlXml(xsltResult);  
   return (retSqlXml);  
}   
```  
  
 在註冊完組件，並建立使用者定義的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 函數之後 ( **SqlXslTransform()** 對應到 **TransformXml()**)，即可從 Transact-SQL 來叫用該函數，如下列查詢所示：  
  
```  
SELECT SqlXslTransform (xCol, 'C:\MyFile\xsltransform.xsl')  
FROM    T  
WHERE  xCol.exist('/book/title/text()[contains(.,"custom")]') =1;  
```  
  
 查詢結果包含已轉換之 XML 的資料列集。  
  
 與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 整合的 CLR 擴展了下列作業的可能性：將 XML 資料分解成資料表或屬性升級，以及在 System.Xml 命名空間中使用 Managed 類別來查詢 XML 資料。 如需詳細資訊，請參閱 [XML 資料 &#40;SQL Server&#41;](xml-data-sql-server.md)。  
  
  