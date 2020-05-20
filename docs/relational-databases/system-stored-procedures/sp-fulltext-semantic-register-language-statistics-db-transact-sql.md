---
title: sp_fulltext_semantic_register_language_statistics_db （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_semantic_register_language_statistics_db
- sp_fulltext_semantic_register_language_statistics_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_semantic_register_language_statistics_db
ms.assetid: bef1b104-5a44-4327-9ae4-45eae3000f7e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 263ea7b2bb0da7822554bbdcad934ef20ec54d3b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830031"
---
# <a name="sp_fulltext_semantic_register_language_statistics_db-transact-sql"></a>sp_fulltext_semantic_register_language_statistics_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在目前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中註冊已預先擴展的語義語言統計資料庫。  
  
 只有在已附加這個語言統計資料庫並使用這個預存程序註冊它，才能起始語義擷取。 在每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上只需要執行這項工作一次。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db  
    [ @dbname = ] 'database_name';  
GO  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>參量  
 [ @dbname =] '*database_name*'  
 這是要在目前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中註冊的語義語言統計資料庫名稱。 資料庫必須已附加。 *database_name*是**sysname**，而且不可以是 Null。  
  
## <a name="return-code-value"></a>傳回碼值  
 **0** （成功）或**1** （失敗）  
  
## <a name="result-set"></a>結果集  
 無。  
  
## <a name="general-remarks"></a>一般備註  
 語義語言統計資料庫包含文字內容語意處理所需的語言相關統計資料。  
  
 **sp_fulltext_semantic_register_language_statistics_db**會執行下列步驟：  
  
1.  檢查 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體是否為支援語意處理的版本。  
  
2.  檢查 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體是否未定義語義語言統計資料庫。  
  
3.  檢查資料庫是否為有效的語義語言統計資料庫。  
  
4.  將語義語言統計資料庫的權限設為限制使用者存取資料庫。  
  
5.  在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中插入定義語義語言統計資料庫名稱的中繼資料。  
  
6.  插入中繼資料，其定義已安裝之語義語言統計資料庫與內部語言模型資料表之間的對應。  
  
7.  檢查以確認資料庫備妥可供使用。  
  
 如需詳細資訊，請參閱 [安裝及設定語意搜尋](../../relational-databases/search/install-and-configure-semantic-search.md)。  
  
## <a name="metadata"></a>中繼資料  
 如需有關在實例上安裝之語意語言統計資料資料庫的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請查詢目錄檢視[sys.databases Fulltext_semantic_language_statistics_database &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md)。  
  
## <a name="security"></a>安全性  
  
### <a name="permissions"></a>權限  
 需要 CONTROL SERVER 權限。  
  
## <a name="examples"></a>範例  
 下列範例顯示如何藉由呼叫**sp_fulltext_semantic_register_language_statistics_db**來註冊語意語言統計資料資料庫。  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = 'semanticsDb';  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [安裝及設定語意搜尋](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
