---
title: 字串函式 （Visual FoxPro ODBC 驅動程式） |Microsoft 文件
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ODBC string functions [ODBC]
- string functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], string functions
- FoxPro ODBC driver [ODBC], string functions
ms.assetid: 1974fd26-ef0d-45d5-860b-298917c8e9c3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 482c21b4c9f872490ac9a2d36165fdc3fc9d8246
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>字串函式 （Visual FoxPro ODBC 驅動程式）
下表列出 Visual FoxPro ODBC 驅動程式; 支援 ODBC 字串操作函數當相同的函式的 Visual FoxPro 文法與 ODBC 語法，會列出 Visual FoxPro 相等。  
  
|ODBC 文法|Visual FoxPro 文法|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|ASC *(string_exp)*|  
|CHAR *（程式碼）*|CHR *(string_exp)*|  
|CONCAT *(string_exp1 string_exp2)*|*string_exp1 + string_exp2*|  
|差異*(string_exp1 string_exp2)*||  
|插入*(string_exp1，開始、 長度、 string_exp2)*|STUFF *(string_exp1，開始、 長度、 string_exp2)*|  
|LCASE *(string_exp)*|較低*(string_exp)*|  
|左*(string_exp 計數)*||  
|長度*(string_exp)*|LEN *(string_exp)*|  
|LTRIM *(string_exp)*||  
|重複*(string_exp 計數)*|複寫*(string_exp 計數)*|  
|取代*(string_exp1，string_exp2，string_exp3)*|STRTRAN *(string_exp1，string_exp2，string_exp3)*|  
|右*(string_exp 計數)*||  
|RTRIM *(string_exp)*||  
|SOUNDEX *(string_exp)*||  
|空間*（計數）*||  
|子字串*(string_exp，開始時，長度)*|SUBSTR *(string_exp，開始時，長度)*|  
|UCASE *(string_exp)*|上方*(string_exp)*|
