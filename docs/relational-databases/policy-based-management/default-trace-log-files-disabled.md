---
title: "預設追蹤記錄檔已停用 | Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e3e13cae337c3006c3e4f4990e292eaeebf7d675
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/18/2018
---
# <a name="default-trace-log-files-disabled"></a>預設追蹤記錄檔已停用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] 此規則會檢查 sp_configure 預存程序 default trace enabled 選項的值，以判斷預設追蹤是否設定為 ON (1) 或 OFF (0)。 當啟用這個選項時，預設追蹤會提供有關組態及 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]之 DDL 變更的資訊。 在某些情況下，當客戶和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務及支援中心在排除 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的問題時，這項資訊對於他們很有幫助。  
  
## <a name="best-practices-recommendations"></a>最佳做法建議  
 使用 sp_configure 預存程序，將 default trace enabled 設定為 1 的值來啟用追蹤。  
  
## <a name="for-more-information"></a>詳細資訊  
 [伺服器組態選項 &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用原則式管理來監視和強制最佳做法](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
