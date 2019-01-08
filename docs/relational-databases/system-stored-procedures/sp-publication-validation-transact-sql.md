---
title: sp_publication_validation & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_publication_validation
- sp_publication_validation_TSQL
helpviewer_keywords:
- sp_publication_validation
ms.assetid: 06be2363-00c0-4936-97c1-7347f294a936
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8612b3713113435461ca59845710b9f7284f1a78
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591402"
---
# <a name="sppublicationvalidation-transact-sql"></a>sp_publication_validation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  針對指定發行集中的每個發行項來初始化發行項驗證要求。 這個預存程序執行於發行集資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_publication_validation [ @publication = ] 'publication'  
    [ , [ @rowcount_only = ] type_of_check_requested ]  
    [ , [ @full_or_fast = ] full_or_fast ]  
    [ , [ @shutdown_agent = ] shutdown_agent ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引數  
 [**@publication=**] **'**_發行集 '_  
 這是發行集的名稱。 *發行集*已**sysname**，沒有預設值。  
  
 [**@rowcount_only=**] *rowcount_only*  
 這是指是否只傳回資料表的資料列數。 *rowcount_only*已**smallint**而且可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**0**|執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 相容總和檢查碼。<br /><br /> 注意：當水平篩選發行項時，會執行資料列計數作業，而不是總和檢查碼作業。|  
|**1** (預設值)|只執行資料列計數檢查。|  
|**2**|執行資料列計數及二進位總和檢查碼。<br /><br /> 注意：如果是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 版訂閱者，就只會執行資料列計數驗證。|  
  
 [**@full_or_fast=**] *full_or_fast*  
 這是用於計算資料列計數的方法。 *full_or_fast*已**tinyint**而且可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**0**|利用 COUNT(*) 執行完整計數。|  
|**1**|快速從計數**sysindexes.rows**。 計算資料列[sys.sysindexes](../../relational-databases/system-compatibility-views/sys-sysindexes-transact-sql.md)比計算實際資料表中的資料列快得多。 不過，因為[sys.sysindexes](../../relational-databases/system-compatibility-views/sys-sysindexes-transact-sql.md)是以延遲的方式更新，資料列計數可能不正確。|  
|**2** (預設值)|先嘗試快速方法來執行條件式快速計數。 如果快速方法有不同結果，便轉換成完整方法。 如果*expected_rowcount*是 NULL，且預存程序正在使用此選項，以取得此值，完整 COUNT(*) 一律會使用。|  
  
 [  **@shutdown_agent=**] *shutdown_agent*  
 這是指在驗證完成時，是否應該立即關閉散發代理程式。 *shutdown_agent*已**位元**，預設值是**0**。 如果**0**，複寫代理程式不會關機。 如果**1**，複寫代理程式會在驗證最後一個發行項之後關閉。  
  
 [ **@publisher** =] **'**_發行者_**'**  
 指定非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]發行者。 *發行者*已**sysname**，預設值是 NULL。  
  
> [!NOTE]  
>  *發行者*應該不在要求上進行驗證時才使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]發行者。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_publication_validation**用於異動複寫中。  
  
 **sp_publication_validation**可在已啟用發行集的相關發行項之後的任何時間加以呼叫。 您可以手動執行這個程序 (一次)，也可以在定期排程驗證資料的作業中執行這個程序。  
  
 如果您的應用程式有立即更新訂閱者， **sp_publication_validation**可能偵測到偽造錯誤。 **sp_publication_validation**先計算的資料列計數或總和檢查碼在 「 發行者 」，然後在 「 訂閱者 」。 由於在發行者端完成資料列計數或總和檢查碼之後，在訂閱者端完成資料列計數或總和檢查碼之前，立即更新觸發程序可能會將訂閱者的更新傳播給發行者，因此，這些值可能會有所不同。 若要確定在驗證發行集時，並不會變更在訂閱者端和發行者端的值，請在驗證期間，停止在發行者端的 Microsoft 分散式交易協調器 (MS DTC) 服務。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色或**db_owner**固定的資料庫角色可以執行**sp_publication_validation**。  
  
## <a name="see-also"></a>另請參閱  
 [驗證訂閱者端的資料](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [sp_article_validation &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)   
 [sp_table_validation &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-table-validation-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
