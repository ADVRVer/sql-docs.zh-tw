---
title: SQL Server 的 Latches 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
caps.latest.revision: 21
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e56ec72b03ca7b4ea4a93ce91a5fe1ac89e50bb2
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43820944"
---
# <a name="sql-server-latches-object"></a>SQL Server 的 Latches 物件
  Microsoft **的** SQLServer:Latches [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件提供計數器，可監視稱為閂鎖的內部 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源鎖定。 監視閂鎖來判斷使用者活動和資源使用狀況，可協助您找出效能的瓶頸。  
  
 下表描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Latches** 計數器。  
  
|SQL Server 的 Latches 計數器|描述|  
|---------------------------------|-----------------|  
|**Average Latch Wait Time (ms)**|必須等候之閂鎖要求的平均閂鎖等候時間 (以毫秒為單位)。|  
|**Latch Waits/sec**|無法立即授權的閂鎖要求次數。|  
|**SuperLatch 數目**|目前為 SuperLatch 的閂鎖數目。|  
|**SuperLatch Demotions/sec**|在上一秒內已降級為一般閂鎖的 SuperLatch 數目。|  
|**SuperLatch Promotions/sec**|在上一秒內已升級為 SuperLatch 的閂鎖數目。|  
|**Total Latch Wait Time (ms)**|最後一秒內的鎖定總等候時間 (以毫秒為單位)。|  
  
## <a name="see-also"></a>另請參閱  
 [監視資源使用狀況 &#40;系統監視器&#41;](monitor-resource-usage-system-monitor.md)  
  
  
