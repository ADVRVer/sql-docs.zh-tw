---
title: 定義篩選 | Microsoft 文件
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.replconflictviewer.definefilters.f1
helpviewer_keywords:
- Define Filters dialog box
ms.assetid: 1fa71d22-ce5a-4aae-ba05-4d755842aeac
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1837e3b57548ec0d4324a408f8f43201ccc3ca6b
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768175"
---
# <a name="define-filters"></a>定義篩選
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[定義篩選]** 對話方塊可讓您定義篩選，然後套用至資料衝突，以在方格中檢視衝突的子集。 若要定義篩選，請從 **[運算子]** 下拉式清單方塊選擇運算子，然後輸入一個值。 例如，若只要顯示衝突失敗者為 **ReplTest1**伺服器的衝突，請從 **[運算子]** 下拉式清單方塊選取 **[等於]** ，然後在 **[值]** 資料行輸入 **ReplTest1** 。  
  
## <a name="options"></a>選項。  
 **[運算子]**  
 選取篩選的運算子，例如 **[小於或等於]** 。
  
 **ReplTest1**  
 輸入篩選的值。 大多數運算子只需要第一個 **[值]** 資料行的值，但 **[介於]** 和 **[不介於]** 運算子則需要兩個 **[值]** 資料行中都有值。  
  
 **Clear**  
 按一下此按鈕即可清除先前已定義的所有篩選。  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft 複寫衝突檢視器 &#40;合併式複寫&#41;](../../relational-databases/replication/microsoft-replication-conflict-viewer-merge-replication.md)   
 [Microsoft 複寫衝突檢視器 &#40;異動複寫&#41;](../../relational-databases/replication/microsoft-replication-conflict-viewer-transactional-replication.md)  
  
  
