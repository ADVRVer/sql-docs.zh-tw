---
title: 將二進位格式的資料傳輸 |Microsoft 文件
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
- data types [ODBC], transferring in binary form
- transferring data in binary form [ODBC]
- binary data transfers [ODBC]
ms.assetid: 4b12a9de-51d0-416a-87f4-9bf84959cad9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d2d1227af9eeb303bc0d9bc56733e6bda9b5325c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="transferring-data-in-its-binary-form"></a>將二進位格式的資料傳輸
應用程式可以安全地在兩個資料來源使用相同的 DBMS 和硬體平台之間傳輸資料 （在指定的 DBMS 所使用的內部形式）。 給定的資料片段，SQL 資料類型必須是相同的來源和目標資料來源。 C 資料類型是 SQL_C_BINARY。  
  
 當應用程式呼叫**SQLFetch**， **SQLFetchScroll**，或**SQLGetData**驅動程式要從原始資料來源擷取資料，從資料擷取資料來源與傳輸，不需要轉換，到類型 SQL_C_BINARY 的存放位置。 當應用程式呼叫**SQLBulkOperations**， **SQLExecute**， **SQLExecDirect**， **SQLPutData 或 SQLSetPos**來傳送資料到目標資料來源驅動程式會從儲存體位置擷取資料，並傳輸，不需要轉換，到目標資料來源。  
  
> [!NOTE]  
>  以這種方式傳送任何資料 （二進位資料除外） 的應用程式不在 Dbms 之間的互通。  
  
 **SQLCopyDesc**可用來複製來源 DBMS 中的資料列繫結目標 DBMS 中的參數繫結。
