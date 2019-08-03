---
title: sp_browsesnapshotfolder (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_browsesnapshotfolder
- sp_browsesnapshotfolder_TSQL
helpviewer_keywords:
- sp_browsesnapshotfolder
ms.assetid: 0872edf2-4038-4bc1-a68d-05ebfad434d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: dcc7c4031253f83df49b45feae17449814af3fc3
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768984"
---
# <a name="spbrowsesnapshotfolder-transact-sql"></a>sp_browsesnapshotfolder (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  傳回針對發行集而產生之最新快照集的完整路徑。 這個預存程序執行於發行集資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_browsesnapshotfolder [@publication= ] 'publication'  
    { [ , [ @subscriber = ] 'subscriber' ]  
 [ , [ @subscriber_db = ] 'subscriber_db' ] }  
```  
  
## <a name="arguments"></a>引數  
`[ @publication = ] 'publication'`這是包含發行項的發行集名稱。 *發行*集是**sysname**, 沒有預設值。  
  
`[ @subscriber = ] 'subscriber'`這是訂閱者的名稱。 *訂閱者*是**sysname**, 預設值是 Null。  
  
`[ @subscriber_db = ] 'subscriber_db'`這是訂閱資料庫的名稱。 *subscriber_db*是**sysname**, 預設值是 Null。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或**1** (失敗)  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**snapshot_folder**|**nvarchar(512)**|快照集目錄的完整路徑。|  
  
## <a name="remarks"></a>備註  
 **sp_browsesnapshotfolder**用於快照式複寫和異動複寫中。  
  
 如果 [*訂閱者*] 和 [ *subscriber_db* ] 欄位保留 Null, 則預存程式會傳回它可以為發行集找到的最新快照集的快照集資料夾。 如果已指定*訂閱者*和*subscriber_db*欄位, 則預存程式會傳回指定之訂閱的快照集資料夾。 如果尚未產生發行集的快照集，就會傳回空結果集。  
  
 如果將發行集設定成同時在發行者工作目錄和發行者快照集資料夾中產生快照集檔案，結果集會包含兩個資料列。 第一個資料列包含發行集快照集資料夾，第二個資料列包含發行者工作目錄。 **sp_browsesnapshotfolder**適用于判斷產生快照集檔案的目錄。  
  
## <a name="permissions"></a>Permissions  
 只有**系統管理員 (sysadmin** ) 固定伺服器角色或**db_owner**固定資料庫角色的成員, 才能夠執行**sp_browsesnapshotfolder**。  
  
## <a name="see-also"></a>另請參閱  
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
