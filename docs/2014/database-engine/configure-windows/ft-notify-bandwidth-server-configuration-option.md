---
title: 全文檢索通知頻寬伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- ft notify bandwidth opion
- small memory buffers
- memory [SQL Server], buffers
ms.assetid: 9ca284c5-f3e0-4a67-a132-fff376ff0ffe
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ea5b6663c2d2b599fa4f0ec3abd1b003fcc1c17c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36131560"
---
# <a name="ft-notify-bandwidth-server-configuration-option"></a>全文檢索通知頻寬伺服器組態選項
  使用 [全文檢索通知頻寬] 選項，指定小型記憶體緩衝集區可以成長到何種大小。 小型記憶體緩衝區的大小是 64 KB。 *max* 參數值會指定全文檢索記憶體管理員應該在小型緩衝集區中維持的最大緩衝區數目。 如果`max`值為零，則可以位於小型緩衝集區的緩衝區數目沒有上限。  
  
 **min** 參數指定必須在小型記憶體緩衝集區中維持的最小記憶體緩衝區數目。 在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記憶體管理員的要求下，所有額外緩衝集區都會釋放，但是仍會維護最小數目的緩衝區。 但是，如果指定的 **min** 值是零，則會釋放所有記憶體緩衝區。  
  
 在某些情況下，目前配置的緩衝區數目小於 **min** 參數所指定的值。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [全文檢索編目頻寬伺服器組態選項](ft-crawl-bandwidth-server-configuration-option.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
