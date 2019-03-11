---
title: ENCRYPTBYCERT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ENCRYPTBYCERT
- ENCRYPTBYCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], encryption
- encryption [SQL Server], certificates
- ENCRYPTBYCERT function
ms.assetid: ab66441f-e2d2-4e3a-bcae-bcc09e12f3c1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 79530fff04d278d9dbc8e1ad1454bc4dca4c885c
ms.sourcegitcommit: b3d84abfa4e2922951430772c9f86dce450e4ed1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56662942"
---
# <a name="encryptbycert-transact-sql"></a>ENCRYPTBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

以憑證的公開金鑰加密資料。  
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
EncryptByCert ( certificate_ID , { 'cleartext' | @cleartext } )  
```  
  
## <a name="arguments"></a>引數  
_certificate\_ID_  
資料庫中的憑證識別碼。 **int**.  
  
_cleartext_  
將以憑證加密的資料字串。  
  
**@cleartext**  
下列其中一個類型的變數，包含將利用憑證公開金鑰加密的資料：

* **nvarchar** 
* **char**
* **varchar**
* **binary** 
* **varbinary**
* **nchar**
  
## <a name="return-types"></a>傳回類型  
**varbinary**，大小上限為 8,000 位元組。  
  
## <a name="remarks"></a>Remarks  
這個函式是利用憑證的公開金鑰為資料加密。 加密文字只能利用對應的私密金鑰加以解密。 與使用對稱金鑰進行加密和解密相比，這些非對稱轉換的成本相當高。 因此，若是使用大型資料集，不建議您使用非對稱式加密。
  
## <a name="examples"></a>範例  
這個範例利用稱為 `@cleartext` 的憑證加密儲存在 `JanainaCert02` 中的純文字。 加密的資料會插入 `ProtectedData04` 資料表中。  
  
```  
INSERT INTO [AdventureWorks2012].[ProtectedData04]   
    VALUES ( N'Data encrypted by certificate ''Shipping04''',  
    EncryptByCert(Cert_ID('JanainaCert02'), @cleartext) );  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
[DECRYPTBYCERT &#40;Transact-SQL&#41;](../../t-sql/functions/decryptbycert-transact-sql.md)   
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
[ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
[DROP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
[BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
[加密階層](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
