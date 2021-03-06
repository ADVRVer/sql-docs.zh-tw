---
description: sp_replmonitorhelppublisher (Transact-SQL)
title: sp_replmonitorhelppublisher (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelppublisher_TSQL
- sp_replmonitorhelppublisher
helpviewer_keywords:
- sp_replmonitorhelppublisher
ms.assetid: 171501fe-4b74-4647-96c3-7691c777e01b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 3bb6c758089b6089dfeb6b7a472a496931f6c929
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543115"
---
# <a name="sp_replmonitorhelppublisher-transact-sql"></a>sp_replmonitorhelppublisher (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  傳回散發者所關聯的一或多個發行者目前的狀態資訊。 這個預存程序用來監視複寫，執行於散發資料庫的散發者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_replmonitorhelppublisher [ [ @publisher = ] 'publisher' ]  
    [ , [ @refreshpolicy = ] refreshpolicy ]  
```  
  
## <a name="arguments"></a>引數  
`[ @publisher = ] 'publisher'` 這是正在監視之狀態的發行者名稱。 *publisher* 是 **sysname**，預設值是 Null。 如果是 NULL，就會傳回所有使用散發者之發行者的資訊。  
  
`[ @refreshpolicy = ] refreshpolicy` 僅供內部使用。  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|這是發行者的名稱。|  
|**distribution_db**|**sysname**|這是給定發行者所用之散發資料庫的名稱。|  
|**status**|**int**|這個發行者的發行集所有相關聯之複寫代理程式的最大值狀態，它可能是下列值之一。<br /><br /> **1** = 已啟動<br /><br /> **2** = 成功<br /><br /> **3** = 進行中<br /><br /> **4** = 閒置<br /><br /> **5** = 重試<br /><br /> **6** = 失敗|  
|**warning**|**int**|屬於這個發行者的發行集之訂閱所產生的臨界值警告最大值，它可能是一個或多個這些值的邏輯 OR 結果。<br /><br /> **1** = 到期-交易式發行集的訂閱未在保留期限閾值內進行同步處理。<br /><br /> **2** = 延遲-將交易式發行者的資料複寫到訂閱者所花費的時間超過閾值（以秒為單位）。<br /><br /> **4** = mergeexpiration-合併式發行集的訂閱未在保留期限閾值內進行同步處理。<br /><br /> **8** = mergefastrunduration 利用-完成合併訂閱的同步處理所花費的時間超過閾值（以秒為單位），透過快速網路連接。<br /><br /> **16** = mergeslowrunduration 利用-完成合併訂閱的同步處理所花費的時間超過閾值（以秒為單位），而不是透過慢速或撥號網路連接。<br /><br /> **32** = mergefastrunspeed 利用-在同步處理合併訂閱期間，資料列的傳遞速率無法維持閾值速率（以每秒資料列數為單位），透過快速網路連接。<br /><br /> **64** = mergeslowrunspeed-在同步處理合併訂閱期間，資料列的傳遞速率無法維持閾值速率（以每秒資料列數為單位），透過慢速或撥號網路連接。|  
|**publicationcount**|**int**|這是屬於發行者的發行集數目。|  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或 **1** (失敗)   
  
## <a name="remarks"></a>備註  
 **sp_replmonitorhelppublisher** 用於所有類型的複寫。  
  
## <a name="permissions"></a>權限  
 只有散發者端之 **系統管理員（sysadmin** ）固定伺服器角色的成員，或是散發資料庫中 **db_owner** 或 **replmonitor** 固定資料庫角色的成員，才能夠執行 **sp_replmonitorhelppublisher**。  
  
## <a name="see-also"></a>另請參閱  
 [以程式設計方式監視複寫](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
