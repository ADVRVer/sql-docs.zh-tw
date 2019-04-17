---
title: HASHBYTES (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HASHBYTES_TSQL
- HASHBYTES
dev_langs:
- TSQL
helpviewer_keywords:
- hash input
- HASHBYTES
ms.assetid: 0ea6a4d1-313e-4f70-b939-dd2cd570f6d6
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fb4a69420f4fc3ac7881b2798ef97fc0b202a31f
ms.sourcegitcommit: 5f38c1806d7577f69d2c49e66f06055cc1b315f1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59429384"
---
# <a name="hashbytes-transact-sql"></a>HASHBYTES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回其在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中輸入的 MD2、MD4、MD5、SHA、SHA1 或 SHA2 雜湊。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
HASHBYTES ( '<algorithm>', { @input | 'input' } )  
  
<algorithm>::= MD2 | MD4 | MD5 | SHA | SHA1 | SHA2_256 | SHA2_512   
```  
  
## <a name="arguments"></a>引數  
 **'**\<algorithm>**'**  
 識別用來雜湊輸入的雜湊演算法。 這是必要的引數，沒有預設值。 必須加上單引號。 從 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 開始，取代 SHA2_256 和 SHA2_512 以外的所有演算法。  
  
 **@input**  
 指定含有要雜湊之資料的變數。 **@input** 為 **varchar**、**nvarchar**，或 **varbinary**。  
  
 **'** *input* **'**  
 指定運算式，這個運算式評估為要雜湊的字元或二進位字串。  
  
 輸出符合演算法標準：適用於 MD2、MD4 和 MD5 的 128 位元 (16 位元組)；適用於 SHA 和 SHA1 的 160 位元 (20 位元組)；適用於 SHA2_256 的 256 位元 (32 位元組)，以及適用於 SHA2_512 的 512 位元 (64 位元組)。  
  
**適用於**：[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 針對 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 及更早版本，允許的輸入值限制為 8000 個位元組。  
  
## <a name="return-value"></a>傳回值  
 **varbinary** (最大 8000 位元組)  

## <a name="remarks"></a>Remarks  
請考慮使用 `CHECKSUM` 或 `BINARY_CHECKSUM` 作為計算雜湊值的替代方案。

從 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 開始已淘汰 MD2、MD4、MD5、SHA 和 SHA1。 請改用 SHA2_256 或 SHA2_512。 較舊的演算法會繼續運作，但它們會引發淘汰事件。

## <a name="examples"></a>範例  
### <a name="return-the-hash-of-a-variable"></a>傳回變數的雜湊  
 下列範例會傳回儲存於 `@HashThis` 變數中 **nvarchar** 資料的 `SHA1` 雜湊。  
  
```sql  
DECLARE @HashThis nvarchar(4000);  
SET @HashThis = CONVERT(nvarchar(4000),'dslfdkjLK85kldhnv$n000#knf');  
SELECT HASHBYTES('SHA1', @HashThis);  
```  
  
### <a name="return-the-hash-of-a-table-column"></a>傳回資料表資料行的雜湊  
 下列範例會傳回 `c1` 資料表 `Test1` 資料行中之值的 SHA1 雜湊。  
  
```sql  
CREATE TABLE dbo.Test1 (c1 nvarchar(50));  
INSERT dbo.Test1 VALUES ('This is a test.');  
INSERT dbo.Test1 VALUES ('This is test 2.');  
SELECT HASHBYTES('SHA1', c1) FROM dbo.Test1;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-------------------------------------------  
0x0E7AAB0B4FF0FD2DFB4F0233E2EE7A26CD08F173  
0xF643A82F948DEFB922B12E50B950CEE130A934D6  
  
(2 row(s) affected)  
```  
  
## <a name="see-also"></a>另請參閱  
[選擇加密演算法](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
[CHECKSUM_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/checksum-agg-transact-sql.md)  
[CHECKSUM &#40;Transact-SQL&#41;](../../t-sql/functions/checksum-transact-sql.md)  
[BINARY_CHECKSUM &#40;Transact-SQL&#41;](../../t-sql/functions/binary-checksum-transact-sql.md)  
  
