---
title: sp_syscollector_update_collector_type （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_update_collector_type_TSQL
- sp_syscollector_update_collector_type
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_update_collector_type
- data collector [SQL Server], stored procedures
ms.assetid: 3c414dfd-d9ca-4320-81aa-949465b967bf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f315b95b100315691d1ace30a3fe3bb2e9788d27
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892797"
---
# <a name="sp_syscollector_update_collector_type-transact-sql"></a>sp_syscollector_update_collector_type (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  更新收集項的收集器型別。 指定收集器型別的名稱和 GUID 之後，就會更新收集器型別組態，包括收集和上傳封裝、參數結構描述，以及參數格式器結構描述。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_syscollector_update_collector_type [ @collector_type_uid = ] 'collector_type_uid' OUTPUT  
          , [ @name = ] 'name'  
          , [ @parameter_schema = ] 'parameter_schema'  
          , [ @collection_package_id = ] collection_package_id  
          , [ @upload_package_id = ] upload_package_id  
```  
  
## <a name="arguments"></a>引數  
`[ @collector_type_uid = ] 'collector_type_uid'`這是收集器型別的 GUID。 *collector_type_uid*是**uniqueidentifier**，而且如果是 Null，則會自動建立並當做輸出傳回。  
  
`[ @name = ] 'name'`這是收集器型別的名稱。 *名稱*是**sysname** ，必須指定。  
  
`[ @parameter_schema = ] 'parameter_schema'`這是此收集器型別的 XML 架構。 *parameter_schema*是**xml** ，某些收集器型別可能需要它。 如果它不是必要項目，這個引數就可能是 NULL。  
  
`[ @collection_package_id = ] collection_package_id`這是指向 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 收集組所使用之集合封裝的本機唯一識別碼。 *collection_package_id*是**uniqueidentifier** ，而且是必要的。 若要取得*collection_package_id*的值，請在 msdb 資料庫中查詢 dbo.syscollector_collector_types 系統檢視。  
  
`[ @upload_package_id = ] upload_package_id`這是指向 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 收集組所使用之上傳封裝的本機唯一識別碼。 *upload_package_id*是**uniqueidentifier** ，而且是必要的。 若要取得*upload_package_id*的值，請在 msdb 資料庫中查詢 dbo.syscollector_collector_types 系統檢視。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功）或**1** （失敗）  
  
## <a name="permissions"></a>權限  
 需要**dc_admin** （具有 EXECUTE 許可權）固定資料庫角色中的成員資格。  
  
## <a name="example"></a>範例  
 此範例會更新一般 T-SQL 查詢收集器型別  (在此範例中，將會使用一般 T-SQL 查詢收集器型別的預設結構描述)。  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_update_collector_type  
@collector_type_uid = '302E93D1-3424-4BE7-AA8E-84813ECF2419',  
@name = 'Generic T-SQL Query Collector Type',  
@parameter_schema = '<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="DataCollectorType">  
  <xs:element name="TSQLQueryCollector">  
<xs:complexType>  
  <xs:sequence>  
<xs:element name="Query" minOccurs="1" maxOccurs="unbounded">  
  <xs:complexType>  
<xs:sequence>  
  <xs:element name="Value" type="xs:string" />  
  <xs:element name="OutputTable" type="xs:string" />  
</xs:sequence>  
  </xs:complexType>  
</xs:element>  
<xs:element name="Databases" minOccurs="0" maxOccurs="1">  
  <xs:complexType>  
<xs:sequence>  
  <xs:element name="Database" minOccurs="0" maxOccurs="unbounded" type="xs:string" />  
</xs:sequence>  
<xs:attribute name="UseSystemDatabases" type="xs:boolean" use="optional" />  
<xs:attribute name="UseUserDatabases" type="xs:boolean" use="optional" />  
  </xs:complexType>  
</xs:element>  
  </xs:sequence>  
</xs:complexType>  
  </xs:element>  
</xs:schema>',  
@collection_package_id = '292B1476-0F46-4490-A9B7-6DB724DE3C0B',  
@upload_package_id = '6EB73801-39CF-489C-B682-497350C939F0';  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [&#40;Transact-sql&#41;的系統預存程式](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [資料收集](../../relational-databases/data-collection/data-collection.md)  
  
  
