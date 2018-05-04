---
title: 預設資料來源 |Microsoft 文件
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
- data sources [ODBC], connection functions
- connecting to data source [ODBC], default data source
- functions [ODBC], data source or driver connections
- data sources [ODBC], default
- default data source [ODBC]
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], default data source
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: dd473cc6-f051-4aa0-ab14-3dd1b37fe99e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3aeb96caca91b681ec7d2a9d34548ba6bac1147f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="default-data-source"></a>預設的資料來源
驅動程式可能會選取資料來源，呼叫預設的資料來源，在某些情況下，應用程式並未明確指定其中一個：  
  
-   在呼叫**SQLConnect**其中*ServerName*引數是零長度字串、 null 指標或 DEFAULT。  
  
-   在呼叫**SQLDriverConnect**其中*InConnectionString*是指定**DSN**= 預設值或指定**DSN**關鍵字並未包含在系統資訊的資料來源。  
  
 它為驅動程式定義的預設資料來源指定的方式。 這可能牽涉到系統管理動作，可能會取決於使用者。
