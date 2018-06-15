---
title: execute 方法 (java.lang.String，int[]) |Microsoft 文件
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerStatement.execute (javal.lang.String.int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc73d1c3-e756-43af-b1fc-ac438cbd0965
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: afe080df57157ae62e604ff8057027a45df39fc1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32833323"
---
# <a name="execute-method-javalangstring-int"></a>execute 方法 (java.lang.String, int[])

  執行給定的 SQL 陳述式，可傳回多個結果，以及訊號[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion-md.md)]給定陣列中所指出的自動產生索引鍵應該進行擷取。

## <a name="syntax"></a>語法

```Java
public final boolean execute(
    java.lang.String sql,
    int[] columnIndexes)
```

#### <a name="parameters"></a>參數
*sql*

包含 SQL 陳述式的**字串**。

*columnIndexes*

陣列**int**，指出應該提供的自動產生索引鍵的資料行索引。

## <a name="return-value"></a>傳回值
**true**如果第一個結果是結果集。 否則為 **false**。
  
## <a name="exceptions"></a>例外狀況
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>備註
這個 execute 方法是由 java.sql.Statement 介面中的 execute 方法中指定。

## <a name="see-also"></a>另請參閱

[execute 方法&#40;SQLServerStatement&#41;](./execute-method-sqlserverstatement.md)

[SQLServerStatement 成員](./sqlserverstatement-members.md)

[SQLServerStatement 類別](./sqlserverstatement-class.md)
