---
title: ALTER COLUMN ENCRYPTION KEY (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 10/28/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER COLUMN ENCRYPTION
- ALTER_COLUMN_ENCRYPTION_TSQL
- ALTER COLUMN ENCRYPTION KEY
- ALTER_COLUMN_ENCRYPTION_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column encryption key, alter
- ALTER COLUMN ENCRYPTION KEY statement
ms.assetid: c79a220d-e178-4091-a330-c924cc0f0ae0
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a6bc70a7cafdbf69549435b44099b903cfc60327
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="alter-column-encryption-key-transact-sql"></a>ALTER COLUMN ENCRYPTION KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  改變資料庫中資料行的加密金鑰，新增或卸除加密的值。 CEK 最多可以使用兩個值來進行對應資料行主要金鑰的輪替。 當使用 [Always Encrypted &#40;資料庫引擎&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md) 功能加密資料行時，便會使用 CEK。 在新增 CEK 值之前，您必須使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [CREATE MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) 來定義用來加密值的資料行主要金鑰。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
ALTER COLUMN ENCRYPTION KEY key_name   
    [ ADD | DROP ] VALUE   
    (  
        COLUMN_MASTER_KEY = column_master_key_name   
        [, ALGORITHM = 'algorithm_name' , ENCRYPTED_VALUE =  varbinary_literal ]   
    ) [;]  
```  
  
## <a name="arguments"></a>引數  
 *key_name*  
 要變更的資料行加密金鑰。  
  
 *column_master_key_name*  
 指定要用來加密資料行加密金鑰 (CEK) 的資料行主要金鑰 (CMK) 名稱。  
  
 *algorithm_name*  
 用來加密值之加密演算法的名稱。 系統提供者的演算法必須是 **RSA_OAEP**。 在卸除資料行加密金鑰值時，此引數無效。  
  
 *varbinary_literal*  
 使用指定主要加密金鑰加密的 CEK BLOB。 執行個體時提供 SQL Server 登入。 在卸除資料行加密金鑰值時，此引數無效。  
  
> [!WARNING]  
>  絕對不要在此陳述式中傳遞純文字的 CEK 值。 這麼做會影響此功能的優點。  
  
## <a name="remarks"></a>Remarks  
 一般來說，資料行加密金鑰建立時只會使用一個加密值。 當資料行主要金鑰必須輪替 (目前資料行主要金鑰必須更換成新的資料行主要金鑰) 時，您可以新增資料行加密金鑰值，並以新的資料行主要金鑰加密。 這可讓您確保用戶端應用程式可以存取由資料行加密金鑰加密的資料，同時新的資料行主要金鑰亦可供用戶端應用程式使用。 如果用戶端應用程式中的驅動程式已啟用 Always Encrypted，但沒有新的主要金鑰存取權，其可使用以舊資料行主要金鑰加密的資料行加密金鑰值來存取敏感性資料。 Always Encrypted 支援的加密演算法需要使用 256 位元純文字值。 您應該使用金鑰存放區提供者來產生加密的值；金鑰存放區提供者可封裝保存資料行主要金鑰的金鑰存放區。  
  
 使用 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)、[sys.column_encryption_keys  &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md) 和 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md) 來檢視資料行加密金鑰的相關資訊。  
  
## <a name="permissions"></a>Permissions  
 需要資料庫的 **ALTER ANY COLUMN ENCRYPTION KEY** 權限。  
  
## <a name="examples"></a>範例  
  
### <a name="a-adding-a-column-encryption-key-value"></a>A. 新增資料行加密金鑰值  
 下列範例會改變稱為 `MyCEK` 的資料行加密金鑰。  
  
```  
ALTER COLUMN ENCRYPTION KEY MyCEK  
ADD VALUE  
(  
    COLUMN_MASTER_KEY = MyCMK2,   
    ALGORITHM = 'RSA_OAEP',   
    ENCRYPTED_VALUE = 0x016E000001630075007200720065006E00740075007300650072002F006D0079002F0064006500650063006200660034006100340031003000380034006200350033003200360066003200630062006200350030003600380065003900620061003000320030003600610037003800310066001DDA6134C3B73A90D349C8905782DD819B428162CF5B051639BA46EC69A7C8C8F81591A92C395711493B25DCBCCC57836E5B9F17A0713E840721D098F3F8E023ABCDFE2F6D8CC4339FC8F88630ED9EBADA5CA8EEAFA84164C1095B12AE161EABC1DF778C07F07D413AF1ED900F578FC00894BEE705EAC60F4A5090BBE09885D2EFE1C915F7B4C581D9CE3FDAB78ACF4829F85752E9FC985DEB8773889EE4A1945BD554724803A6F5DC0A2CD5EFE001ABED8D61E8449E4FAA9E4DD392DA8D292ECC6EB149E843E395CDE0F98D04940A28C4B05F747149B34A0BAEC04FFF3E304C84AF1FF81225E615B5F94E334378A0A888EF88F4E79F66CB377E3C21964AACB5049C08435FE84EEEF39D20A665C17E04898914A85B3DE23D56575EBC682D154F4F15C37723E04974DB370180A9A579BC84F6BC9B5E7C223E5CBEE721E57EE07EFDCC0A3257BBEBF9ADFFB00DBF7EF682EC1C4C47451438F90B4CF8DA709940F72CFDC91C6EB4E37B4ED7E2385B1FF71B28A1D2669FBEB18EA89F9D391D2FDDEA0ED362E6A591AC64EF4AE31CA8766C259ECB77D01A7F5C36B8418F91C1BEADDD4491C80F0016B66421B4B788C55127135DA2FA625FB7FD195FB40D90A6C67328602ECAF3EC4F5894BFD84A99EB4753BE0D22E0D4DE6A0ADFEDC80EB1B556749B4A8AD00E73B329C95827AB91C0256347E85E3C5FD6726D0E1FE82C925D3DF4A9  
);  
GO  
  
```  
  
### <a name="b-dropping-a-column-encryption-key-value"></a>B. 卸除資料行加密金鑰值  
 下列範例會藉由卸除值來改變稱為 `MyCEK` 的資料行加密金鑰。  
  
```  
ALTER COLUMN ENCRYPTION KEY MyCEK  
DROP VALUE  
(  
    COLUMN_MASTER_KEY = MyCMK  
);  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)   
 [DROP COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
 [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
 [永遠加密 &#40;Database Engine&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 [sys.column_encryption_keys  &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md)   
 [sys.column_encryption_key_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
