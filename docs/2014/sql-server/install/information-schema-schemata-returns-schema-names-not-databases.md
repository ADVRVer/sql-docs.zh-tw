---
title: INFORMATION_SCHEMA。架構會傳回資料庫中的架構名稱，而不是實例中的資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0e3683ee043785ec6adc349ac52301280c7bc2b8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2020
ms.locfileid: "66094733"
---
# <a name="information_schemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a>INFORMATION_SCHEMA.SCHEMATA 會傳回資料庫 (非執行個體中的資料庫) 中的結構描述名稱
  Upgrade Advisor 偵測到參考 INFORMATION_SCHEMA.SCHEMATA 檢視的陳述式。 在舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，此檢視會傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中的所有資料庫。 在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本中，此檢視會傳回資料庫中的所有結構描述。  
  
## <a name="component"></a>元件  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>描述  
 在舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，INFORMATION_SCHEMA.SCHEMATA 檢視會傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中的所有資料庫。 現在，該檢視會傳回符合「SQL 標準」之資料庫中的所有結構描述。  
  
## <a name="corrective-action"></a>更正動作  
 將您的應用程式修改為參考**sys.databases**目錄檢視，以傳回實例中的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所有資料庫。  
  
## <a name="see-also"></a>另請參閱  
 [資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新的&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
