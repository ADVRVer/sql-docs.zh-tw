---
title: 取得驅動程式版本
description: 了解如何尋找以及在何處尋找 Microsoft JDBC Driver for SQL Server 的版本。
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5e241d72-16da-4ada-ac67-e6308394108f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f90f521457f5df17be814a179353d138a3245aea
ms.sourcegitcommit: b2ab989264dd9d23c184f43fff2ec8966793a727
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86381192"
---
# <a name="getting-the-driver-version"></a>取得驅動程式版本
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  您可以下列方式尋找已安裝的 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 版本：  
  
-   呼叫 [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) 方法 [getDriverMajorVersion](../../connect/jdbc/reference/getdrivermajorversion-method-sqlserverdatabasemetadata.md)、[getDriverMinorVersion](../../connect/jdbc/reference/getdriverminorversion-method-sqlserverdatabasemetadata.md) 或 [getDriverVersion](../../connect/jdbc/reference/getdriverversion-method-sqlserverdatabasemetadata.md)。  
  
-   版本會顯示在產品分銷的 readme.txt 檔中。  
  
 此外，JDBC 驅動程式名稱可從 SQLServerDatabaseMetaData 類別上的 [getDriverName](../../connect/jdbc/reference/getdrivername-method-sqlserverdatabasemetadata.md) 方法呼叫傳回。 例如，它會傳回 "Microsoft JDBC Driver 6.4 for SQL Server"。  
  
 下列是呼叫 SQLServerDatabaseMetaData 類別之方法的輸出範例：  
  
 `getDriverName = Microsoft JDBC Driver 6.4 for SQL Server`  
  
 `getDriverMajorVersion = 6`  
  
 `getDriverMinorVersion = 4`  
  
 `getDriverVersion = 6.4.` *xxx.x*  
  
 其中 "xxx.x" 為最終的版本號碼。  
  
## <a name="see-also"></a>另請參閱  
 [診斷 JDBC 驅動程式的問題](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
