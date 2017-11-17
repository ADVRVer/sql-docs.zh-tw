---
title: "ENCRYPTBYPASSPHRASE (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ENCRYPTBYPASSPHRASE
- ENCRYPTBYPASSPHRASE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ENCRYPTBYPASSPHRASE function
- encryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], ENCRYPTBYPASSPHRASE function
ms.assetid: f8dbb9e6-94d6-40d7-8b38-6833a409d597
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ddfbea4ac550f21787eb88db6119c391f2b1b85a
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="encryptbypassphrase-transact-sql"></a>ENCRYPTBYPASSPHRASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  使用 TRIPLE DES 演算法搭配 128 金鑰位元長度，以複雜密碼加密資料。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
EncryptByPassPhrase ( { 'passphrase' | @passphrase }   
    , { 'cleartext' | @cleartext }  
  [ , { add_authenticator | @add_authenticator }  
    , { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>引數  
 *複雜密碼*  
 用於產生對稱金鑰的複雜密碼。  
  
 @passphrase  
 類型的變數**nvarchar**， **char**， **varchar**，**二進位**， **varbinary**，或**nchar**包含要從中產生對稱金鑰的複雜密碼。  
  
 *純文字*  
 要加密的純文字。  
  
 @cleartext  
 類型的變數**nvarchar**， **char**， **varchar**，**二進位**， **varbinary**，或**nchar**包含純文字。 大小上限是 8,000 位元組。  
  
 *add_authenticator*  
 指出驗證器是否要與純文字一起加密。 若要加入驗證器，則為 1。 **int**。  
  
 @add_authenticator  
 指出雜湊是否要與純文字一起加密。  
  
 *驗證器*  
 要衍生驗證器的資料。 **sysname**。  
  
 @authenticator  
 含有要衍生驗證器之資料的變數。  
  
## <a name="return-types"></a>傳回類型  
 **varbinary** ，大小上限為 8,000 個位元組。  
  
## <a name="remarks"></a>備註  
 複雜密碼是指包含空格的密碼。 使用複雜密碼的好處是，記住有意義的片語或句子比記住相較之下冗長的字元字串容易得多。  
  
 這個函數不會檢查密碼複雜性。  
  
## <a name="examples"></a>範例  
 下列範例會更新 `SalesCreditCard` 資料表中的記錄，並使用主索引鍵當做驗證器，加密儲存在資料行 `CardNumber_EncryptedbyPassphrase` 中的信用卡號碼之值。  
  
```  
USE AdventureWorks2012;  
GO  
-- Create a column in which to store the encrypted data.  
ALTER TABLE Sales.CreditCard   
    ADD CardNumber_EncryptedbyPassphrase varbinary(256);   
GO  
-- First get the passphrase from the user.  
DECLARE @PassphraseEnteredByUser nvarchar(128);  
SET @PassphraseEnteredByUser   
    = 'A little learning is a dangerous thing!';  
  
-- Update the record for the user's credit card.  
-- In this case, the record is number 3681.  
UPDATE Sales.CreditCard  
SET CardNumber_EncryptedbyPassphrase = EncryptByPassPhrase(@PassphraseEnteredByUser  
    , CardNumber, 1, CONVERT( varbinary, CreditCardID))  
WHERE CreditCardID = '3681';  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [DECRYPTBYPASSPHRASE &#40;TRANSACT-SQL &#41;](../../t-sql/functions/decryptbypassphrase-transact-sql.md)   
 [加密階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

