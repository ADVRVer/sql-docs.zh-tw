---
title: SQLFreeStmt 對應 |Microsoft 文件
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
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeStmt function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeStmt
ms.assetid: 267d95f2-4f0c-47ab-9411-5afe105215a2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77392dff0f22fcabd26b54cad700bb5cebcde2bf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="sqlfreestmt-mapping"></a>SQLFreeStmt 對應
當應用程式呼叫**SQLFreeStmt**與*選項*引數到 ODBC 3 SQL_DROP *.x*驅動程式，會呼叫  
  
```  
SQLFreeStmt(hstmt, SQL_DROP)   
```  
  
 對應到  
  
```  
SQLFreeHandle(SQL_HANDLE_STMT,Handle)  
```  
  
 與*處理*引數設定中的值為*hstmt*。
