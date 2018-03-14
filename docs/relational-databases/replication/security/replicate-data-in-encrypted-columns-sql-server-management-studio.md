---
title: "複寫加密資料行中的資料 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption [SQL Server], replicating data
- encryption [SQL Server replication]
- publishing [SQL Server replication], encrypted columns
ms.assetid: d1f8f586-e5a3-4a71-9391-11198d42bfa3
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ec0ce41a59250557e189dc7414969b15c4e0c31b
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="replicate-data-in-encrypted-columns-sql-server-management-studio"></a>複寫加密資料行中的資料 (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  複寫讓您可以發行加密的資料行資料。 若要在訂閱者端解密及使用此資料，於發行者端用來加密資料的金鑰也必須存在訂閱者端。 複寫並不會提供用於傳輸加密金鑰的安全機制。 您必須以手動方式於訂閱者端重新建立加密金鑰。 本主題示範如何於發行者端加密資料行，並確定訂閱者端可使用加密金鑰。  
  
 基本步驟如下：  
  
1.  於發行者端建立對稱金鑰。  
  
2.  使用對稱金鑰加密資料行資料。  
  
3.  發行包含加密資料行的資料表。  
  
4.  訂閱發行集。  
  
5.  初始化訂閱。  
  
6.  使用與步驟 1 相同的 ALGORITHM、KEY_SOURCE 和 IDENTITY_VALUE 值，於訂閱者端重新建立對稱金鑰。  
  
7.  存取加密的資料行資料。  
  
> [!NOTE]  
>  您應該使用對稱金鑰來加密資料行資料。 在發行者端和訂閱者端可以用不同方式維護對稱金鑰本身的安全性。  
  
### <a name="to-create-and-replicate-encrypted-column-data"></a>建立和複寫加密的資料行資料  
  
1.  於發行者端，執行 [CREATE SYMMETRIC KEY](../../../t-sql/statements/create-symmetric-key-transact-sql.md)。  
  
    > [!IMPORTANT]  
    >  KEY_SOURCE 的值是重要的資料，可用於重新建立對稱金鑰和解密資料， 所以務必安全地存放和傳輸 KEY_SOURCE。  
  
2.  執行 [OPEN SYMMETRIC KEY](../../../t-sql/statements/open-symmetric-key-transact-sql.md) 開啟新的金鑰。  
  
3.  使用 [EncryptByKey](../../../t-sql/functions/encryptbykey-transact-sql.md) 函數於發行者端加密資料行資料。  
  
4.  執行 [CLOSE SYMMETRIC KEY](../../../t-sql/statements/close-symmetric-key-transact-sql.md) 關閉金鑰。  
  
5.  發行包含加密資料行的資料表。 如需詳細資訊，請參閱 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)。  
  
6.  訂閱發行集。 如需詳細資訊，請參閱[建立提取訂閱](../../../relational-databases/replication/create-a-pull-subscription.md)或[建立發送訂閱](../../../relational-databases/replication/create-a-push-subscription.md)。  
  
7.  初始化訂閱。 如需詳細資訊，請參閱 [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)。  
  
8.  在訂閱者端，使用與步驟 1 相同的 ALGORITHM、KEY_SOURCE 和 IDENTITY_VALUE 值來執行 [CREATE SYMMETRIC KEY](../../../t-sql/statements/create-symmetric-key-transact-sql.md) 。 您可以針對 ENCRYPTION BY 指定不同的值。  
  
    > [!IMPORTANT]  
    >  KEY_SOURCE 的值是重要的資料，可用於重新建立對稱金鑰和解密資料， 所以務必安全地存放和傳輸 KEY_SOURCE。  
  
9. 執行 [OPEN SYMMETRIC KEY](../../../t-sql/statements/open-symmetric-key-transact-sql.md) 開啟新的金鑰。  
  
10. 使用 [DecryptByKey](../../../t-sql/functions/decryptbykey-transact-sql.md) 函數於訂閱者端解密複寫的資料。  
  
11. 執行 [CLOSE SYMMETRIC KEY](../../../t-sql/statements/close-symmetric-key-transact-sql.md) 關閉金鑰。  
  
## <a name="example"></a>範例  
 此範例會建立對稱金鑰、用來協助維護對稱金鑰安全性的憑證和主要金鑰。 這些金鑰建立在複寫資料庫中， 然後用來在 `SalesOrderHeader` 資料表中建立加密資料行 (EncryptedCreditCardApprovalCode)。 這個資料行會發行在 AdvWorksSalesOrdersMerge 發行集中，取代未加密的 CreditCardApprovalCode 資料行。 可能的話，會在執行階段提示使用者輸入安全性認證。 如果您必須將認證儲存在指令碼檔案中，則必須維護這個檔案的安全性，使他人無法在未獲授權的情況下擅自存取。  
  
 [!code-sql[HowTo#sp_PublishEncryptedColumn](../../../relational-databases/replication/codesnippet/tsql/replicate-data-in-encryp_1.sql)]  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/replicate-data-in-encryp_2.sql)]  
  
## <a name="example"></a>範例  
 本範例會使用與第一個範例相同的 ALGORITHM、KEY_SOURCE 和 IDENTITY_VALUE 值，在訂閱資料庫中重新建立相同的對稱金鑰。 本範例假設您已經初始化訂閱 AdvWorksSalesOrdersMerge 發行集，以複寫加密資料行。 可能的話，會在執行階段提示使用者輸入安全性認證。 如果您必須將認證儲存在指令碼檔案中，則必須維護這個檔案在儲存和傳輸時的安全性，使他人無法在未獲授權的情況下擅自存取。  
  
 [!code-sql[HowTo#sp_SubscriberEncryptedColumn](../../../relational-databases/replication/codesnippet/tsql/replicate-data-in-encryp_3.sql)]  
  
## <a name="see-also"></a>另請參閱  
 [安全性概觀 &#40;複寫&#41;](../../../relational-databases/replication/security/security-overview-replication.md)   
 [在兩部伺服器上建立相同的對稱金鑰](../../../relational-databases/security/encryption/create-identical-symmetric-keys-on-two-servers.md)  
  
  
