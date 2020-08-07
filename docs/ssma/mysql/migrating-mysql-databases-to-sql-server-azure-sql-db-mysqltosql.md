---
title: 將 MySQL 資料庫遷移至 SQL Server Azure SQL Database |Microsoft Docs
description: 使用此建議的程式，將 MySQL 資料庫遷移至使用 SQL Server 移轉小幫手 (SSMA) 的 SQL Server 或 Azure SQL Database。
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8006f9a0-394d-4238-8dc5-44255134628b
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c6f360e67621288e6c04381931a7c0df0de3e256
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "87862354"
---
# <a name="migrating-mysql-databases-to-sql-server---azure-sql-database-mysqltosql"></a>將 MySQL 資料庫遷移至 SQL Server Azure SQL Database (MySQLToSql) 
適用于 MySQL 的 SQL Server 移轉小幫手 (SSMA) 是一個完整的環境，可協助您快速將 MySQL 資料庫遷移至 SQL Server 或 SQL Azure。 藉由使用 SSMA for MySQL，您可以查看資料庫物件和資料、評估要遷移的資料庫、將資料庫物件遷移至 SQL Server 或 SQL Azure，然後將資料移轉至 SQL Server 或 SQL Azure。  
  
## <a name="recommended-migration-process"></a>建議的遷移程式  
若要成功地將物件和資料從 MySQL 資料庫遷移至 SQL Server 或 SQL Azure，請使用下列程式：  
  
1.  使用[SSMA Projects &#40;MySQLToSQL&#41;](../../ssma/mysql/working-with-ssma-projects-mysqltosql.md)。  
  
    建立專案之後，您可以設定專案轉換、遷移和類型對應選項。 如需專案設定的詳細資訊，請參閱[&#40;MySQLToSQL&#41;設定專案選項](../../ssma/mysql/setting-project-options-mysqltosql.md)。 如需如何自訂資料類型對應的詳細資訊，請參閱將[MySQL 和 SQL Server 資料類型對應 &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
2.  [連接到 MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
3.  [連接到 SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
4.  [將 MySQL 資料庫對應至 SQL Server 架構 &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
5.  [連接到 Azure SQL Database &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
6.  （選擇性）[評估要轉換的 MySQL 資料庫 &#40;MySQLToSQL&#41;](../../ssma/mysql/assessing-mysql-databases-for-conversion-mysqltosql.md)評估要轉換的資料庫物件，並估計轉換時間。  
  
7.  [將 MySQL 資料庫轉換 &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
8.  [同步處理](loading-converted-database-objects-into-sql-server-mysqltosql.md)  
  
9. 您可以透過下列其中一種方式來執行這項操作：  
  
    -   儲存腳本，並在 SQL Server 或 SQL Azure 上執行。  
  
    -   同步處理資料庫物件。  
  
10. [將 MySQL 資料移轉至 SQL Server Azure SQL Database &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
11. 如有必要，請更新資料庫應用程式。  
  
> [!NOTE]  
> 您無法遷移 Information_schema 和 MySQL 架構。  
  
## <a name="see-also"></a>另請參閱  
[安裝 SSMA for MySQL &#40;MySqlToSql&#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
[適用于 MySQL 的 SSMA &#40;MySQLToSQL&#41;的消費者入門](../../ssma/mysql/getting-started-with-ssma-for-mysql-mysqltosql.md)  
  
