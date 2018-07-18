---
title: SQLGetConnectOption 對應 |Microsoft 文件
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
- mapping deprecated functions [ODBC], SQLGetConnectOption
- SQLGetConnectOption function [ODBC], mapping
ms.assetid: e3792fe4-a955-473a-a297-c1b2403660c4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ec36a536732299337efde3cf58cc98fbf4c46e0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906733"
---
# <a name="sqlgetconnectoption-mapping"></a>SQLGetConnectOption 對應
當應用程式呼叫**SQLGetConnectOption**透過 ODBC 3 *.x*驅動程式，會呼叫  
  
```  
SQLGetConnectOption(hdbc, fOption, pvParam)   
```  
  
 會對應，如下所示：  
  
-   如果*fOption*指出傳回的字串，此驅動程式管理員會呼叫 ODBC 定義的連接選項  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   如果*fOption*指出傳回 32 位元整數值，驅動程式管理員呼叫 ODBC 定義的連接選項  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   如果*fOption*表示驅動程式定義陳述式選項，驅動程式管理員呼叫  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 在前述三個情況下， *ConnectionHandle*引數設定中的值為*hdbc*、*屬性*引數設定中的值為*fOption*，而*ValuePtr*引數設定為相同的值做為*pvParam*。  
  
 針對 ODBC 定義的字串連接選項，設定驅動程式管理員*Columnsize*引數在呼叫**SQLGetConnectAttr**預先定義的最大長度 (SQL_MAX_OPTION_STRING_LENGTH);將非字串的連接選項，如*Columnsize*設為 0。  
  
 ODBC 3 *.x*驅動程式，驅動程式管理員不會再檢查，看看是否*選項*之間 SQL_CONN_OPT_MIN 和 SQL_CONN_OPT_MAX，或大於 SQL_CONNECT_OPT_DRVR_START。 驅動程式必須檢查的選項值的有效性。
