---
title: SQLSpecialColumns |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b205e2637e9588404926d8d0e73016765cd54c56
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48107528"
---
# <a name="sqlspecialcolumns"></a>SQLSpecialColumns
  當要求資料列識別碼 (*IdentifierType* SQL_BEST_ROWID)， **SQLSpecialColumns**針對 SQL_SCOPE_CURROW 以外的任何要求範圍傳回空的結果集 （無資料列）。 產生的結果集表示資料行只有在這個範圍中才是有效的。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不支援識別碼的虛擬資料行。 **SQLSpecialColumns**結果集將會將所有資料行識別為 SQL_PC_NOT_PSEUDO。  
  
 **SQLSpecialColumns**可以在靜態資料指標上執行。 嘗試執行**SQLSpecialColumns**上可更新 （索引鍵集驅動或動態） 會傳回 SQL_SUCCESS_WITH_INFO，指出資料指標類型已經變更。  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a>增強型日期和時間功能的 SQLSpecialColumns 支援  
 如需值的資訊傳回的資料行 DATA_TYPE、 TYPE_NAME、 COLUMN_SIZE、 BUFFER_LENGTH 和 DECIMAL_DIGTS 日期/時間類型，請參閱 < [Catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md)。  
  
 如需詳細資訊，請參閱 <<c0> [ 日期和時間改善&#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</c0>  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a>大型 CLR UDT 的 SQLSpecialColumns 支援  
 **SQLSpecialColumns**支援大型 CLR 使用者定義型別 (Udt)。 如需詳細資訊，請參閱 < [Large CLR User-Defined 類型&#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQLSpecialColumns 函數](http://go.microsoft.com/fwlink/?LinkId=59371)   
 [ODBC API 實作詳細資料](odbc-api-implementation-details.md)  
  
  
