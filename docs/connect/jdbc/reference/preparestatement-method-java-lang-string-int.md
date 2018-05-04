---
title: prepareStatement 方法 (java.lang.String) |Microsoft 文件
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e825765c-eb55-4800-951b-f3495da36641
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: afd095efadf10a6838fb5ba8f6abec6a6f9e0bb5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="preparestatement-method-javalangstring"></a>prepareStatement 方法 (java.lang.String)

建立[SQLServerPreparedStatement](./sqlserverpreparedstatement-class.md)物件以傳送參數化資料庫的 SQL 陳述式。

## <a name="syntax"></a>語法

```
public java.sql.PreparedStatement prepareStatement(java.lang.String sql)
```

#### <a name="parameters"></a>參數
*sql*

A**字串**包含 SQL 陳述式。

## <a name="return-value"></a>傳回值
PreparedStatement 物件。

## <a name="exceptions"></a>例外狀況  
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>備註
這個 prepareStatement 方法是由 java.sql.Connection 介面中的 prepareStatement 方法指定。

## <a name="see-also"></a>另請參閱

[prepareStatement 方法&#40;SQLServerConnection&#41;](./preparestatement-method-sqlserverconnection.md)

[SQLServerConnection 成員](./sqlserverconnection-members.md)

[SQLServerConnection 類別](./sqlserverconnection-class.md)
