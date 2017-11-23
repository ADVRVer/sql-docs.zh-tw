---
title: "ODBC 資料來源的子機碼 |Microsoft 文件"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC], for data sources
- data sources [ODBC], subkeys
- registry entries for data sources [ODBC], subkeys
ms.assetid: 0a8ccb80-c573-4418-84e5-f04a2b0e2ac1
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c3d2ed7d39772237f522320f227c49c773d12801
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2017
---
# <a name="odbc-data-sources-subkey"></a>ODBC 資料來源子機碼
ODBC 資料來源的子機碼下的值清單的資料來源。 這些值的格式為下表所示。  
  
|名稱|資料類型|data|  
|----------|---------------|----------|  
|*資料來源名稱*|REG_SZ|*驅動程式說明*|  
  
 *資料來源名稱*值由管理程式 （這通常它會提示使用者），定義和*驅動程式描述*定義驅動程式開發者 (通常是名稱DBMS 驅動程式相關聯)。  
  
 例如，假設已定義三個資料來源： 清查，這樣會使用 SQL Server;使用 dBASE; 的薪資和人員，它會使用格式化的文字檔案。 ODBC 資料來源的子機碼下的值可能如下所示：  
  
```  
Inventory : REG_SZ : SQL Server  
Payroll : REG_SZ : dBASE  
Personnel : REG_SZ : Text  
```
