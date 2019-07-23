---
title: 伺服器觸發程序遞迴伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- recursive triggers [SQL Server]
- triggers [SQL Server], recursive
- server trigger recursion option
ms.assetid: da4c25f5-d04c-4951-a3db-409e71a1b468
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dcd67a89ea5605647d6736d9d28a6e070a483c16
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68027619"
---
# <a name="server-trigger-recursion-server-configuration-option"></a>伺服器觸發程序遞迴伺服器組態選項
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  使用 [伺服器觸發程序遞迴]  選項，可指定是否允許伺服器層級的觸發程序以遞迴方式引發。 如果此選項設成 1 (ON)，則允許伺服器層級的觸發程序以遞迴方式引發。 若設成 0 (OFF)，則伺服器層級的觸發程序無法以遞迴方式引發。 當 server trigger recursion 選項設為 0 (OFF)，只能阻止直接遞迴。 (若要停用間接遞迴，請將 [巢狀觸發程序]  選項設定為 0)。這個選項的預設值是 1 (ON)。 伺服器不需重新啟動，設定即可立刻生效。  
  
 如需相關資訊，請參閱 [建立巢狀觸發程序](../../relational-databases/triggers/create-nested-triggers.md)。  
  
## <a name="see-also"></a>另請參閱  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [伺服器組態選項 &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
