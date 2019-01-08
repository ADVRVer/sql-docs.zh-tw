---
title: SQLDescribeCol | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDescribeCol function
ms.assetid: ffbf34c6-8268-434f-829a-82009a6cda59
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95d367efc0bf3fb3e3a74bd0ba9d48b9d8f25be2
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/13/2018
ms.locfileid: "53369840"
---
# <a name="sqldescribecol"></a>SQLDescribeCol
  對於執行的陳述式， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式不需要查詢伺服器來描述結果集資料行。 在此情況下，`SQLDescribeCol`不會造成伺服器往返。 像是[SQLColAttribute](sqlnumresultcols.md)，則呼叫`SQLDescribeCol`上備妥但未執行的陳述式會產生伺服器往返。  
  
 當 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式或陳述式批次傳回多個結果資料列集時，按序數參考的資料行有可能源自於個別的資料表，或是參考結果集中完全不同的資料行。 `SQLDescribeCol` 應該針對每個集呼叫。 當結果集變更時，應用程式應該在提取資料列結果以前先重新繫結資料值。 如需有關處理多個結果集傳回，請參閱[SQLMoreResults](sqlmoreresults.md)。  
  
 當已備妥的 SQL 陳述式批次產生多個結果集時，只有第一個結果集會報告資料行屬性。  
  
 大數值資料類型，傳回的值在*DataTypePtr*為 SQL_VARCHAR、 SQL_VARBINARY 或 SQL_NVARCHAR。 中的 SQL_SS_LENGTH_UNLIMITED 值*ColumnSizePtr*表示大小是 「 無限制 」。  
  
 在開始 database engine 的改進[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]允許 SQLDescribeCol 以取得更精確的預期結果的描述。 這些更精確的結果可能不同於在舊版的 SQLDescribeCol 傳回的值[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 中繼資料探索](../native-client/features/metadata-discovery.md)。  
  
## <a name="sqldescribecol-support-for-enhanced-date-and-time-features"></a>SQLDescribeCol 對增強型日期和時間功能的支援  
 針對日期/時間類型所傳回的值如下：  
  
||*DataTypePtr*|*ColumnSizePtr*|*DecimalDigitsPtr*|  
|-|-------------------|---------------------|------------------------|  
|DATETIME|SQL_TYPE_TIMESTAMP|23|3|  
|smalldatetime|SQL_TYPE_TIMESTAMP|16|0|  
|日期|SQL_TYPE_DATE|10|0|  
|time|SQL_SS_TIME2|8, 10..16|0..7|  
|datetime2|SQL_TYPE_TIMESTAMP|19, 21..27|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|26, 28..34|0..7|  
  
 如需詳細資訊，請參閱 <<c0> [ 日期和時間改善&#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</c0>  
  
## <a name="sqldescribecol-support-for-large-clr-udts"></a>SQLDescribeCol 對於大型 CLR UDT 的支援  
 `SQLDescribeCol` 支援大型 CLR 使用者定義型別 (UDT)。 如需詳細資訊，請參閱 < [Large CLR User-Defined 類型&#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQLDescribeCol 函數](https://go.microsoft.com/fwlink/?LinkID=59338)   
 [ODBC API 實作詳細資料](odbc-api-implementation-details.md)  
  
  
