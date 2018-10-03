---
title: sp_server_info (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_server_info
- sp_server_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_server_info
ms.assetid: 2dc2c262-3cfa-4a84-8127-3632ba583543
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6ee0f3e2f7858959b04394e4e809df3ab71dcc83
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47846636"
---
# <a name="spserverinfo-transact-sql"></a>sp_server_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、資料庫閘道或基礎資料來源的屬性名稱和相符值的清單。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_server_info [[@attribute_id = ] 'attribute_id']  
```  
  
## <a name="arguments"></a>引數  
 [  **@attribute_id =** ] **'***attribute_id***'**  
 這是屬性的整數識別碼。 *attribute_id*已**int**，預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 None  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**ATTRIBUTE_ID**|**int**|屬性的識別碼。|  
|**ATTRIBUTE_NAME**|**varchar (** 60 **)**|屬性名稱。|  
|**ATTRIBUTE_VALUE**|**varchar (** 255 **)**|屬性目前的設定。|  
  
 下表列出各個屬性。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC 用戶端程式庫目前使用的屬性**1**， **2**， **18**， **22**，以及**500**在連線時間。  
  
|ATTRIBUTE_ID|ATTRIBUTE_NAME 描述|ATTRIBUTE_VALUE|  
|-------------------|---------------------------------|----------------------|  
|**1**|DBMS_NAME|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**2**|DBMS_VER|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] - *x.xx.xxxx*|  
|**10**|OWNER_TERM|owner|  
|**11**|TABLE_TERM|資料表|  
|**12**|MAX_OWNER_NAME_LENGTH|128|  
|**13**|TABLE_LENGTH<br /><br /> 指定資料表名稱的最大字元數目。|128|  
|**14**|MAX_QUAL_LENGTH<br /><br /> 指定資料表限定詞 (三部份資料表名稱的第一部份) 名稱的最大長度。|128|  
|**15**|COLUMN_LENGTH<br /><br /> 指定資料行名稱的最大字元數目。|128|  
|**16**|IDENTIFIER_CASE<br /><br /> 指定資料庫 (系統目錄中的物件案例) 中的使用者自訂名稱 (資料表名稱、資料行名稱、預存程序名稱)。|SENSITIVE|  
|**17**|TX_ISOLATION<br /><br /> 指定伺服器假設的初始交易隔離等級，它對應於 SQL-92 所定義的隔離等級。|2|  
|**18**|COLLATION_SEQ<br /><br /> 指定這部伺服器的字元集排序。|charset=iso_1 sort_order=dictionary_iso charset_num=1 sort_order_num=51|  
|**19**|SAVEPOINT_SUPPORT<br /><br /> 指定基礎 DBMS 是否支援具名儲存點。|Y|  
|**20**|MULTI_RESULT_SETS<br /><br /> 指定基礎資料庫或閘道本身是否支援多個結果集 (可以透過閘道傳送多個陳述式，將多個結果集傳回用戶端)。|Y|  
|**22**|ACCESSIBLE_TABLES<br /><br /> 指定無論**sp_tables**，閘道會傳回唯一的資料表、 檢視和等等，供目前使用者 （也就是擁有資料表的最少選取權限的使用者）。|Y|  
|**100**|USERID_LENGTH<br /><br /> 指定使用者名稱的最大字元數目。|128|  
|**101**|QUALIFIER_TERM<br /><br /> 指定資料表限定詞的 DBMS 供應商詞彙 (三部份名稱的第一部份)。|[資料庫]|  
|**102**|NAMED_TRANSACTIONS<br /><br /> 指定基礎 DBMS 是否支援具名交易。|Y|  
|**103**|SPROC_AS_LANGUAGE<br /><br /> 指定預存程序是否可作為語言事件來執行。|Y|  
|**104**|ACCESSIBLE_SPROC<br /><br /> 指定無論**sp_stored_procedures**，閘道會傳回只預存程序目前的使用者所能執行。|Y|  
|**105**|MAX_INDEX_COLS<br /><br /> 指定 DBMS 索引中的最大資料行數目。|16|  
|**106**|RENAME_TABLE<br /><br /> 指定是否可以重新命名資料表。|Y|  
|**107**|RENAME_COLUMN<br /><br /> 指定是否可以重新命名資料行。|Y|  
|**108**|DROP_COLUMN<br /><br /> 指定是否可以卸除資料行。|Y|  
|**109**|INCREASE_COLUMN_LENGTH<br /><br /> 指定是否可以增加資料行大小。|Y|  
|**110**|DDL_IN_TRANSACTION<br /><br /> 指定 DDL 陳述式是否能出現在交易中。|Y|  
|**111**|DESCENDING_INDEXES<br /><br /> 指定是否支援遞減的索引。|Y|  
|**112**|SP_RENAME<br /><br /> 指定是否能重新命名預存程序。|Y|  
|**113**|REMOTE_SPROC<br /><br /> 指定是否可利用 DB-Library 中的遠端預存程序函數來執行預存程序。|Y|  
|**500**|SYS_SPROC_VERSION<br /><br /> 指定目前實作的目錄預存程序版本。|目前版本號碼|  
  
## <a name="remarks"></a>備註  
 **sp_server_info**會傳回所提供的資訊子集**SQLGetInfo** ODBC 中。  
  
## <a name="permissions"></a>Permissions  
 需要結構描述的 SELECT 權限。  
  
## <a name="see-also"></a>另請參閱  
 [目錄預存程序&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
