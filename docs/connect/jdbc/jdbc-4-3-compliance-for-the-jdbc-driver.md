---
title: JDBC 4.3 JDBC 驅動程式的相容性 |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33b218598871e570fa99d212d565c834718de1d9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>JDBC 4.3 JDBC 驅動程式的相容性
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  適用於 SQL Server 的 Microsoft JDBC 驅動程式 6.4 之前的版本是 Java 資料庫連線 API 4.2 規格相容。 本節不適用於 6.4 版之前的版本。  
  
 目前，SQL Server 的 Microsoft JDBC 驅動程式 6.4 是 Java 9 相容，但不完全符合標準的 Java 資料庫連線 API 4.3 規格。 新導入 JDBC 4.3 中的 Api，否則驅動程式支援驅動程式將會擲回 SQLFeatureNotSupportedException。