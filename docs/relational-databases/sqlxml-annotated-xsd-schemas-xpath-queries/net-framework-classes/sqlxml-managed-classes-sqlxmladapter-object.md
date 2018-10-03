---
title: SqlXmlAdapter 物件 (SQLXML Managed 類別) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- void Update(DataSet ds) method
- SqlXmlAdapter object
- void Fill(DataSet ds) method
- SQLXML Managed Classes, SqlXmlAdapter object
- Managed Classes [SQLXML], SqlXmlAdapter object
ms.assetid: 0a16eddf-fc26-4d92-82d4-359b5fb905d5
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b7a34cae11dcb866b9ed78a456c560957823982f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796536"
---
# <a name="sqlxml-managed-classes---sqlxmladapter-object"></a>SQLXML 受控類別 - SqlXmlAdapter 物件
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  這個物件會提供一些方法，方便您與 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 中的資料集進行互動。 如需實用範例，請參閱 <<c0> [ 存取.NET 環境中的 SQLXML 功能](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/accessing-sqlxml-functionality-in-the-net-environment.md)。  
  
 SqlXmlAdapter 物件支援這些方法：  
  
 void Fill (DataSet ds)  
 將 .NET Framework 中的資料集填滿從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中擷取的 XML 資料。  
  
 void Update (DataSet ds)  
 從資料集中的資料，將更新套用至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的記錄。  
  
 SqlXmlAdapter 物件支援這些建構函式：  
  
```  
public SqlXmlAdapter(SqlXmlCommand  cmd)   
  
public SqlXmlAdapter(  
                     string commandText,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                      )   
  
public SqlXmlAdapter(  
                     Stream commandStream,   
                     SqlXmlCommandType cmdType,   
                     string connectionString  
                     )   
```  
  
## <a name="see-also"></a>另請參閱  
 [SqlXmlCommand 物件&#40;SQLXML Managed 類別&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlcommand-object.md)   
 [SqlXmlParameter 物件&#40;SQLXML Managed 類別&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/net-framework-classes/sqlxml-managed-classes-sqlxmlparameter-object.md)  
  
  
