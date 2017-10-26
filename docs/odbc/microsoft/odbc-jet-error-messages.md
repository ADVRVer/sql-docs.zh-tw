---
title: "ODBC Jet 錯誤訊息 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- error messages (ODBC driver for oracle)
ms.assetid: f8d2a8f2-0316-42c4-bc34-5367661634ae
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0fad2aab1020cb7a56c00a2b78c1d2c46a41c422
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-jet-error-messages"></a>ODBC Jet 錯誤訊息
資料來源中發生的錯誤，ODBC 驅動程式會傳回錯誤訊息傳回至它的 ODBC 檔案程式庫。 ODBC 驅動程式或驅動程式管理員中發生的錯誤，錯誤訊息會根據的文字，則驅動程式傳回 SQLSTATE 與相關聯。  
  
 錯誤訊息的格式如下：  
  
```  
[vendor][ODBC-component][data-source]message-text  
```  
  
 括號 ([]) 中的前置詞識別錯誤的位置。 當發生錯誤時的驅動程式管理員 中*資料來源*未指定。 當錯誤發生在資料來源，[*廠商*] 和 [*ODBC 元件*] 前置詞識別供應商並收到錯誤，資料來源的 ODBC 元件名稱。  
  
 下表顯示驅動程式管理員和驅動程式 ISAM 所傳回的錯誤訊息：  
  
|錯誤訊息|錯誤的位置|  
|-------------------|--------------------|  
|[Microsoft][ODBC 驅動程式管理員]*訊息文字*|驅動程式管理員 (Odbc32.dll)|  
|[Microsoft][ODBC*驅動程式名稱*]*訊息文字*|驅動程式 ISAM （請參閱驅動程式 ISAMs）|

