---
title: 多語系支援 （Visual FoxPro ODBC 驅動程式） |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- double-byte character sets [ODBC]
- FoxPro ODBC driver [ODBC], international support
- DBCS [ODBC]
- international support [ODBC]
- sort order [ODBC]
- collating sequences [ODBC]
- Visual FoxPro ODBC driver [ODBC], international support
ms.assetid: cd3fab32-13f1-4a86-abc4-5e18667669fc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 151d3989737d221e46f6771055d0775c69f7e576
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32899913"
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>多語系支援 （Visual FoxPro ODBC 驅動程式）
Microsoft Visual FoxPro ODBC 驅動程式支援：  
  
-   雙位元組字元集 (DBCS)  
  
-   多個定序序列  
  
 定序的順序定義*排序次序*Visual FoxPro 資料表或資料庫中儲存的資料。 根據預設，此驅動程式被設定為使用支援的作業系統語言版本的定序序列。  
  
 如需支援的定序順序的清單，請參閱[設定 COLLATE](../../odbc/microsoft/set-collate-command.md)。  
  
## <a name="locale"></a>地區設定 (locale)  
 對應至給定的語言和國家/地區的資訊集。 地區設定會指出特定的設定，例如的十進位分隔符號、 日期和時間格式，以及字元排序順序。  
  
## <a name="sort-order"></a>排序次序 (sort order)  
 排序順序納入不同的排序規則*地區設定*s，讓您可以正確排序這些語言中的資料。 Visual FoxPro，在目前的排序次序會判斷字元運算式的比較和記錄出現在中編製索引或資料表的排序的順序的結果。
