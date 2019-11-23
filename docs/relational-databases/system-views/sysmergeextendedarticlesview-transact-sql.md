---
title: sysmergeextendedarticlesview （Transact-sql） |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysmergeextendedarticlesview
- sysmergeextendedarticlesview_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergeextendedarticlesview view
ms.assetid: bd5c8414-5292-41fd-80aa-b55a50ced7e2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 576fe599772454cb0cc8a01bf28c530f5cdfb13b
ms.sourcegitcommit: 710d60e7974e2c4c52aebe36fceb6e2bbd52727c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2019
ms.locfileid: "72278178"
---
# <a name="sysmergeextendedarticlesview-transact-sql"></a>sysmergeextendedarticlesview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sysmergeextendedarticlesview** view 會公開發行項資訊。 這份檢視儲存在發行者端的發行集資料庫以及訂閱者端的訂閱資料庫中。  
  
|資料行名稱|[名稱]|描述|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|發行項的名稱。|  
|**型別**|**tinyint**|指出發行項類型，它可以是下列項目之一：<br /><br /> **10** = 資料表。<br /><br /> **32** = 僅限 Proc 架構。<br /><br /> **64** = 僅 view schema 或 indexed view schema。<br /><br /> **128** = 僅限函數架構。<br /><br /> **160** = 僅限同義字架構。|  
|**objid**|**int**|發行者物件的識別碼。|  
|**sync_objid**|**int**|代表同步處理資料集檢視的識別碼。|  
|**view_type**|**tinyint**|檢視的類型：<br /><br /> **0** = 不是 view;使用所有基底物件。<br /><br /> **1** = 永久視圖。<br /><br /> **2** = 暫時視圖。|  
|**artid**|**ssNoversion**|給定發行項的唯一識別碼。|  
|**description**|**nvarchar(255)**|發行項的簡要描述。|  
|**pre_creation_command**|**tinyint**|當在訂閱資料庫中建立發行項時，所採取的預設動作。<br /><br /> **0** = 無-如果資料表已存在於訂閱者端，則不會採取任何動作。<br /><br /> **1** = Drop-卸載資料表，然後再重新建立。<br /><br /> **2** = 刪除-根據子集篩選中的 WHERE 子句發出刪除。<br /><br /> **3** = 截斷-與2相同，但會刪除頁面而不是資料列。 不過，它不用 WHERE 子句。|  
|**pubid**|**ssNoversion**|目前發行項所屬發行集的識別碼。|  
|**昵稱**|**int**|發行項識別的暱稱對應。|  
|**column_tracking**|**int**|指出是否實作發行項的資料行追蹤。|  
|**status**|**tinyint**|指出發行項的狀態，它可以是下列項目之一：<br /><br /> **1** = 未同步-發行資料表的初始處理腳本會在下一次執行快照集代理程式時執行。<br /><br /> **2** = 主動-已執行發行資料表的初始處理腳本。<br /><br /> **5** = 要加入 New_inactive。<br /><br /> **6** = 要加入 New_active。|  
|**conflict_table**|**sysname**|包含目前發行項的衝突記錄之本機資料表的名稱。 提供這份資料表只供參考，自訂衝突解決常式可以修改或刪除它的內容，管理員也可以直接修改或刪除它的內容。|  
|**creation_script**|**nvarchar(255)**|這個發行項的建立指令碼。|  
|**conflict_script**|**nvarchar(255)**|這個發行項的衝突指令碼。|  
|**article_resolver**|**nvarchar(255)**|這個發行項的自訂資料列層級衝突解析程式。|  
|**ins_conflict_proc**|**sysname**|用來將衝突寫入**conflict_table**的程式。|  
|**insert_proc**|**sysname**|預設衝突解析程式在同步處理期間插入資料列所使用的程序。|  
|**update_proc**|**sysname**|預設衝突解析程式在同步處理期間更新資料列所使用的程序。|  
|**select_proc**|**sysname**|合併代理程式用來實現鎖定以及尋找發行項的資料行和資料列之自動產生預存程序的名稱。|  
|**schema_option**|**binary （8）**|如需*schema_option*的支援值，請[參閱&#40;sp_addmergearticle transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)。|  
|**destination_object**|**sysname**|在訂閱者端建立之資料表的名稱。|  
|**resolver_clsid**|**nvarchar(50)**|自訂衝突解析程式的識別碼。|  
|**subset_filterclause**|**nvarchar(1000)**|這個發行項的篩選子句。|  
|**missing_col_count**|**int**|遺漏的資料行數。|  
|**missing_cols**|**varbinary(128)**|遺漏資料行的點陣圖。|  
|**columns**|**varbinary(128)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**resolver_info**|**nvarchar(255)**|自訂衝突解析程式所需要之其他資訊的儲存體。|  
|**view_sel_proc**|**Nvarchar （290）**|合併代理程式用來初始擴展動態篩選發行集的發行項以及列舉任何篩選發行集中已變更之資料列的預存程序名稱。|  
|**gen_cur**|**int**|發行項基底資料表的本機變更產生數目。|  
|**excluded_cols**|**varbinary(128)**|在傳送給訂閱者的發行項中排除資料行的點陣圖。|  
|**excluded_col_count**|**int**|排除的資料行數。|  
|**vertical_partition**|**int**|指定是否啟用資料表發行項的資料行篩選。 **0**表示沒有垂直篩選，而且會發行所有資料行。|  
|**identity_support**|**int**|指定是否啟用自動識別範圍處理。 **1**表示已啟用識別範圍處理， **0**表示不支援識別範圍。|  
|**destination_owner**|**sysname**|目的地物件的擁有者名稱。|  
|**before_image_objid**|**int**|追蹤資料表物件識別碼。 發行集設定為啟用資料分割變更最佳化時，追蹤資料表會包含某些索引鍵資料行值。|  
|**before_view_objid**|**int**|檢視資料表的物件識別碼。 檢視所在的資料表會追蹤是否刪除或更新了在它之前屬於特定訂閱者的資料列。 只有在使用 *\@keep_partition_changes* = **true**建立發行集時才適用。|  
|**verify_resolver_signature**|**int**|指定在合併式複寫中使用解析程式之前，是否要驗證數位簽章：<br /><br /> **0** = 未驗證簽章。<br /><br /> **1** = 已驗證簽章，以查看它是否來自信任的來源。|  
|**allow_interactive_resolver**|**bit**|指定是否啟用發行項的互動式解析程式。 **1**指定在發行項上使用互動式解析程式。|  
|**fast_multicol_updateproc**|**bit**|指定是否已啟用合併代理程式，以在 UPDATE 陳述式中，將變更套用相同資料列的多個資料行中。<br /><br /> **0** = 針對每個變更的資料行發出個別的更新。<br /><br /> **1** = 在 UPDATE 語句上發出，這會導致在單一語句中對多個資料行進行更新。|  
|**check_permissions**|**int**|合併代理程式將變更套用在發行者時，將驗證之資料表層級權限的點陣圖。 *check_permissions*可以有下列其中一個值：<br /><br /> **0x00** = 不檢查許可權。<br /><br /> **0x10** = 先在發行者端檢查許可權，然後才能上傳在訂閱者端進行的插入。<br /><br /> **0x20** = 先在發行者端檢查許可權，再上傳在訂閱者端進行的更新。<br /><br /> **0x40** = 在訂閱者端進行刪除之前，先檢查發行者的許可權，才能上傳。|  
|**maxversion_at_cleanup**|**int**|清除中繼資料的最高層代 (Generation)。|  
|**processing_order**|**int**|表示合併式發行集中之發行項的處理順序;其中，值為**0**表示發行項未排序，而且會依照從最低到最高值的順序來處理文章。 如果兩個發行項有相同的值，就會同時處理它們。 如需詳細資訊，請參閱[指定合併式複寫屬性](../../relational-databases/replication/merge/specify-merge-replication-properties.md)。|  
|**published_in_tran_pub**|**bit**|指出合併式發行集中的發行項也在交易式發行集中發行。<br /><br /> **0** = 發行項在交易式發行項中未發佈。<br /><br /> **1** = 發行項也在交易式發行項中發行。|  
|**upload_options**|**tinyiny**|定義是否能在訂閱者端進行變更或從訂閱者上傳變更，它可以是下列值之一。<br /><br /> **0** = 在訂閱者端進行的更新沒有任何限制;所有變更都會上傳到發行者。<br /><br /> **1** = 允許在訂閱者端進行變更，但不會上傳至發行者。<br /><br /> **2** = 在訂閱者端不允許變更。|  
|**輕巧**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**delete_proc**|**sysname**|預設衝突解析程式在同步處理期間刪除資料列所使用的程序。|  
|**before_upd_view_objid**|**int**|在更新之前，資料表的檢視之識別碼。|  
|**delete_tracking**|**bit**|指出是否複寫刪除。<br /><br /> **0** = 不復寫刪除。<br /><br /> **1** = 已複寫刪除，這是合併式複寫的預設行為。<br /><br /> 當*delete_tracking*的值為**0**時，必須在發行者端手動移除在訂閱者端刪除的資料列，而且必須在訂閱者端手動移除在發行者端刪除的資料列。<br /><br /> 注意： **0**值會導致非聚合。|  
|**compensate_for_errors**|**bit**|指出在同步處理期間發現錯誤時，是否採取補償動作。<br /><br /> **0** = 補償動作已停用。<br /><br /> **1** = 無法在訂閱者或發行者端套用的變更，一律會導致補償動作復原這些變更，這是合併式複寫的預設行為。<br /><br /> 注意： **0**值會導致非聚合。|  
|**pub_range**|**bigint**|發行者識別範圍大小。|  
|**格或**|**bigint**|將在調整中指派給訂閱者的連續識別值大小。|  
|**閾值**|**int**|識別範圍臨界值百分比。|  
|**metadata_select_proc**|**sysname**|用來存取合併式複寫系統資料表中的中繼資料之自動產生預存程序的名稱。|  
|**stream_blob_columns**|**bit**|指定當複寫二進位大型物件資料行時，是否使用資料流最佳化。 **1**表示將嘗試優化。|  
|**preserve_rowguidcol**|**bit**|指出複寫是否使用現有的 rowguid 資料行。 值為**1**表示使用現有的 ROWGUIDCOL 資料行。 **0**表示複寫已加入 ROWGUIDCOL 資料行。|  
  
## <a name="see-also"></a>另請參閱  
 複寫[資料表&#40;transact-sql&#41; ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replication Views &#40;transact-sql&#41; ](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addmergearticle &#40;transact-sql&#41; ](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [sp_helpmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)   
 [sysmergearticles &#40;transact-sql&#41;](../../relational-databases/system-tables/sysmergearticles-transact-sql.md)  
  
  
