---
title: 條件約束的西曆 |Microsoft 文件
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
- data types [ODBC], Gregorian calendar
- Gregorian calendar [ODBC]
ms.assetid: 70667410-c582-4369-8e06-9d98e21cd2bf
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 36cbe4802912e2497408498b32e48f8f201479f1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="constraints-of-the-gregorian-calendar"></a>西曆的條件約束
日期和日期時間資料類型和尾端欄位間隔資料型別，必須符合西曆的條件約束。 這些條件約束如下所示：  
  
-   月份欄位的值必須是介於 1 到 12 （含) 之間。  
  
-   日期欄位的值必須是介於 1 到該月份的天數。 月份的天數數目取決於年和月欄位的值，而且可以是 28、 29、 30 或 31。 （月份的天數數目可能也會相依於它是否為閏年。）  
  
-   小時欄位的值必須是介於 0 到 23 之間 （含） 之間。  
  
-   [分鐘] 欄位的值必須是介於 0 到 59 （含) 之間。  
  
-   Interval 資料類型的尾端秒欄位，如秒欄位的值必須是介於 0 到 59.9 (*n*) (含） 之間，其中*n*是數字的小數秒數有效位數的數目。  
  
-   尾端的秒欄位的日期時間資料型別，秒欄位的值必須介於 0 至 61.9 (*n*) (含） 之間，其中*n*指定"9"的數字的數目和值*n*小數秒數有效位數。 （秒的範圍可以讓維護恒星時間同步處理兩個閏秒）。
