---
description: SIGNBYASYMKEY (Transact-SQL)
title: SIGNBYASYMKEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SIGNBYASYMKEY_TSQL
- SIGNBYASYMKEY
dev_langs:
- TSQL
helpviewer_keywords:
- text signing [SQL Server]
- encryption [SQL Server], asymmetric keys
- signing text [SQL Server]
- SIGNBYASYMKEY function
- asymmetric keys [SQL Server], SIGNBYASYMKEY function
- cryptography [SQL Server], asymmetric keys
- clear text signing
ms.assetid: b1c46159-cc76-4205-a841-8f4a71742f80
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: b90807f116b115e3e4756791d821ea9bad85f14e
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2020
ms.locfileid: "91378854"
---
# <a name="signbyasymkey-transact-sql"></a>SIGNBYASYMKEY (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  使用非對稱金鑰簽署純文字。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```syntaxsql
SignByAsymKey( Asym_Key_ID , @plaintext [ , 'password' ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>引數
 *Asym_Key_ID*  
 為目前資料庫中非對稱金鑰的識別碼。 *Asym_Key_ID* 為 **int**。  
  
 **\@plaintext**  
 為 **nvarchar**、**char**、**varchar** 或 **nchar** 類型的變數，其中包含要以非對稱金鑰簽署的資料。  
  
 *password*  
 為用來保護私密金鑰的密碼。 *password* 為 **nvarchar(128)**。  
  
## <a name="return-types"></a>傳回型別  
 **varbinary**，大小上限為 8,000 位元組。  
  
## <a name="remarks"></a>備註  
 需要非對稱金鑰的 CONTROL 權限。  
  
## <a name="examples"></a>範例  
 下列範例會建立資料表 `SignedData04`，並在其中儲存純文字和其簽章。 接著會在利用非對稱金鑰 `PrimeKey` 簽署的資料表中插入記錄 (會先利用密碼 `'pGFD4bb925DGvbd2439587y'` 將金鑰解密)。  
  
```sql  
-- Create a table in which to store the data  
CREATE TABLE [SignedData04](Description NVARCHAR(max), Data NVARCHAR(max), DataSignature VARBINARY(8000));  
GO  
-- Store data together with its signature  
DECLARE @clear_text_data NVARCHAR(max);  
set @clear_text_data = N'Important numbers 2, 3, 5, 7, 11, 13, 17,   
      19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79,  
      83, 89, 97';  
INSERT INTO [SignedData04]   
    VALUES( N'data encrypted by asymmetric key ''PrimeKey''',  
    @clear_text_data, SignByAsymKey( AsymKey_Id( 'PrimeKey' ),  
    @clear_text_data, N'pGFD4bb925DGvbd2439587y' ));  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [ASYMKEY_ID &#40;Transact-SQL&#41;](../../t-sql/functions/asymkey-id-transact-sql.md)   
 [VERIFYSIGNEDBYASYMKEY &#40;Transact-SQL&#41;](../../t-sql/functions/verifysignedbyasymkey-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [DROP ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)   
 [加密階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
