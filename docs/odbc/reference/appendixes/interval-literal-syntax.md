---
title: 間隔常值的語法 |Microsoft 文件
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
- literals [ODBC], interval
- interval literals [ODBC]
- ODBC literals [ODBC], interval
ms.assetid: 2f2d22c1-51d6-4055-9f5a-53bc31e9fea0
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 016a4fa307e9bda697dde5eec81ce606ad07a19b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="interval-literal-syntax"></a>間隔常值的語法
下列語法用於間隔 ODBC 中的常值。  
  
 *間隔常值:: = 間隔*[+*&#124;*-]*間隔字串間隔限定詞*  
  
 *時間間隔字串*:: =*引號*{*年-月-常值* &#124; *日期時間常值*}*引號*  
  
 *常值年-月*:: =*年份值* &#124; [*年份值*-]*月份值*  
  
 *日期時間常值*:: =*天的時間間隔* &#124; *時間間隔*  
  
 *日期時間間隔*:: =*天數值*[*小時值*[:*分鐘值*[:*秒數值*]]]  
  
 *時間間隔*:: =*小時值*[:*分鐘值*[:*秒數值*]]  
  
 &#124;*分鐘值*[:*秒數值*]  
  
 &#124;*秒數值*  
  
 *年份值*:: =*日期時間值*  
  
 *月份值*:: =*日期時間值*  
  
 *天數值*:: =*日期時間值*  
  
 *小時值*:: =*日期時間值*  
  
 *分鐘值*:: =*日期時間值*  
  
 *秒數值*:: =*秒整數值*[。 [*秒分數*]]  
  
 *秒數的整數值*:: =*不帶正負號整數*  
  
 *秒數部分*:: =*不帶正負號整數*  
  
 *日期時間值*:: =*不帶正負號整數*  
  
 *間隔限定詞*:: =*開始欄位*TO*結束欄位* &#124; *單一日期時間欄位*  
  
 *開始欄位*:: =*非第二個-datetime-欄位*[(*間隔前置欄位的精確度*)]  
  
 *結束欄位*:: =*非第二個-datetime-欄位*&#124;第二個 [(*間隔位小數的秒數-有效位數*)]  
  
 *單一日期時間欄位*:: =*非第二個-datetime-欄位*[(*間隔前置欄位的精確度*)]&#124;第二個 [(*間隔前置欄位的精確度* [，(*間隔位小數的秒數-有效位數*)]  
  
 *datetime 欄位*:: =*非第二個-datetime-欄位*&#124;第二個  
  
 *非第二個-datetime-欄位*:: = 年&#124;月份&#124;天&#124;小時&#124;分鐘  
  
 *間隔位小數的秒數-有效位數*:: =*不帶正負號整數*  
  
 *間隔開頭欄位的精確度*:: =*不帶正負號整數*  
  
 *引號*:: = '  
  
 *不帶正負號整數*:: =*位數...*
