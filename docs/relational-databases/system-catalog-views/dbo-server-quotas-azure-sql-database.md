---
title: "dbo.server_quotas (Azure SQL Database) |Microsoft 文件"
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 08/02/2016
ms.prod: 
ms.reviewer: 
ms.service: sql-database
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.server_quotas
- dbo.server_quotas_TSQL
- server_quotas
- server_quotas_TSQL
dev_langs: TSQL
helpviewer_keywords: server_quotas
ms.assetid: 34423903-1aaa-4a55-88a6-8228315d84e7
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 612f4d0a819c1271ca9b5e8b9fda8f224ae6fbe6
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="dboserverquotas-azure-sql-database"></a>dbo.server_quotas (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> **重要！！** 這適用於 **[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11 只 ！**  
>   
>  這項功能處於預覽狀態。 不要採用此功能的特定實作的相依性，因為在未來的版本中可能會變更或移除此功能。  
  
 傳回伺服器上可用的資料庫配額類型。  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|quota_name|**nvarchar**|伺服器的配額類型。 型別**Premium_database**相當於含有資源保留的資料庫。|  
|quota_value|**int**|伺服器中允許的配額類型數目。|  
  
## <a name="permissions"></a>Permissions  
 這個檢視可用於所有的使用者角色有權連接到虛擬**主要**資料庫。  
  
## <a name="see-also"></a>請參閱＜  
 [管理高階資料庫](http://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
