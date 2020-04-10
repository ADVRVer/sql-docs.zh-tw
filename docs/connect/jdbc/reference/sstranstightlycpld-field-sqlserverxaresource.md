---
title: SSTRANSTIGHTLYCPLD 欄位 (SQLServerXAResource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apilocation:
- SSTRANSTIGHTLYCPLD Field (SQLServerXAResource)
apitype: Assembly
ms.assetid: 379857c3-9de1-4964-8782-32df317cbfbb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d6d816ba896b792894716b9b61b133d1acea0c93
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925645"
---
# <a name="sstranstightlycpld-field-sqlserverxaresource"></a>SSTRANSTIGHTLYCPLD 欄位 (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  用來允許緊密結合的 XA 交易，這些交易擁有不同的 XA 分支交易識別碼 (XID)，但是擁有相同的全域交易識別碼 (GTRID)。  
  
## <a name="syntax"></a>語法  
  
```  
  
public static final int SSTRANSTIGHTLYCPLD  
```  
  
## <a name="field-value"></a>欄位值  
 為 32768 的 **int** 值。  
  
## <a name="remarks"></a>備註  
 每一筆交易都是由 XA 分支交易識別碼 (XID) 和全域交易識別碼 (GTRID) 所識別。 為了讓應用程式使用緊密結合的 XA 交易 (這些交易擁有不同的 XID，但是有相同的 GTRID)，您必須在 XAResource.start 方法的 flags 參數上設定 [SSTRANSTIGHTLYCPLD](../../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md)。 如需如何使用此旗標的詳細資訊，請參閱[了解 XA 交易](../../../connect/jdbc/understanding-xa-transactions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerXAResource 欄位](../../../connect/jdbc/reference/sqlserverxaresource-fields.md)   
 [SQLServerXAResource 成員](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource 類別](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
