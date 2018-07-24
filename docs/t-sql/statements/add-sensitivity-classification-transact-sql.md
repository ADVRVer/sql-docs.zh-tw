---
title: ADD SENSITIVITY CLASSIFICATION (Transact-SQL) | Microsoft Docs
ms.date: 06/17/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology: t-sql
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.custom: ''
ms.manager: craigg
ms.author: giladm
author: giladmit
f1_keywords:
- ADD SENSITIVITY CLASSIFICATION
- ADD_SENSITIVITY_CLASSIFICATION
dev_langs:
- TSQL
helpviewer_keywords:
- ADD SENSITIVITY CLASSIFICATION statement
- add labels
- adding labels
- adding labels
- classification [SQL]
- labels [SQL]
- information types
- data classification
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 9aa56df824fcad5da2ef2165e0a5e2e265331cd0
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38041636"
---
# <a name="add-sensitivity-classification-transact-sql"></a>ADD SENSITIVITY CLASSIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

將有關敏感度分類的中繼資料新增至一或多個資料庫資料行。 分類可包含敏感度標籤和資訊類型。  

將資料庫環境中的機密資料分類，可協助達到擴充可見度和更佳的防護。 [開始使用 SQL 資訊保護](https://aka.ms/sqlip)中可以找到其他資訊

## <a name="syntax"></a>語法  

```sql
ADD SENSITIVITY CLASSIFICATION TO
    <object_name> [, ...n ]
    WITH ( <sensitivity_label_option> [, ...n ] )     

<object_name> ::=
{
    [schema_name.]table_name.column_name
}

<sensitivity_label_option> ::=  
{   
    LABEL = string |
    LABEL_ID = guidOrString |
    INFORMATION_TYPE = string |
    INFORMATION_TYPE_ID = guidOrString  
}
```  

## <a name="arguments"></a>引數  

*object_name* ([schema_name.]table_name.column_name)

是要分類的資料庫資料行名稱。 目前只支援資料行分類。
    - *schema_name* (選用) - 是分類的資料行所屬的結構描述名稱。
    - *table_name* - 是分類的資料行所屬的資料表名稱。
    - *column_name* - 是所分類的資料行名稱。

*LABEL*

是人類看得懂的敏感度標籤名稱。 敏感度標籤代表資料庫資料行中所儲存資料的敏感度。

*LABEL_ID*

是與敏感度標籤相關聯的識別碼。 集中式資訊保護平台常用此來唯一識別系統中的標籤。

*INFORMATION_TYPE*

是人類看得懂的資訊類型名稱。 資訊類型是用來描述資料庫資料行中所儲存的資料類型。

*INFORMATION_TYPE_ID*

是與資訊類型相關聯的識別碼。 集中式資訊保護平台常用此來唯一識別系統中的資訊類型。


## <a name="remarks"></a>Remarks  

- 單一物件只能新增一個分類。 將分類新增至已分類的物件會覆寫現有的分類。
- 多個物件可使用單一 `ADD SENSITIVITY CLASSIFICTION` 陳述式來分類。
- 系統檢視 [sys.sensitivity_classifications](../../relational-databases/system-catalog-views/sys-sensitivity-classifications-transact-sql.md) 可用來擷取資料庫的敏感度分類資訊。


## <a name="permissions"></a>[權限]

需要 ALTER ANY SENSITIVITY CLASSIFICATION 權限。 ALTER ANY SENSITIVITY CLASSIFACTION 是由資料庫權限 ALTER，或由伺服器權限 CONTROL SERVER 默許。


## <a name="examples"></a>範例  

### <a name="a-classifying-two-columns"></a>A. 將兩個資料行分類

下列範例以 **Highly Confidential** 敏感度標籤與 **Financial** 資訊類型，將 **dbo.sales.price** 與 **dbo.sales.discount** 資料行分類。

```sql
ADD SENSITIVITY CLASSIFICATION TO
    dbo.sales.price, dbo.sales.discount
    WITH ( LABEL='Highly Confidential', INFORMATION_TYPE='Financial' )
```  

### <a name="b-classifying-only-a-label"></a>B. 僅分類標籤
下列範例以**Confidential** 標籤與標籤識別碼 **643f7acd-776a-438d-890c-79c3f2a520d6**，將**dbo.customer.comments** 資料行分類。 此資料行的資訊類型並未分類。

```sql
ADD SENSITIVITY CLASSIFICATION TO
    dbo.customer.comments
    WITH ( LABEL='Confidential', LABEL_ID='643f7acd-776a-438d-890c-79c3f2a520d6' )
```  

## <a name="see-also"></a>另請參閱  

[DROP SENSITIVITY CLASSIFICTION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[sys.sensitivity_classifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sensitivity-classifications-transact-sql.md)

[權限 (資料庫引擎)](https://docs.microsoft.com/en-us/sql/relational-databases/security/permissions-database-engine)

[開始使用 SQL 資訊保護](http://aka.ms/sqlip)
