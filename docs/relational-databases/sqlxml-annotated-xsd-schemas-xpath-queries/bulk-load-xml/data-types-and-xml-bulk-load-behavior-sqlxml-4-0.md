---
title: 資料型別和 XML 大量載入行為 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 38f4cfc90143830119e99ab607a51c1bf234bf21
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43065831"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>資料類型與 XML 大量載入行為 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  指定對應結構描述中的資料類型 (XSD 或 XDR 類型和**sql: datatype**) 通常會遭到忽略，下列情況除外：  
  
 在 XSD 中：  
  
-   如果類型是**dateTime**或是**時間**，您必須指定**sql: datatype**因為 XML 大量載入會執行資料轉換，再將資料傳送給 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   當您大量載入的資料行**uniqueidentifier**中輸入[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，而且 XSD 值是 GUID，其中包含大括號 （{和}），您必須指定**sql: datatype ="uniqueidentifier"** 至值插入資料行之前，請移除大括號。 如果**sql: datatype**未指定，則傳送值以大括弧和插入會失敗。  
  
 如需詳細資訊**sql: datatype**，請參閱[資料類型強制型轉和 sql: datatype 註解&#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)。  
  
 在 XDR 中：  
  
-   如果**dt: type**是**datetime**，**時間**， **dateTime.tz**，或**time.tz**，您必須同時指定**dt: type**並**sql: datatype**資料類型，因為它傳送至資料之前，XML 大量載入會執行資料轉換[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。  
  
-   如果 XML 資料型別的**uuid**， **sql: datatype**必須指定;**dt: type ="uuid"** 也是必要項，除非資料是字串資料。 如果您未指定**dt:uuid**，XML 大量載入會接受字串以大括弧 （並移除它們，如有需要）。  
  
-   如果 XML 資料**bin.hex、bin.base64**或是**bin.hex**，您必須指定使用的 XML 資料類型**dt: type**。 接著，XML 大量載入會將資料載入 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，做為資料的十六進位表示法。  
  
  
