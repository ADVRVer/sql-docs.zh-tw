---
title: "CREATE INDEX 陳述式 |Microsoft 文件"
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
- CREATE INDEX [ODBC]
- SQL grammar [ODBC], create index
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0f6e7525059640e7ffdadd79ec26a62229eabae9
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="create-index-statement"></a>CREATE INDEX 陳述式
CREATE INDEX 陳述式的語法為：  
  
 建立 [唯一] 索引*索引名稱*ON*資料表名稱*(*資料行識別碼*[ASC] [DESC] [，*資料行識別碼*[ASC][DESC]...])與\<*索引選項清單*>  
  
 其中\<*索引選項清單*> 可以是： 主要檔案群組 &#124;不允許 NULL &#124;忽略 NULL  
  
 Microsoft Access 驅動程式會使用不允許 NULL 和 NULL 忽略索引選項。 DBASE 和 Paradox 驅動程式接受語法，但略過的其中一個選項。  
  
 使用 Paradox 驅動程式時，CREATE INDEX 陳述式會建立 Paradox 主要金鑰檔案，然後次要檔案。  
  
 這個陳述式不支援的 Microsoft Excel 或文字的驅動程式。
