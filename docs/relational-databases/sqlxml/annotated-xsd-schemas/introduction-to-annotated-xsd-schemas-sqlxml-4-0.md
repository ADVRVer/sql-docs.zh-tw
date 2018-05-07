---
title: 註解式的 XSD 結構描述 (SQLXML 4.0) 簡介 |Microsoft 文件
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- mapping schema [SQLXML], about mapping schema
- views [SQLXML]
- valid XSD schemas [SQLXML]
- annotations [SQLXML]
- XSD schemas [SQLXML], creating XML views
- annotated XSD schemas, creating XML views
- minimum XSD schema
- annotated XSD schemas, examples
- XML views [SQLXML]
ms.assetid: 15282db1-65c4-43be-bdb7-e9ef49cb33a2
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8b771edea6a71767e05e9d24c3ddd542bae2930c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="introduction-to-annotated-xsd-schemas-sqlxml-40"></a>註解式 XSD 結構描述簡介 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  您可以使用 XML 結構描述定義 (XSD) 語言來建立關聯式資料的 XML 檢視。 接著，您就可以使用 XML 路徑語言 (XPath) 查詢來查詢這些檢視。 這類似於使用 CREATE VIEW 陳述式來建立檢視，然後針對檢視指定 SQL 查詢。  
  
 XML 結構描述會描述 XML 文件的結構，而且也會描述文件中資料的各種條件約束。 針對結構描述指定 XPath 查詢時，傳回之 XML 文件的結構取決於執行 XPath 查詢所針對的結構描述。  
  
 在 XSD 結構描述中，  **\<schema >** 元素會括住整個結構描述，則所有元素宣告都必須都包含在 **\<schema >** 項目。 您可以描述定義中的命名空間的屬性結構描述所在並做為結構描述中屬性的命名空間 **\<schema >** 項目。  
  
 必須包含有效的 XSD 結構描述 **\<schema >** 項目定義，如下所示：  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<!-- additional schema definitions here -->  
</xsd:schema>  
```  
  
 **\<Schema >** 元素衍生自 XML 結構描述命名空間規格，在http://www.w3.org/2001/XMLSchema。  
  
## <a name="annotations-to-the-xsd-schema"></a>XSD 結構描述的註解  
 您可以使用 XSD 結構描述搭配描述資料庫對應的註解、查詢資料庫，並且以 XML 文件的格式傳回結果。 提供註解的目的是要將 XSD 結構描述對應至資料庫資料表和資料行。 您可以針對 XSD 結構描述所建立的 XML 檢視指定 XPath 查詢來查詢資料庫，並以 XML 的格式取得結果。  
  
> [!NOTE]  
>  在 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 中，XSD 結構描述語言支援 [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] 中註解式 XML-Data Reduced (XDR) 結構描述語言所導入的註解。 註解式 XDR 在 SQLXML 4.0 中已被取代。  
  
 在關聯式資料庫的內容中，將任意的 XSD 結構描述對應到關聯式存放區相當實用。 封存的其中一種方式是為 XSD 結構描述註解。 包含註解 XSD 結構描述指*對應結構描述*，其中提供有關如何 XML 資料對應到關聯式存放區的資訊。 實際上，對應結構描述就是關聯式資料的 XML 檢視。 這些對應可用於擷取關聯式資料做為 XML 文件。  
  
## <a name="namespace-for-annotations"></a>註解的命名空間  
 在 XSD 結構描述，使用命名空間指定註解**描述 urn:-microsoft-: mapping-schema-結構描述**。 下列範例所示，指定的命名空間最簡單的方式是指定在 **\<schema >** 標記。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
...  
</xsd:schema>  
```  
  
 所使用的命名空間前置詞是任意的。 在此文件**sql**前置詞用於代表註解命名空間，並區別此命名空間中的註解中其他命名空間。  
  
## <a name="example-of-an-annotated-xsd-schema"></a>註解式 XSD 結構描述的範例  
 在下列範例中，XSD 結構描述包含 **\<Person.Contact >** 項目。 **\<員工 >** 項目具有**ContactID**屬性和 **\<FirstName >** 和 **\<LastName >** 子項目：  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <xsd:element name="Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"    
                     type="xsd:string" />   
        <xsd:element name="LName"  
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID" type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 然後，將註解加入至這個 XSD 結構描述，以便將其元素和屬性對應至資料庫資料表和資料行：  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Contact" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"  
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID"   
                       sql:field="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 對應結構描述中**\<連絡人 >** 元素會對應至 AdventureWorks 範例資料庫中的 Person.Contact 資料表使用**sql: relation**註解。 ConID、 FName 和 LName 屬性會使用對應至 Person.Contact 資料表中的 ContactID、 FirstName 和 LastName 資料行**sql: field**註解。  
  
 此註解式 XSD 結構描述會提供關聯式資料的 XML 檢視。 您可以使用 XPath 語言來查詢這個 XML 檢視。 XPath 查詢會傳回 XML 文件當做結果，而不是 SQL 查詢所傳回的資料列集。  
  
> [!NOTE]  
>  在對應結構描述中，指定的關聯式值 (例如，資料表名稱和資料行名稱) 是否區分大小寫會取決於 SQL Server 是否使用區分大小寫的定序設定。 如需詳細資訊，請參閱 [Collation and Unicode Support](../../../relational-databases/collations/collation-and-unicode-support.md)。  
  
## <a name="other-resources"></a>其他資源  
 您可以在下列網站上找到有關 XML 結構描述定義語言 (XSD)、XML 路徑語言 (XPath) 和可延伸樣式表語言轉換 (XSLT) 的資訊：  
  
-   XML 結構描述第 0 部分： 入門，W3C 建議事項 (http://www.w3.org/TR/xmlschema-0/)  
  
-   XML 結構描述第 1 部分： 結構、 W3C 建議事項 (http://www.w3.org/TR/xmlschema-1/)  
  
-   XML 結構描述第 2:Datatypes，W3C 建議事項 (http://www.w3.org/TR/xmlschema-2/)  
  
-   XML 路徑語言 (XPath) (http://www.w3.org/TR/xpath)  
  
-   XSL 轉換 (XSLT) (http://www.w3.org/TR/xslt)  
  
## <a name="see-also"></a>另請參閱  
 [註解式結構描述的安全性考量&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)   
 [註解式 XDR 結構描述&#40;SQLXML 4.0 中已被取代&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)  
  
  
