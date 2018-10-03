---
title: 使用自動擷取搭配 ODBC 資料指標 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 343975c2c6ad39c67dcd10c0d55886d21e69f3f5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076308"
---
# <a name="using-autofetch-with-odbc-cursors"></a>使用自動擷取搭配 ODBC 資料指標
  當連接到的執行個體[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，則[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式時使用任何伺服器資料指標類型，支援自動擷取選項。 使用自動擷取時， **SQLExecute**或是**SQLExecDirect**開啟資料指標的函式也具有隱含[SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST) 函數。 構成第一個資料列集的資料列會當做陳述式執行的一部分而傳回至繫結的應用程式變數，如此就不需要再一次透過網路往返伺服器。 [SQLGetData](../../native-client-odbc-api/sqlgetdata.md)時不支援已啟用自動擷取選項; 將結果集資料行必須繫結至程式變數。  
  
 應用程式會藉由將驅動程式特定的 SQL_SOPT_SS_CURSOR_OPTIONS 陳述式屬性設定為 SQL_CO_AF 來要求自動擷取。  
  
## <a name="see-also"></a>另請參閱  
 [資料指標程式設計詳細資料&#40;ODBC&#41;](cursor-programming-details-odbc.md)  
  
  
