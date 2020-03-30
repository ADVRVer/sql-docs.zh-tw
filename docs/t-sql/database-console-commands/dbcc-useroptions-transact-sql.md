---
title: DBCC USEROPTIONS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC USEROPTIONS
- DBCC_USEROPTIONS_TSQL
- USEROPTIONS_TSQL
- USEROPTIONS
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC USEROPTIONS statement
- active SET options
- SET statement, active SET options
ms.assetid: 565ab112-7af1-4c18-a579-07cdb332f539
author: pmasl
ms.author: umajay
ms.openlocfilehash: dc8f12ae745acd0410fb309dc4c3dc9b65e7a382
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "68040453"
---
# <a name="dbcc-useroptions-transact-sql"></a>DBCC USEROPTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

傳回目前連接在使用中 (已設定) 的 SET 選項。
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>語法  
  
```sql
DBCC USEROPTIONS  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>引數  
NO_INFOMSGS  
抑制所有嚴重性層級在 0 到 10 的參考用訊息。
  
## <a name="result-sets"></a>結果集  
DBCC USEROPTIONS 會針對 SET 選項的名稱傳回一個資料行，以及針對該選項的值傳回一個資料行 (值和項目可能不同)：

```sql

Set Option                   Value`  
---------------------------- ---------------------------`  
textsize                     64512 
language                     us_english 
dateformat                   mdy  
datefirst                    7 
lock_timeout                 -1 
quoted_identifier            SET 
arithabort                   SET 
ansi_null_dflt_on            SET 
ansi_warnings                SET 
ansi_padding                 SET 
ansi_nulls                   SET 
concat_null_yields_null      SET 
isolation level              read committed  
(13 row(s) affected) 
DBCC execution completed. If DBCC printed error messages, contact your system administrator.
 ```  
  
## <a name="remarks"></a>備註  
當 READ_COMMITTED_SNAPSHOT 資料庫選項設為 ON 且交易隔離等級設為 'read committed' 時，DBCC USEROPTIONS 會報告 'read committed snapshot' 隔離等級。 實際的隔離等級為讀取認可。
  
## <a name="permissions"></a>權限  
需要 **public** 角色的成員資格。
  
## <a name="examples"></a>範例  
下列範例會針對目前連接傳回使用中的 SET 選項。
  
```sql  
DBCC USEROPTIONS;  
```  
  
## <a name="see-also"></a>另請參閱  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[SET 陳述式 &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
[SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)
  
  
