---
title: 設定 PolyBase 存取 Oracle 中的外部資料 | Microsoft Docs
description: 本文示範如何使用 PolyBase 建立外部資料來源來存取 Oracle 資料。
ms.date: 04/23/2019
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: Abiola
ms.author: aboke
ms.reviewer: mikeray
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: 09899bf161289e87e7bb15b9084335bbb4bc6180
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68062303"
---
# <a name="configure-polybase-to-access-external-data-in-oracle"></a>設定 PolyBase 存取 Oracle 中的外部資料

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

本文說明如何在 SQL Server 執行個體上使用 PolyBase 查詢位於 Oracle 中的外部資料。

## <a name="prerequisites"></a>Prerequisites

如果您尚未安裝 PolyBase，請參閱 [PolyBase 安裝](polybase-installation.md)。

  在建立資料庫範圍認證之前，必須建立[主要金鑰](../../t-sql/statements/create-master-key-transact-sql.md)。 

## <a name="configure-an-oracle-external-data-source"></a>設定 Oracle 外部資料來源

若要查詢來自 Oracle 資料來源的資料，您必須建立外部資料表參考外部資料。 本節提供建立這些外部資料表的範例程式碼。

本節中使用下列 Transact-SQL 命令：

- [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)
- [CREATE EXTERNAL DATA SOURCE (Transact-SQL)](../../t-sql/statements/create-external-data-source-transact-sql.md) 
- [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)


1. 建立資料庫範圍認證以存取 Oracle 來源。

    ```sql
    /*  specify credentials to external data source
    *  IDENTITY: user name for external source. 
    *  SECRET: password for external source.
    */
    CREATE DATABASE SCOPED CREDENTIAL credential_name WITH IDENTITY = 'username', Secret = 'password';
    ```

1. 使用 [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) 建立外部資料來源。

    ```sql
    /* 
    * LOCATION: Location string should be of format '<vendor>://<server>[:<port>]'.
    * PUSHDOWN: specify whether computation should be pushed down to the source. ON by default.
    * CONNECTION_OPTIONS: Specify driver location
    * CREDENTIAL: the database scoped credential, created above.
    */  
    CREATE EXTERNAL DATA SOURCE external_data_source_name
    WITH ( LOCATION = 'oracle://<server address>[:<port>]',
    -- PUSHDOWN = ON | OFF,
    CREDENTIAL = credential_name)
    ```

1. **選擇性：** 在外部資料表上建立統計資料。

    我們建議在外部資料表資料行上建立統計資料 (尤其是用於聯結、篩選和彙總的資料行)，以取得最佳查詢效能。

    ```sql
    CREATE STATISTICS statistics_name ON customer (C_CUSTKEY) WITH FULLSCAN; 
    ```

>[!IMPORTANT] 
>當您建立外部資料來源之後，可以使用 [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) 命令透過該來源建立可查詢的資料表。 

如需詳細資訊和範例，請參閱下列文章：

- [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md)。
- [SQL Server PolyBase 概觀](polybase-guide.md)。
