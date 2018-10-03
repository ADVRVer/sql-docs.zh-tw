---
title: SQLGetConnectOption 對應 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLGetConnectOption
- SQLGetConnectOption function [ODBC], mapping
ms.assetid: e3792fe4-a955-473a-a297-c1b2403660c4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8504709cb2cedb36c62bb9be74ffc8d12a4c811d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745786"
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
  
-   如果*fOption*指出傳回 32 位元整數值，此驅動程式管理員會呼叫 ODBC 定義的連接選項  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   如果*fOption*表示驅動程式定義的陳述式選項，此驅動程式管理員會呼叫  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 在上述三種情況下， *ConnectionHandle*引數設定中的值為*hdbc*，則*屬性*引數設定中的值為*fOption*，而*ValuePtr*引數設定為相同的值*pvParam*。  
  
 如 ODBC 定義的字串連接選項，請設定驅動程式管理員*Columnsize*呼叫中的引數**SQLGetConnectAttr**預先定義的最大長度 (SQL_MAX_OPTION_STRING_LENGTH);非連線選項，如*Columnsize*設為 0。  
  
 適用於 ODBC 3 *.x*驅動程式，則驅動程式管理員不會再檢查，看看是否*選項*介於 SQL_CONN_OPT_MIN 和 SQL_CONN_OPT_MAX，或大於 SQL_CONNECT_OPT_DRVR_START。 此驅動程式必須檢查的選項值的有效性。
