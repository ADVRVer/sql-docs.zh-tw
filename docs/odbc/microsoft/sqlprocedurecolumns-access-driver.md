---
title: SQLProcedureColumns （存取驅動程式） |Microsoft 文件
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
- Access driver [ODBC], SQLProcedureColumns
- SQLProcedureColumns function [ODBC], Access Driver
ms.assetid: 34fee995-5848-4ecb-bda0-fc362a77b2d9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f293c0af98eb262abd838c957e0228dc8b69a813
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="sqlprocedurecolumns-access-driver"></a>SQLProcedureColumns （存取驅動程式）
> [!NOTE]  
>  本主題提供存取驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC 應用程式開發介面參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 應用程式開發人員應該尋找驅動程式定義資料行結果集的結尾開始並繼續向後。  
  
|資料行|註解|  
|------------|--------------|  
|COLUMN_TYPE|SQL_PARAM_INPUT 或 SQL_RESULT_COL|  
|序數|這是傳回的結果集結尾的驅動程式專用資料行。 資料行的 SQL 類型是整數。|
