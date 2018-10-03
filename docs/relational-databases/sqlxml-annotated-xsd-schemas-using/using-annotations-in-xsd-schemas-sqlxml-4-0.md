---
title: 使用 XSD 結構描述 (SQLXML 4.0) 中的註釋 |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, about annotated XSD schemas
- annotations [SQLXML]
- relationships [SQLXML]
- relationships [SQLXML], hierarchical relationships
- hierarchical relationships [SQLXML]
- mapping schema [SQLXML], scenarios for using
ms.assetid: 78f318a4-7a36-473b-9852-a4bae6940ce5
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 80aa9ae1fd19f9f7ed0e90436604095f091ca781
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47618328"
---
# <a name="using-annotations-in-xsd-schemas-sqlxml-40"></a>在 XSD 結構描述中使用註釋 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0 中，XSD 結構描述語言以類似 XML-Data Reduced (XDR) 結構描述語言所推出之註解的方式支援註解。 在 XSD 中有 XDR 不支援的其他註解。  
  
 這些註解可以在 XSD 結構描述內，用於指定 XML 到關聯式的對應。 這包括 XSD 結構描述中的元素和屬性到資料庫中的資料表 (檢視) 和資料行之間的對應。  
  
 如果您沒有指定註解，就會使用預設對應。 根據預設，包含複雜類型的 XSD 元素會對應到指定之資料庫中的資料表 (檢視) 名稱，而包含簡單類型的元素或屬性會對應到具有相同名稱的資料行，做為元素或屬性。  
  
 這些註解也可以用於指定 XML 中的階層式關聯性以代表資料庫中的關聯性，因為 XSD 結構描述只是關聯式資料的 XML 檢視。  
  
 本節提供您可搭配 XSD 結構描述一起使用之註解的描述以及其使用方式的範例。  
  
> [!NOTE]  
>  本節中的所有範例都會根據每個範例中所描述的註解式 XSD 結構描述，指定簡單的 XPath 查詢。 同時會假設您熟悉 XPath 語言。  
  
## <a name="in-this-section"></a>本節內容  
 [XSD 註解&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/xsd-annotations-sqlxml-4-0.md)  
 列出您可以搭配 XSD 結構描述使用的註解、其描述，以及適用於 XDR 的相等註解。  
  
 [XSD 元素和屬性對資料表和資料行的預設對應&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
 說明預設對應，並提供與預設對應相關之工作的範例。  
  
 [XSD 元素和屬性對資料表和資料行的明確對應&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns.md)  
 說明使用明確的對應**sql: relation**並**sql: field**註解，並提供範例。  
  
 [關聯性使用 sql: relationship 指定&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
 描述與提供的範例**sql: relationship**註釋。  
  
 [Sql: relationship 指定 sql: inverse 屬性&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)  
 描述**sql: inverse**註釋。  
  
 [建立常數項目使用 sql: is-constant&lt &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)  
 描述與提供的範例**sql: is-constant&lt**註釋。  
  
 [結構描述元素排除產生 XML 文件使用 sql： 對應&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)  
 描述與提供的範例**sql： 對應**註釋。  
  
 [篩選值使用 sql: limit-value-欄位和 sql: limit-value-值&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/filtering-values-using-sql-limit-field-and-sql-limit-value-sqlxml-4-0.md)  
 描述與提供的範例**sql: limit-value-欄位**並**sql: limit-value-值**註解。  
  
 [識別索引鍵資料行使用 sql: key-fields 來-欄位&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)  
 描述與提供的範例**sql: key-fields 來-欄位**註釋。  
  
 [目標命名空間使用 targetNamespace 屬性來指定&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
 描述與提供的範例**targetNamespace**屬性。  
  
 [有效的 ID、 IDREF 和 IDREFS 類型屬性使用 sql: prefix 建立&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)  
 描述與提供的範例**sql: prefix**註釋。  
  
 [資料類型強制型轉和 sql: datatype 註解&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)  
 描述與提供的範例**sql: datatype**註釋。  
  
 [將 XSD 資料類型對應到 XPath 資料類型&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/mapping-xsd-data-types-to-xpath-data-types-sqlxml-4-0.md)  
 提供比較 XSD、XDR 與 XPath 資料類型的資料表，並列出相關的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 轉換。  
  
 [CDATA 區段使用 sql: use-cdata 建立-cdata &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)  
 描述與提供的範例**sql: use-cdata-資料**註釋。  
  
 [要求的 URL 參考 BLOB 資料使用 sql： 編碼&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)  
 描述與提供的範例**sql： 編碼**註釋。  
  
 [擷取未耗用資料使用 sql: overflow-field-欄位&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/retrieving-unconsumed-data-using-the-sql-overflow-field-sqlxml-4-0.md)  
 描述與提供的範例**sql: overflow-field-欄位**註釋。  
  
 [使用 sql:hide 來隱藏項目和屬性](../../relational-databases/sqlxml-annotated-xsd-schemas-using/hiding-elements-and-attributes-by-using-sql-hide.md)  
 描述與提供的範例**sql: hide**註釋。  
  
 [使用 sql:identity 和 sql:guid 註解](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)  
 描述與提供的範例**sql: identity**並**sql: guid**註解。  
  
 [使用 sql:max-depth 來指定遞迴關聯性的深度](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)  
 描述與提供的範例**sql: max-depth-深度**註釋。  
  
## <a name="see-also"></a>另請參閱  
 [註解式結構描述安全性考量&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)  
  
  
