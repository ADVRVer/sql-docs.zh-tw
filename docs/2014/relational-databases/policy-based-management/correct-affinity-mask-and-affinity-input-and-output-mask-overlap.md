---
title: 正確的 Affinity Mask 和 Affinity 輸入的輸出遮罩重疊 |Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1a0da6df-57ff-4f3f-aae9-2fbc4897508c
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9a5cc744eb941d309ff938452fef01a24716a946
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36133935"
---
# <a name="correct-affinity-mask-and-affinity-input-output-mask-overlap"></a>正確的 Affinity Mask 和 Affinity 輸入的輸出 Mask 重疊
  這個規則會檢查 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體是否有一或多個指派給搭配 affinity mask 和 affinity I/O mask 選項使用的處理器。 在具有一個以上處理器的電腦中，affinity mask 和 affinity I/O mask 選項是用來指派 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所使用的 CPU。 使用 affinity mask 和 affinity I/O mask 來啟用 CPU 可能會強制處理器過度使用而使效能變慢。  
  
## <a name="best-practices-recommendations"></a>最佳做法建議  
 當您指定 affinity mask 或 affinity I/O mask 選項時，您應該指定這兩者，但是每一個 CPU 不能啟用超過一次。  
  
 請勿同時在 affinity mask 選項和 affinity I/O mask 選項內啟用相同的 CPU。 對應到每個 CPU 的位元應屬於下列三種情況之一：  
  
-   affinity mask 選項和 affinity I/O mask 選項內的 0  
  
-   affinity mask 選項內的 0 和 affinity I/O mask 選項內的 1  
  
-   affinity mask 選項內的 1 和 affinity I/O mask 選項內的 0  
  
## <a name="for-more-information"></a>詳細資訊  
 [affinity mask 伺服器組態選項](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)  
  
 [affinity Input-Output mask 伺服器組態選項](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md)  
  
 [affinity64 mask 伺服器組態選項](../../database-engine/configure-windows/affinity64-mask-server-configuration-option.md)  
  
 [affinity64 輸入輸出伺服器組態選項](../../database-engine/configure-windows/affinity64-input-output-mask-server-configuration-option.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用原則式管理來監視和強制最佳做法](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  