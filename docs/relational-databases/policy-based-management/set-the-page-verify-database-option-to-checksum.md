---
title: 將 PAGE_VERIFY 資料庫選項設定為 CHECKSUM | Microsoft 文件
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: b9c9e3f77ef7d94fa1847bb1df9f846423ec56fc
ms.sourcegitcommit: ef6e3ec273b0521e7c79d5c2a4cb4dcba1744e67
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51512383"
---
# <a name="set-the-pageverify-database-option-to-checksum"></a>將 PAGE_VERIFY 資料庫選項設定為 CHECKSUM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  這個規則會檢查 PAGE_VERIFY 資料庫選項是否設定為 CHECKSUM。 當針對 PAGE_VERIFY 資料庫選項啟用 CHECKSUM 時， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 會針對整頁的內容計算總和檢查碼，並在將頁面寫入磁碟時，於頁首中儲存值。 從磁碟讀取頁面時，會重新計算總和檢查碼，並與頁首所儲存的總和檢查碼值作比較。 如此有助於提供高層級的資料檔完整性。  
  
## <a name="best-practices-recommendations"></a>最佳做法建議  
 將 PAGE_VERIFY 資料庫選項設定為 CHECKSUM。  
  
## <a name="for-more-information"></a>詳細資訊  
 [ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  
