---
title: "SQLXML 不會安裝在 SQL Server |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 82106a146c4c491ebc48da493ab325c7553b7edd
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2018
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>SQLXML 不會安裝在 SQL Server 中
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 之前，SQLXML 4.0 隨附於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 而且是所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本 ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 除外) 之預設安裝的一部分。 不過，從 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 開始，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已不再包含最新版 SQLXML (SQLXML 4.0 SP1)。 若要安裝 SQLXML 4.0 SP1，下載從[SQLXML 4.0 SP1 的安裝位置](https://www.microsoft.com/en-us/download/details.aspx?id=30403)。  
  
 如果應用程式執行於[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，而且需要 SQLXML 4.0 中，您必須下載並安裝 SQLXML 4.0 SP1。  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>使用 SQLOLEDB 和 SQL Server Native Client OLE DB Provider 的 SQLXML 4.0 SP1 行為以及新的資料類型  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 導入使用 SQLXML 開發人員可能想要使用下列資料類型：  
  
-   **日期**  
  
-   **Time**  
  
-   **DateTime2**  
  
-   **DateTimeOffset**  
  
 當使用 SQLXML 4.0 SP1 搭配 SQLOLEDB 或[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 從[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]，這些類型會顯示為字串的開發人員。 SQLXML 4.0 SP1 會將這四個新的資料類型啟用成內建的純量類型搭配使用時[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者 11.0 或更新版本。 在您下載 SQLXML 4.0 SP1 之前，將這些類型對應至非字串類型可能會導致某些資料遭截斷。 例如，對應**DateTime2**至**xsd: date**會導致資料截斷成[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] **DateTime**精確度為 3.33 毫秒。  
  
## <a name="see-also"></a>另請參閱  
 [SQLXML 4.0 程式設計概念](../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md)  
  
  
