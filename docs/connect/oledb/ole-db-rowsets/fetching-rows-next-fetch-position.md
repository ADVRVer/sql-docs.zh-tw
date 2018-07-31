---
title: 下一個提取位置 |Microsoft Docs
description: 擷取資料列 - 下一個擷取位置
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: ec1149b615c64f2113afc007c0ea04e4c4665698
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2018
ms.locfileid: "39106104"
---
# <a name="fetching-rows---next-fetch-position"></a>擷取資料列 - 下一個擷取位置
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server 會追蹤下一個提取位置，讓 **GetNextRows** 方法的呼叫序列 (沒有略過、變更方向，或者介入 **FindNextRow**、**Seek** 或 **RestartPosition** 方法的呼叫) 讀取完整的資料列集，而不用略過或重複任何資料列。 下一個提取位置的變更方式為：呼叫 **IRowset::GetNextRows**、**IRowset::RestartPosition** 或 **IRowsetIndex::Seek**，或者呼叫包含 Null *pBookmark* 值的 **FindNextRow**。 呼叫包含非 Null *pBookmark* 值的 **FindNextRow** 不會影響下一個提取位置。  
  
## <a name="see-also"></a>另請參閱  
 [擷取資料列](../../oledb/ole-db-rowsets/fetching-rows.md)  
  
  
