---
title: 支援 ODBC SQL 文法 （Visual FoxPro ODBC 驅動程式） |Microsoft 文件
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
- native Visual FoxPro language syntax [ODBC]
- FoxPro ODBC driver [ODBC], SQL grammar
- SQL grammar [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], SQL grammar
- grammar support in Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
- FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
ms.assetid: f41a38c2-e22e-4c65-a32e-9a6777435160
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7eccb1bbdb86ded6b949756b4e5762a83a59fc0e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906913"
---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>支援的 ODBC SQL 文法 （Visual FoxPro ODBC 驅動程式）
Microsoft Visual FoxPro ODBC 驅動程式支援以下功能：  
  
-   所有 SQL 陳述式和 ODBC 的最小 SQL 文法中的子句  
  
-   其他的 SQL 陳述式，從 ODBC core SQL 文法  
  
 下表列出支援的驅動程式時，由 ODBC SQL 文法層級的項目。  
  
|Level|元素|項目|  
|-----------|--------------|----------|  
|最小值|資料定義語言 (DDL)|CREATE TABLE 和 DROP TABLE|  
||資料操作語言 (DML)|選取、 插入、 更新和刪除|  
||運算式|簡單 (例如 A > C B +)|  
||資料類型|CHAR、 VARCHAR 或 LONG VARCHAR|  
  
 除了支援的 ODBC SQL 文法，Visual FoxPro ODBC 驅動程式也支援下列 Visual FoxPro 命令的完整原生 Visual FoxPro 語言語法：  
  
 [ALTER TABLE](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)  
  
 [DELETE](../../odbc/microsoft/delete-sql-command.md)  
  
 [刪除標記](../../odbc/microsoft/delete-tag-command.md)  
  
 [DROP TABLE](../../odbc/microsoft/drop-table-command.md)  
  
 [INDEX](../../odbc/microsoft/index-command.md)  
  
 [INSERT](../../odbc/microsoft/insert-sql-command.md)  
  
 [SELECT](../../odbc/microsoft/select-sql-command.md)  
  
 [UPDATE](../../odbc/microsoft/update-sql-command.md)
