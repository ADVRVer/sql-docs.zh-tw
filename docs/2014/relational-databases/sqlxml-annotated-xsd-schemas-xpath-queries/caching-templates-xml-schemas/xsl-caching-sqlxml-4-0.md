---
title: XSL 快取 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- XSL caching [SQLXML]
ms.assetid: 91994142-32f0-4d8d-a8cf-eb0d8b1f1999
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9c23a208a0276a2a3eb71f493aa7e5ce7fad0928
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62805821"
---
# <a name="xsl-caching-sqlxml-40"></a>XSL 快取 (SQLXML 4.0)
  快取 XSL 樣式表可以改善效能。 第一次執行之後，如果 XSL 快取設定為 ON，XSL 樣式表仍保持在記憶體中；這樣可以改善後續處理的效能。 預設值是 ON。  
  
 您可以在登錄中加入下列機碼來設定 XSL 快取大小：  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\XSLCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 XSL 快取大小應該根據可用的記憶體以及您要使用的 XSL 樣式表數目來設定。 預設值是**XSLCacheSize**大小為 31。 如果 XSL 存取速度似乎緩慢，您可以增加快取大小，或者如果記憶體不足，則減少快取大小。  
  
 為了達到最佳效能，建議您設定**XSLCacheSize**比您通常使用的 XSL 樣式表數目高。 如果**XSLCacheSize**是小於的數目 XSL 樣式的表，效能會隨著 XSL 樣式表會增加數目。 **XSLCacheSize**可以設為上限 128。  
  
 每次使用快取的 XSL 樣式表時，就會檢查 XSL 檔的修改時間以判斷該 XSL 檔是否需要重新整理。 這是因為磁碟副本比快取副本新的緣故。  
  
## <a name="see-also"></a>另請參閱  
 [範本快取&#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md)   
 [結構描述快取&#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md)  
  
  
