---
title: allow updates 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: configure-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
caps.latest.revision: 32
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d8dca8b3d27f5035fa3576677f595d3bde0a981d
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/18/2018
---
# <a name="allow-updates-server-configuration-option"></a>允許更新伺服器組態選項
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  此選項仍會出現在 **sp_configure** 預存程序中，但其功能已無法在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中使用。 此設定無效。 不支援對系統資料表的直接更新。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 變更 **allow updates** 選項將會導致 RECONFIGURE 陳述式失敗。 應該從所有指令碼移除對於 **allow updates** 選項的變更。  
  
## <a name="see-also"></a>另請參閱  
 [伺服器組態選項 &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
