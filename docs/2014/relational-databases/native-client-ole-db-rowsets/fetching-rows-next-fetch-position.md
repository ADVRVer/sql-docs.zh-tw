---
title: 下一個擷取位置 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 05d2c63c2d973416883562512ac45dd391f6c4b6
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/01/2020
ms.locfileid: "82694513"
---
# <a name="next-fetch-position"></a>下一個提取位置
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會追蹤下一個提取位置，讓**GetNextRows**方法的一系列呼叫（不略過、方向變更或對**FindNextRow**、 **Seek**或**RestartPosition**方法的中間呼叫）會讀取整個資料列集，而不會略過或重複任何資料列。 下一個提取位置的變更方式為：呼叫 **IRowset::GetNextRows**、**IRowset::RestartPosition** 或 **IRowsetIndex::Seek**，或者呼叫包含 Null *pBookmark* 值的 **FindNextRow**。 呼叫包含非 Null *pBookmark* 值的 **FindNextRow** 不會影響下一個提取位置。  
  
## <a name="see-also"></a>另請參閱  
 [擷取資料列](fetching-rows.md)  
  
  
