---
title: 配置環境控制碼 |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, environment handles
- ODBC applications, connections
- handles [SQL Server Native Client]
- environment handles [SQLNCLI]
ms.assetid: 15c1b428-ea6d-4672-894c-f0e289e2da3f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2ec79644005e599fc17bada65c49d6f1516539fb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85734921"
---
# <a name="allocating-an-environment-handle"></a>配置環境控制代碼
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  應用程式必須先初始化 ODBC 環境並配置環境控制代碼，然後才能呼叫任何 ODBC 函數。 在 ODBC 中，這是其他控制代碼的全域內容控制代碼和預留位置。 若要這麼做，您可以呼叫**SQLAllocHandle**並將*HandleType*參數設定為 SQL_HANDLE_ENV，並將*InputHandle*設定為 SQL_Null_HANDLE。  
  
 配置環境控制代碼之後，應用程式必須設定環境屬性來指出它將使用的 ODBC 函數呼叫版本。 使用 ODBC 3。*x*函式，請呼叫[SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)並將*Attribute*參數設定為 SQL_ATTR_ODBC_VERSION，並將*valueptr 是*設為 SQL_OV_ODBC3。  
  
## <a name="see-also"></a>另請參閱  
 [與 SQL Server &#40;ODBC&#41;通訊](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
