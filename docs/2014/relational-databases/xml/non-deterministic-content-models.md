---
title: 不具決定性的內容模型 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- non-deterministic content models
- content models [XML in SQL Server]
ms.assetid: 9d4513e7-dd19-4491-b7c7-28bc7c2f8589
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: df49312f86513e1860fbb3bc14cd33ca1edc845e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48113755"
---
# <a name="non-deterministic-content-models"></a>不具決定性的內容模型
  在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 (SP1) 之前， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會拒絕具有不具決定性之內容模型的 XML 結構描述。  
  
 但是從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1 開始，即使出現次數條件約束為 0、1 或未受約束，仍可接受不具決定性的內容模型。  
  
## <a name="example-non-deterministic-content-model-rejected"></a>範例：拒絕不具決定性的內容模型  
 下列範例會嘗試建立具有不具決定性之內容模型的 XML 結構描述。 此程式碼會失敗，因為 `<root>` 元素是否應該具有兩個 `<a>` 元素的序列，或者 `<root>` 元素是否應該具有兩個序列 (每個序列含有一個 `<a>` 元素) 並不明確。  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="1" maxOccurs="2">  
                <element name="a" type="string" minOccurs="1" maxOccurs="2"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
 將出現次數條件約束移動至唯一位置，即可修正結構描述。 例如，可將條件約束移動至包含順序物件：  
  
```  
<sequence minOccurs="1" maxOccurs="4">  
    <element name="a" type="string" minOccurs="1" maxOccurs="1"/>  
</sequence>  
```  
  
 或者，可將條件約束移動至內含元素：  
  
```  
<sequence minOccurs="1" maxOccurs="1">  
     <element name="a" type="string" minOccurs="1" maxOccurs="4"/>  
</sequence>  
```  
  
## <a name="example-non-deterministic-content-model-accepted"></a>範例：接受不具決定性的內容模型  
 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SP1 之前的 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 版本中，下列結構描述會遭到拒絕。  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="0" maxOccurs="unbounded">  
                <element name="a" type="string" minOccurs="0" maxOccurs="1"/>  
                <element name="b" type="string" minOccurs="1" maxOccurs="unbounded"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [伺服器上 XML 結構描述集合的需求與限制](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
