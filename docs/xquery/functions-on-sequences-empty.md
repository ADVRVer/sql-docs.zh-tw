---
title: empty 函數（XQuery） |Microsoft Docs
description: 深入瞭解 XQuery 函式 empty （），此函式會傳回值，指出指定的專案序列是否為空的。
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- empty function
- fn:empty function
ms.assetid: 46da89a8-0cd9-4913-8521-4087589a04ba
author: rothja
ms.author: jroth
ms.openlocfilehash: c522e0756ca846558acbf6ac1b96c7d4abeef57e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85753563"
---
# <a name="functions-on-sequences---empty"></a>序列的相關函式 - empty
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

  如果 *$arg*的值是空的序列，則傳回 True。 否則，此函數會傳回 False。  
  
## <a name="syntax"></a>語法  
  
```  
  
fn:empty($arg as item()*) as xs:boolean  
```  
  
## <a name="arguments"></a>引數  
 *$arg*  
 項目序列。 如果序列是空的，則函數會傳回 True。 否則，此函數會傳回 False。  
  
## <a name="remarks"></a>備註  
 不支援**fn： exists （）** 函數。 或者，也可以使用**not （）** 函數。  
  
## <a name="examples"></a>範例  
 本主題針對 XML 實例提供 XQuery 範例，這些實例是儲存在 AdventureWorks 資料庫的各種**xml**類型資料行中。  
  
### <a name="a-using-the-empty-xquery-function-to-determine-if-an-attribute-is-present"></a>A. 使用 empty() XQuery 函數來決定是否出現屬性  
 在產品型號7的製造過程中，此查詢會傳回所有沒有**MachineHours**屬性的工作中心位置。  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     for $i in /AWMI:root/AWMI:Location[empty(@MachineHours)]  
     return  
       <Location  
            LocationID="{ ($i/@LocationID) }"  
            LaborHrs="{ ($i/@LaborHours) }" >  
            {   
              $i/@MachineHours  
            }    
       </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 以下是結果：  
  
```  
ProductModelID      Result          
-------------- ------------------------------------------  
7              <Location LocationID="30" LaborHrs="1"/>  
               <Location LocationID="50" LaborHrs="3"/>  
               <Location LocationID="60" LaborHrs="4"/>  
```  
  
 如果**MachineHour**屬性不存在，下列已稍微修改的查詢會傳回 "NotFound"：  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace p14="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     for $i in /p14:root/p14:Location  
     return  
       <Location  
            LocationID="{ ($i/@LocationID) }"  
            LaborHrs="{ ($i/@LaborHours) }" >  
            {   
                 if (empty($i/@MachineHours)) then  
                    attribute MachineHours { "NotFound" }  
                 else  
                    attribute MachineHours { data($i/@MachineHours) }  
            }    
       </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 以下是結果：  
  
```  
ProductModelID Result                         
-------------- -----------------------------------  
7                
  <Location LocationID="10" LaborHrs="2.5" MachineHours="3"/>  
  <Location LocationID="20" LaborHrs="1.75" MachineHours="2"/>  
  <Location LocationID="30" LaborHrs="1" MachineHours="NotFound"/>  
  <Location LocationID="45" LaborHrs="0.5" MachineHours="0.65"/>  
  <Location LocationID="50" LaborHrs="3" MachineHours="NotFound"/>  
  <Location LocationID="60" LaborHrs="4" MachineHours="NotFound"/>  
```  
  
## <a name="see-also"></a>另請參閱  
 [針對 xml 資料類型的 XQuery 函數](../xquery/xquery-functions-against-the-xml-data-type.md)   
 [exist&#40;&#41; 方法 &#40;xml 資料類型&#41;](../t-sql/xml/exist-method-xml-data-type.md)  
  
  
