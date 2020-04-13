---
title: 預設包含 NULL 值的資料行 | Microsoft 文件
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- columns [XML in SQL Server], null default value
ms.assetid: 9381c07f-6887-4a62-9730-32661f9aa87c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f7672d59b2355c0733a5e26da6217fbabf729c6a
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664703"
---
# <a name="columns-that-contain-a-null-value-by-default"></a>預設包含 NULL 值的資料行

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

依預設，資料行中的 Null 值會與缺少的屬性、節點或元素相對應。 此預設行為可使用 ELEMENTS XSINIL 關鍵字片語覆寫。 此片語會要求項目中心 XML。 這表示傳回的結果中會明確指出 Null 值。 這些項目將不具有任何值。

下列 Transact-SQL SELECT 範例中會顯示 ELEMENTS XSINIL 片語。

```sql
SELECT EmployeeID as "@EmpID",   
       FirstName  as "EmpName/First",   
       MiddleName as "EmpName/Middle",   
       LastName   as "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
  AND  E.EmployeeID=1
FOR XML PATH, ELEMENTS XSINIL;
```  
  
 下列範例會顯示結果。 請注意如果沒有指定 XSINIL，將不會有 <`Middle`> 元素。  
  
```xml
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a>另請參閱  
 [搭配 FOR XML 使用 PATH 模式](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
