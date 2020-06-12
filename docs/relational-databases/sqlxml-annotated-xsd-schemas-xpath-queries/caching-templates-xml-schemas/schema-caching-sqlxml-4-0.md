---
title: 架構快取（SQLXML）
description: 瞭解如何使用登錄機碼來明確控制架構快取，並改善 SQLXML 4.0 中 XPath 查詢的效能。
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- schemas [SQLXML]
ms.assetid: 7e5fda21-b435-41fd-b637-8b616560a93f
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ca7eb937f75575dd34e1857209605aeb74a2d1d6
ms.sourcegitcommit: 9921501952147b9ce3e85a1712495d5b3eb13e5b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84215795"
---
# <a name="schema-caching-sqlxml-40"></a>結構描述快取 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  透過 XML for Microsoft SQL Server 2000 Web Release 1、Microsoft SQLXML 2.0 和 SQLXML 3.0 的並行安裝，您可以使用下列登錄機碼，明確地控制所有版本中的結構描述快取：  
  
 Web Release 1：  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXMLX\SchemaCacheSize  
```  
  
 SQLXML 2.0：  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML2\SchemaCacheSize  
```  
  
 SQLXML 3.0：  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML3\SchemaCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 如需並存安裝的詳細資訊，請參閱[SQLXML 4.0 SP1 的新功能](../../../relational-databases/sqlxml/what-s-new-in-sqlxml-4-0-sp1.md)。  
  
 結構描述快取能大幅提升 XPath 查詢的效能。 當 XPath 查詢針對對應結構描述執行時，結構描述會儲存在記憶體中，而且會在記憶體中建立所需的資料結構。 如果設定結構描述快取，結構描述仍會保留在記憶體中，藉以提升後續 XPath 查詢的效能。  
  
 您可以在登錄中加入上述機碼來設定結構描述快取大小  
  
 結構描述大小應該根據可用的記憶體以及您要使用的結構描述數目來設定。 預設的**SchemaCacheSize**大小為31。 如果您將**SchemaCacheSize**設定為較高，則會使用較多的記憶體。 因此，如果結構描述存取速度似乎緩慢，您可以增加快取大小，或者如果記憶體不足，則減少快取大小。  
  
 基於效能考慮，建議您將**SchemaCacheSize**設定為高於您通常使用的對應架構數目。 隨著架構數目的增加，如果**SchemaCacheSize**小於您擁有的架構數目，效能就會降低。  
  
> [!NOTE]  
>  在開發期間，建議您不要快取結構描述，因為您對結構描述所做的變更，約有兩分鐘不會反映在快取中。  
  
## <a name="see-also"></a>另請參閱  
 [&#40;SQLXML 4.0&#41;的範本快取](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/template-caching-sqlxml-4-0.md)   
 [XSL Caching &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
  
  
