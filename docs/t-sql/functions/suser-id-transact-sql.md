---
title: SUSER_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SUSER_ID_TSQL
- SUSER_ID
dev_langs:
- TSQL
helpviewer_keywords:
- users [SQL Server], IDs
- logins [SQL Server], IDs
- SUSER_ID function
- IDs [SQL Server], logins
- identification numbers [SQL Server], logins
- user IDs [SQL Server]
ms.assetid: 348911ab-b0b6-4867-aee7-e6f42e053a4a
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a7eb46bf624a90ac5498dd69ed7ec821ce652a14
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="suserid-transact-sql"></a>SUSER_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  傳回使用者的登入識別碼。  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]
  
> [!NOTE]  
>  從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 開始，SUSER_ID 會傳回在 **sys.server_principals** 目錄檢視中列為 **principal_id** 的值。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
SUSER_ID ( [ 'login' ] )   
```  
  
## <a name="arguments"></a>引數  
 **'** *login* **'**  
 這是使用者的登入名稱。 *login* 為 **nchar**。 若將 *login* 指定為 **char**，則 *login* 便會隱含轉換成 **nchar**。 *login* 可以是有權連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入或是 Windows 使用者或群組。 如果未指定 *login*，便會傳回目前使用者的登入識別碼。 如果參數包含 NULL 一詞，就會傳回 NULL。  
  
## <a name="return-types"></a>傳回類型  
 **int**  
  
## <a name="remarks"></a>Remarks  
 SUSER_ID 只會針對在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 內明確規定的登入來傳回識別碼。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 內，這個識別碼是用來追蹤擁有權和權限。 這個識別碼不等於 SUSER_SID 傳回之登入的 SID。 如果 *login* 是一項 SQL Server 登入，則 SID 會對應至 GUID。 如果 *login* 是 Windows 登入或 Windows 群組，則 SID 會對應至 Windows 安全性識別碼。  
  
 SUSER_SID 只會傳回在 **syslogins** 系統資料表中有項目之登入的 SUID。  
  
 系統函數可用在選取清單、WHERE 子句及任何允許使用運算式的位置中，且後面一律必須接著括號，即使未指定任何參數也一樣。  
  
## <a name="examples"></a>範例  
 下列範例會傳回 `sa` 登入的登入識別碼。  
  
```  
SELECT SUSER_ID('sa');  
```  
  
## <a name="see-also"></a>另請參閱  
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [SUSER_SID &#40;Transact-SQL&#41;](../../t-sql/functions/suser-sid-transact-sql.md)   
 [系統函式 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  
