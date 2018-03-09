---
title: "記錄的與有沒有修改 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-text-image-columns
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
caps.latest.revision: "29"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4cf91e1b77d1d6731d73653682320e1c61eec734
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="logged-vs-unlogged-modifications"></a>記錄的與有沒有的修改
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  應用程式可以要求[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式不要記錄**文字**， **ntext**，和**映像**修改。 但是在使用這個選項時，應該要特別小心。 它應該僅適用於這些情況下其中**文字**， **ntext**，或**映像**資料並不重要，而且資料擁有者願意取捨就能夠復原資料較高的效能。  
  
 記錄**文字**， **ntext**，和**映像**修改由呼叫[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)與*屬性*參數設定為 SQL_SOPT_SS_ TEXTPTR_LOGGING 以及*ValuePtr*設定為 SQL_TL_ON 或 sql_tl_off 所控制。  
  
## <a name="see-also"></a>另請參閱  
 [管理 Text 和 Image 資料行](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
