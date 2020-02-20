---
title: execute 方法 (java.lang.String, int[]) | Microsoft Docs
ms.custom: ''
ms.date: 02/07/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.execute (javal.lang.String.int[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc73d1c3-e756-43af-b1fc-ac438cbd0965
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6e96e0c9c957522db6a766b3491d394b7337d7b6
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/31/2020
ms.locfileid: "67954986"
---
# <a name="execute-method-javalangstring-int"></a>execute 方法 (java.lang.String, int[])

  執行可傳回多個結果的指定 SQL 陳述式，並向 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 發出訊號，通知必須提供指定陣列所指出的自動產生索引鍵以進行擷取。

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

**int** 的陣列，這些值指出必須提供自動產生索引鍵的資料行索引。

## <a name="return-value"></a>傳回值
如果第一個結果是結果集，則為 **true** 否則為 **false**。
  
## <a name="exceptions"></a>例外狀況
[SQLServerException](./sqlserverexception-class.md)

## <a name="remarks"></a>備註
這個 execute 方法是由 java.sql.Statement 介面中的 execute 方法指定。

## <a name="see-also"></a>另請參閱

[execute 方法 &#40;SQLServerStatement&#41;](./execute-method-sqlserverstatement.md)

[SQLServerStatement 成員](./sqlserverstatement-members.md)

[SQLServerStatement 類別](./sqlserverstatement-class.md)
