---
title: sp_helplanguage & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helplanguage
- sp_helplanguage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplanguage
- default languages
ms.assetid: 8c4651a5-7dbc-49c5-8691-dc72103c2dfa
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d46e178fc1872a84bb573f16629803c59f2fb6c6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122505"
---
# <a name="sphelplanguage-transact-sql"></a>sp_helplanguage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  報告特定替代語言或 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中所有語言的相關資訊。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helplanguage [ [ @language = ] 'language' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @language = ] 'language'` 是要顯示資訊的替代語言名稱。 *語言*已**sysname**，預設值是 NULL。 如果*語言*已指定，會傳回指定語言的相關資訊。 如果未指定語言，在 所有語言的相關資訊**sys.syslanguages**相容性檢視會傳回。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**langid**|**smallint**|語言識別碼。|  
|**dateformat**|**nchar(3)**|日期的格式。|  
|**datefirst**|**tinyint**|一週的第一天：1 代表星期一，2 代表星期二，以此類推至 7 代表星期日。|  
|**upgrade**|**int**|這個語言最後升級的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。|  
|**name**|**sysname**|語言名稱。|  
|**alias**|**sysname**|語言的替代名稱。|  
|**幾個月**|**nvarchar(372)**|月份名稱。|  
|**shortmonths**|**nvarchar(132)**|簡短月份名稱。|  
|**天**|**nvarchar(217)**|日期名稱。|  
|**lcid**|**int**|語言的 Windows 地區設定識別碼。|  
|**msglangid**|**smallint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 訊息群組識別碼。|  
  
## <a name="permissions"></a>Permissions  
 需要 **public** 角色的成員資格。  
  
## <a name="examples"></a>範例  
  
### <a name="a-returning-information-about-a-single-language"></a>A. 傳回單一語言的相關資訊  
 下列範例會顯示替代語言 `French` 的相關資訊。  
  
```  
sp_helplanguage French;  
```  
  
### <a name="b-returning-information-about-all-languages"></a>B. 傳回所有語言的相關資訊  
 下列範例會顯示所有已安裝之替代語言的相關資訊。  
  
```  
sp_helplanguage;  
```  
  
## <a name="see-also"></a>另請參閱  
 [Database Engine 預存程序&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [@@LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/functions/language-transact-sql.md)   
 [SET LANGUAGE &#40;Transact-SQL&#41;](../../t-sql/statements/set-language-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
