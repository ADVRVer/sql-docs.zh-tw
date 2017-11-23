---
title: "註解式結構描述的安全性考量 (SQLXML 4.0) |Microsoft 文件"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- mapping schema [SQLXML], security
- annotated XDR schemas, security
- XDR schemas [SQLXML], security
- annotations [SQLXML]
- annotated XSD schemas, security
- SQLXML, annotated XSD schemas
- SQLXML, annotated XDR schemas
- security [SQLXML], annotated schemas
- XSD schemas [SQLXML], security
ms.assetid: 7d7e44dc-b6d3-4e0f-95c7-8f99930c94f2
caps.latest.revision: "22"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7cc1cfae87ada312c674c1c2f124761d3d3111f5
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="annotated-schema-security-considerations-sqlxml-40"></a>註解式結構描述安全性考量 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]以下是使用註解式結構描述安全性指導方針：  
  
-   請避免在對應結構描述中使用預設的對應。 預設對應會在產生的 XML 文件中公開資料庫資訊 (資料表和資料行名稱)，因為根據預設，元素名稱會對應到資料表名稱，而屬性名稱則對應到資料行名稱。 因此，看到 XML 文件的任何使用者都可以存取資料庫中的資料表和資料行資訊，因此暴露潛在的安全性風險。 為避免此風險，請在結構描述中指定任意的元素和屬性名稱，並使用註解將其明確地對應到資料表和資料行。 如需使用預設對應，當您建立 XSD 結構描述的詳細資訊，請參閱[預設對應的 XSD 元素和屬性對資料表和資料行 &#40;SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md).  
  
-   使用註解指定的明確對應會公開資料庫資訊 (例如資料表名稱和資料行名稱)。 因此，您可能不會想要公開地提供這些結構描述。  
  
-   某些查詢，例如針對對應結構描述利用遞迴指定 (使用指定**最大深度**設定較高的值為註解) 可能需要較長的時間執行。 您可以選擇性地指定逾時限制的命令逾時屬性設定 （以秒為單位）。 例如：  
  
    ```  
    cn.Open "Provider=SQLOLEDB;Server=localhost;Database=tempdb;Integrated Security=SSPI;Command Properties='Command Time Out=50';"  
    ```  
  
## <a name="see-also"></a>請參閱＜  
 [SQLXML 4.0 中的註解式 XSD 結構描述](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xsd-schemas-in-sqlxml-4-0.md)  
  
  
