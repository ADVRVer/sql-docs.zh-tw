---
title: executeUpdate 方法 (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeUpdate (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 91ecb1cd-001d-4ac9-9ae8-5db05c3c2959
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8c408098ebe1e9e732b171390eb1901f01014292
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "66804144"
---
# <a name="executeupdate-method-javalangstring"></a>executeUpdate 方法 (java.lang.String)

執行可能是 INSERT、UPDATE、MERGE 或 DELETE 陳述式的給定 SQL 陳述式，否則會是不傳回任何項目的 SQL 陳述式，例如 SQL DDL 陳述式。

## <a name="syntax"></a>語法

```
public final int executeUpdate(java.lang.String sql)
```

#### <a name="parameters"></a>參數
*sql*

包含 SQL 陳述式的 **String**。

## <a name="return-value"></a>傳回值
**int** 會指出受影響的資料列數目，如果是使用 DDL 陳述式，則為 0。

## <a name="exceptions"></a>例外狀況
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>備註
這個 executeUpdate 方法是由 java.sql.PreparedStatement 介面中的 executeUpdate方法指定。

呼叫這個方法將會產生例外狀況，因為當建立 SQLServerPreparedStatement 物件時，已指定此物件的 SQL 陳述式。

## <a name="see-also"></a>另請參閱

[executeUpdate 方法 &#40;SQLServerPreparedStatement&#41;](./executeupdate-method-sqlserverpreparedstatement.md)

[SQLServerPreparedStatement 成員](./sqlserverpreparedstatement-members.md)

[SQLServerPreparedStatement 類別](./sqlserverpreparedstatement-class.md)
