---
title: SQL Server 2016 資料庫引擎功能的重大變更 | Microsoft Docs
ms.custom: ''
ms.date: 11/27/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], what's new
- breaking changes [SQL Server]
ms.assetid: 47edefbd-a09b-4087-937a-453cd5c6e061
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 83725ee74e17a91465356b426b13afc0c265f851
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2018
ms.locfileid: "52536376"
---
# <a name="breaking-changes-to-database-engine-features-in-sql-server-2016"></a>SQL Server 2016 中對於 Database Engine 的重大變更
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  本主題描述 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] 以及舊版 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的最新變更。 這些變更可能會中斷以舊版 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]為根據的應用程式、指令碼或功能。 當您升級時可能會遇到這些問題。  
  
##  <a name="SQL15"></a> [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] 的重大變更  
  
-   sys.dm_io_virtual_file_stats 的 sample_ms 資料行已經從 **int** 擴充到 **bigint** 資料類型。  
  
-   sys.fn_virtualfilestats 的 TimeStamp 資料行已經從 **int** 擴充到 **bigint** 資料類型。  

-   使用 MD2、MD4、MD5、SHA 或 SHA1 雜湊演算法 (不建議使用) 必須將資料庫相容性層級設定為早於 130。  

-   在資料庫相容性層級 130 下，藉由考量小數部分的毫秒從 **datetime** 隱含轉換至 **datetime2** 資料類型顯示改善的精確度，會導致不同的轉換值。 只要 datetime 和 datetime2 資料類型之間存在混合的比較案例，就明確轉換為 datetime2 資料類型。 如需詳細資訊，請參閱此篇 [Microsoft 支援服務文章](https://support.microsoft.com/help/4010261)。

## <a name="previous-versions"></a>舊版  

如需 SQL Server 2014 版和某些舊版中的重大變更資訊，請參閱 [SQL Server 2014 中對於 Database Engine 的重大變更](https://docs.microsoft.com/sql/database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016?view=sql-server-2014#SQL14)。

#### <a name="archived-documentation-for-very-old-versions-of-sql-server"></a>非常舊版的 SQL Server 封存文件

[!INCLUDE[Archived documentation for very old versions of SQL Server](../includes/paragraph-content/previous-versions-archive-documentation-sql-server.md)]

## <a name="see-also"></a>另請參閱  
 [SQL Server 2016 中已被取代的 Database Engine 功能](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [SQL Server 2016 中已停止的 Database Engine 功能](../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [SQL Server Database Engine 回溯相容性](../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [ALTER DATABASE 相容性層級 &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
 [Windows 上處理某些資料類型和不常見作業的 SQL Server 2016 或 SQL Server 2017 改善](https://support.microsoft.com/help/4010261)
  
  
