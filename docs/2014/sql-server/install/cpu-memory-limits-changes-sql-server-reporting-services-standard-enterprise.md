---
title: SQL Server Reporting Services Standard 和 Enterprise 的變更 CPU 和記憶體限制 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: dd553715-2b95-4119-8f58-d01de388d9ab
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: efc71378e6570a86d075ed50e206284a93b0532a
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/13/2018
ms.locfileid: "53353865"
---
# <a name="changes-to-cpu-and-memory-limits-for-sql-server-reporting-services-standard-and-enterprise"></a>SQL Server Reporting Services Standard 和 Enterprise 之 CPU 和記憶體限制的變更
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services Standard 和 Enterprise 最多可支援 64 GB 的系統記憶體。  
  
## <a name="component"></a>元件  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
### <a name="description"></a>描述  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Reporting Services Standard 和 Enterprise 最多可支援 64 GB 的系統記憶體。 您可能需要重新設定目前的系統設定，才能符合新的限制。  
  
 如需針對其他版本的 CPU 和記憶體限制[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，請參閱[SQL server 版本計算容量限制](../compute-capacity-limits-by-edition-of-sql-server.md)，和[支援的 SQL Server 版本的記憶體](https://go.microsoft.com/fwlink/?LinkId=212633)。  
  
## <a name="corrective-action"></a>更正動作  
 您可能需要重新設定目前的系統設定，才能符合新的 CPU 和記憶體限制。 如需詳細資訊，請參閱 < [ALTER SERVER CONFIGURATION &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)，以及[伺服器記憶體伺服器組態選項](../../database-engine/configure-windows/server-memory-server-configuration-options.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 2014 各版本所支援的功能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [回溯相容性](../../../2014/getting-started/backward-compatibility.md)  
  
  
