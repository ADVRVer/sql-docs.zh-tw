---
title: 對應的資料指標 Attributes1 資訊類型 |Microsoft 文件
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
- compatibility [ODBC], mapping cursor attributes1 information types
- application upgrades [ODBC], mapping cursor attributes1 information types
- mapping cursor attributes1 information types [ODBC]
- backward compatibility [ODBC], mapping cursor attributes1 information types
- upgrading applications [ODBC], mapping cursor attributes1 information types
ms.assetid: 9f112449-ca86-45ac-a865-e6174d67f91b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec986c2feea1b5c2ef64de87d64944ce0d184898
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="mapping-the-cursor-attributes1-information-types"></a>對應的資料指標 Attributes1 資訊類型
當 ODBC 3。*x*應用程式會呼叫**SQLGetInfo** ODBC 2 *.x* SQL_XXXX_CURSOR_ATTRIBUTES1 資訊類型的驅動程式 (如動態、 順向的索引鍵集驅動程式，或靜態資料指標） 驅動程式管理員傳回的位元設定取決於 ODBC 2。*x*驅動程式會傳回對應的 ODBC 2。*x*資訊類型。 下表所示，會設定位元。  
  
|位元<br /><br /> SQL_XXXX_CURSOR_ATTRIBUTES1|資料指標類型|ODBC 2。*x*資訊<br /><br /> 型別|  
|-----------------------------------------------|-----------------|-------------------------------------|  
|SQL_CA1_NEXT|全部|SQL_FETCH_DIRECTION|  
|SQL_CA1_ABSOLUTE SQL_CA1_RELATIVE SQL_CA1_BOOKMARK|動態的索引鍵集驅動程式靜態|SQL_FETCH_DIRECTION|  
|SQL_CA1_LOCK_NO_CHANGE SQL_CA1_LOCK_UNLOCK SQL_CA1_LOCK_EXCLUSIVE|動態的索引鍵集驅動程式靜態|SQL_LOCK_TYPES|  
|SQL_CA1_POSITIONED_UPDATE SQL_CA1_POSITIONED_DELETE SQL_CA1_SELECT_FOR_UPDATE|全部|SQL_POSITIONED_STATEMENTS|  
|SQL_CA1_POS_POSITION SQL_CA1_POS_DELETE SQL_CA1_POS_REFRESH SQL_CA1_POS_BULK_ADD|動態的索引鍵集驅動程式靜態|SQL_POS_OPERATIONS|
