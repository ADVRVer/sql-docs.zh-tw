---
title: sp_enclave_send_keys （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 10/19/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_enclave_send_keys
- sp_enclave_send_keys_TSQL
- sys.sp_enclave_send_keys
- sys.sp_enclave_send_keys_TSQL
helpviewer_keywords:
- sp_enclave_send_keys
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: ca6e7485e85665f06c2410438b902fa0647418ae
ms.sourcegitcommit: 312b961cfe3a540d8f304962909cd93d0a9c330b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73593755"
---
# <a name="sp_enclave_send_keys-transact-sql"></a>sp_enclave_send_keys （Transact-sql）
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

將資料庫中定義的資料行加密金鑰傳送至搭配[安全記憶體保護區 Always Encrypted](../security/encryption/always-encrypted-enclaves.md)使用的伺服器端安全記憶體保護區。

`sp_enclave_send_keys` 只會傳送已啟用記憶體保護區的索引鍵，並將使用隨機加密的資料行加密並擁有索引。 針對一般使用者查詢，用戶端驅動程式會提供記憶體保護區，其中包含查詢中計算所需的索引鍵。 `sp_enclave_send_keys` 會傳送資料庫中定義的所有資料行加密金鑰，並用於索引加密的資料行。 

`sp_enclave_send_keys` 提供簡單的方法，將金鑰傳送至記憶體保護區，並在資料行加密金鑰快取中填入後續的索引作業。 使用 `sp_enclave_send_keys` 啟用：
- DBA 在加密資料庫資料行上重建或更改索引或統計資料（如果 DBA 無法存取資料行主要金鑰）。 請參閱使用快取的資料[行加密金鑰叫用索引作業](../security/encryption/always-encrypted-enclaves-create-use-indexes.md#invoke-indexing-operations-using-cached-column-encryption-keys)。
- [!INCLUDE [ssnoversion-md](../../includes/ssnoversion-md.md)]，以完成已加密資料行上索引的復原。 請參閱[資料庫](../security/encryption/always-encrypted-enclaves.md#database-recovery)復原。
- 使用 .NET Framework Data Provider SQL Server 的應用程式，將資料大量載入加密的資料行。

若要成功叫用 `sp_enclave_send_keys`，您必須使用針對資料庫連接啟用的 Always Encrypted 和記憶體保護區計算來連接到資料庫。 您也必須能夠存取資料行主要金鑰，保護您要傳送的資料行加密金鑰，而且您需要存取資料庫中 Always Encrypted 金鑰中繼資料的許可權。 

## <a name="syntax"></a>語法  
  
```
sp_enclave_send_keys
[ ;]  
```

## <a name="arguments"></a>引數

這個預存程式沒有任何引數。

## <a name="return-value"></a>傳回值

這個預存程式沒有傳回值。
  
## <a name="result-sets"></a>結果集

這個預存程式沒有任何結果集。
  
## <a name="permissions"></a>Permissions

 需要資料庫中的 `VIEW ANY COLUMN ENCRYPTION KEY DEFINITION` 和 `VIEW ANY COLUMN MASTER KEY DEFINITION` 許可權。  
  
## <a name="examples"></a>範例  
  
```sql
EXEC sp_enclave_send_keys;  
```

## <a name="see-also"></a>另請參閱
- [具有安全記憶體保護區的 Always Encrypted](../security/encryption/always-encrypted-enclaves.md) 
 
- [使用具有安全記憶體保護區的 Always Encrypted，在資料行上建立及使用索引](../security/encryption/always-encrypted-enclaves-create-use-indexes.md)

- [教學課程：使用隨機化加密在啟用記憶體保護區的資料行上建立及使用索引](../security/tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md)
