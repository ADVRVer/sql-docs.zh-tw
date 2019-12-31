---
title: sys.databases dm_cluster_endpoints （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, big-data-clusters
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_cluster_endpoints
- dm_cluster_endpoints_TSQL
- dm_cluster_endpoints
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cluster_endpoints dynamic management view
ms.assetid: ''
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: b6ec5de74d2da2a94c25ef121abc0157348554d5
ms.sourcegitcommit: ef830f565ee07dc7d4388925cc3c86c5d2cfb4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2019
ms.locfileid: "74947061"
---
# <a name="sysdm_cluster_endpoints-transact-sql"></a>sys.databases dm_cluster_endpoints （Transact-sql）
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|name|`sysname`|在 SQL big data 叢集中外部公開的服務名稱。 端點的唯一識別碼。 此視圖的索引鍵。 不可為 Null。 |  
|description|`nvarchar(4000)`|服務的描述。 不可為 Null。 |
|endpoint|`sysname`|端點 url 或連接屬性。 不可為 Null。 |
|protocol_desc|`sysname`|端點通訊協定的描述 |

## <a name="permissions"></a>權限

在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]上， `VIEW SERVER STATE`需要許可權。

## <a name="see-also"></a>另請參閱

[什麼是[!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ss-nover.md)] ](../../big-data-cluster/big-data-cluster-overview.md)？
