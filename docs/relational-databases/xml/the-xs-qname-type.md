---
title: xs:QName 類型 | Microsoft Docs
description: 了解如何使用 xs:QName 類型作為 XML 結構描述限制元素，或作為聯集的成員類型。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xs:QName type
ms.assetid: 72c5bfde-b0b2-4372-bf36-97ba930dea06
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 879ec2e1e4aaebfde4b3597df3d244380f2b4165
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758515"
---
# <a name="the-xsqname-type"></a>xs:QName 類型
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不支援使用 XML 結構描述限制元素且從 **xs:QName** 衍生的類型。 此外， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目前不支援 **QName** 為成員類型的聯集類型。  
  
## <a name="example"></a>範例  
 下列 `CREATE XML SCHEMA COLLECTION` 陳述式無法載入 XML 結構描述，因為它們將 `xs:QName` 類型指定為聯集的成員類型：  
  
```  
CREATE XML SCHEMA COLLECTION QNameLimitation1 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:int xs:QName"/>  
    </xs:simpleType>  
</xs:schema>'  
GO  
  
CREATE XML SCHEMA COLLECTION QNameLimitation2 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:integer">  
   <xs:simpleType>  
    <xs:list itemType="xs:QName"/>  
   </xs:simpleType>  
  </xs:union>  
    </xs:simpleType>  
</xs:schema>'  
GO  
```  
  
 這兩個陳述式會因錯誤而導致失敗。  
  
## <a name="see-also"></a>另請參閱  
 [伺服器上 XML 結構描述集合的需求與限制](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
