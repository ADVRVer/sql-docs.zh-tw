---
title: 設定資料收集參數 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 25acc3d0b5f9c29476e0041e38fc62f04d646b27
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="configure-data-collection-parameters-transact-sql"></a>設定資料收集參數 (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  在您建立自訂收集組之前，必須先設定資料收集參數。 您可以使用資料收集器所提供的預存程序來完成此作業。 完成這項工作需要在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中使用查詢編輯器來進行以下程序。  
  
> [!NOTE]  
>  只設定資料收集參數一次。 在組態設定之後，這些參數會用於您所建立的其他任何收集組。  
  
### <a name="configure-data-collection-parameters"></a>設定資料收集參數  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接到您想要建立自訂收集組的資料庫。  
  
2.  在查詢編輯器中，發出下列陳述式。  
  
    ```sql  
    USE msdb;  
    EXEC sp_syscollector_set_warehouse_instance_name N'INSTANCE_NAME';-- where instance name is the name of the SQL Server instance  
    EXEC sp_syscollector_set_warehouse_database_name N'MDW';  
    EXEC sp_syscollector_set_cache_directory N'D:\tempdata';  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [資料收集](../../relational-databases/data-collection/data-collection.md)   
 [資料收集器預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
