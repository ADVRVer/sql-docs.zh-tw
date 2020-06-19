---
title: 設定快速剖析 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: dcd1dc09-6eaf-440b-9ce6-fef779ff794f
author: janinezhang
ms.author: janinez
ms.openlocfilehash: bb0fefd2f9c06d6bcff44c211904a951ebe01937
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84963348"
---
# <a name="set-fast-parse"></a>設定快速剖析
  使用快速剖析的來源或轉換，其每一個資料行都必須設定快速剖析屬性。 若要設定屬性，請使用「一般檔案」來源或「資料轉換」的進階編輯器。  
  
### <a name="to-set-fast-parse"></a>設定快速剖析  
  
1.  以滑鼠右鍵按一下 [一般檔案] 來源或 [資料轉換]，然後按一下 [顯示進階編輯器]****。  
  
2.  按一下 **[進階編輯器]** 對話方塊中的 **[輸入與輸出屬性]** 索引標籤。  
  
3.  在 **[輸入及輸出]** 窗格中，按一下您要啟用快速剖析的資料行。  
  
4.  在 [屬性視窗中，展開 [**自訂屬性**] 節點，然後將 `FastParse` 屬性設定為 `True` 。  
  
5.  按一下 [確定]。  
  
  
