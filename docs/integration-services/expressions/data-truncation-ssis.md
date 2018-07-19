---
title: 資料截斷 (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6fd9e7c0c04df6f9cb6ec326d02e876c8847d2d6
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2018
ms.locfileid: "35334352"
---
# <a name="data-truncation-ssis"></a>資料截斷 (SSIS)
  將某個資料類型的值轉換成其他類型，可能會導致值被截斷。  
  
 發生截斷的狀況︰  
  
-   如果原始字串包含雙位元組字元，將字串資料從 *DT_WSTR* 轉換成相同長度的 *DT_STR* 時。  
  
-   當整數從 *DT_I4* 轉型成 *DT_I2* 時，可能會遺失大量位數。  
  
-   不帶正負號的整數轉換成帶正負號的整數時，可能會遺失大量位數。  
  
-   當實數從 *DT_R8* 轉型成 *DT_R4* 時，可能會遺失少量位數。  
  
-   當整數從 *DT_I4* 轉型成 *DT_R4* 時，可能會遺失少量位數。  
  
 運算式評估工具會識別可能導致截斷的明確轉換，並在剖析運算式時發出警告。 例如，如果將 30 個字元的字串轉換成 20 個字元的字串，則運算式評估工具會向您發出警告。  
  
 不過，執行階段不檢查截斷。 資料在執行階段截斷時，不會發出警告。 多數資料配接器和轉換支援錯誤輸出，可處理錯誤資料列的配置。  
  
 如需處理資料截斷的詳細資訊，請參閱 [Error Handling in Data](../../integration-services/data-flow/error-handling-in-data.md)(處理資料時發生錯誤)。  
  
  
