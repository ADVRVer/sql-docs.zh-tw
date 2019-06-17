---
title: SET FIPS_FLAGGER (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FIPS_FLAGGER
- SET_FIPS_FLAGGER_TSQL
- FIPS_FLAGGER_TSQL
- SET FIPS_FLAGGER
dev_langs:
- TSQL
helpviewer_keywords:
- SET FIPS_FLAGGER statement
- FIPS 127-2 standard
- FIPS_FLAGGER option
ms.assetid: e82f6bee-6cf6-4061-be22-9ad2e8e9d3d6
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 4dd2c65a885e7619c9ddcd92ed7849981453e838
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "62939726"
---
# <a name="set-fipsflagger-transact-sql"></a>SET FIPS_FLAGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  指定 FIPS 127-2 標準的符合檢查。 這是以 ISO 標準為基礎。 如需 SQL Server FIPS 合規性資訊，請參閱[如何在 FIPS 140-2 合規模式中使用 SQL Server 2016](https://support.microsoft.com/help/4014354/how-to-use-sql-server-2016-in-fips-140-2-compliant-mode)。 
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
SET FIPS_FLAGGER ( 'level' |  OFF )  
```  
  
## <a name="arguments"></a>引數  
 **'** *level* **'**  
 這是用來檢查所有資料庫作業的 FIPS 127-2 標準之符合層級。 如果資料庫作業與所選的 ISO 標準層級衝突，[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會產生一則警告。  
  
 *level* 必須是下列值之一。  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|ENTRY|符合 ISO 入門層級的標準檢查。|  
|FULL|完全符合 ISO 的標準檢查。|  
|INTERMEDIATE|符合 ISO 中等層級的標準檢查。|  
|OFF|無標準檢查。|  
  
## <a name="remarks"></a>Remarks  
 `SET FIPS_FLAGGER` 的設定是在剖析階段進行設定，而不是在執行階段進行設定。 在剖析階段設定表示：如果批次或預存程序中有 SET 陳述式，則不論程式碼是否實際執行到這一點，它都會生效；且 `SET` 陳述式會在任何陳述式執行之前生效。 例如，即使 `SET` 陳述式是在永遠不會執行到的 `IF...ELSE` 陳述式區塊中，`SET` 陳述式仍會生效，因為系統會剖析 `IF...ELSE` 陳述式區塊。  
  
 如果 `SET FIPS_FLAGGER` 設在預存程序中，從預存程序傳回控制權之後，會還原 `SET FIPS_FLAGGER` 的值。 因此，動態 SQL 中所指定的 `SET FIPS_FLAGGER` 陳述式完全不會影響在動態 SQL 陳述式之後的任何陳述式。  
  
## <a name="permissions"></a>權限  
 需要 **public** 角色的成員資格。  
  
## <a name="see-also"></a>另請參閱  
 [SET 陳述式 &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
