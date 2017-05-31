---
title: "時態表安全性 | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 02/21/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60e5d6f6-a26d-4bba-aada-42e382bbcd38
caps.latest.revision: 9
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f73cdc0f3a240e3d4c795fd67c2913b99748de4a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/11/2017

---
# <a name="temporal-table-security"></a>時態表安全性
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  若要了解適用於時態表的安全性，請務必了解適用於時態表的安全性原則。 了解這些安全性原則之後，您就已經準備好深入了解關於 **CREATE TABLE**、 **ALTER TABLE**及 **SELECT** 陳述式的安全性。  
  
## <a name="security-principles"></a>安全性原則  
 下表描述適用於時態表的安全性原則︰  
  
|原則|描述|  
|---------------|-----------------|  
|啟用/停用系統建立版本功能需要受影響物件上的最高權限|啟用和停用 SYSTEM_VERSIONING 需要目前和記錄資料表上的 CONTROL 權限|  
|無法直接修改記錄資料|當 SYSTEM_VERSIONING 為 ON 時，使用者無法變更記錄資料，而不論其在目前或記錄資料表上的實際權限為何。 這包括資料和結構描述修改。|  
|查詢記錄資料需要記錄資料表上的 **SELECT** 權限|只是因為使用者具備目前資料表上的 **SELECT** 權限，並不表示他們具有記錄資料表上的 **SELECT** 權限。|  
|稽核介面作業會以特定方式來影響記錄資料表︰|定期稽核記錄資料表，會擷取所有直接存取資料的嘗試 (不論成功與否)。<br /><br /> **SELECT** 搭配時態查詢延伸模組會顯示記錄資料表已受到該作業影響。<br /><br /> **CREATE/ALTER** 時態表也會公開在記錄資料表上發生的權限檢查資訊。 稽核檔案將包含記錄資料表的額外記錄。<br /><br /> 目前資料表介面上的 DML 作業會影響記錄資料表，但 additional_info 會提供必要的內容 (DML 是 system_versioning 的結果)。|  
  
## <a name="performing-schema-operations"></a>執行結構描述作業  
 將 SYSTEM_VERSIONING 設為 ON 時，結構描述修改作業會受到限制。  
  
### <a name="disallowed-alter-schema-operations"></a>不允許的 ALTER 結構描述作業  
  
|運算|目前的資料表|記錄資料表|  
|---------------|-------------------|-------------------|  
|**DROP TABLE**|不允許|不允許|  
|**ALTER TABLE…SWITCH PARTITION**|僅限 SWITCH IN (請參閱 [對時態表進行資料分割](../../relational-databases/tables/partitioning-with-temporal-tables.md))|僅限 SWITCH OUT (請參閱 [對時態表進行資料分割](../../relational-databases/tables/partitioning-with-temporal-tables.md))|  
|**ALTER TABLE…DROP PERIOD**|不允許|-|  
|**ALTER TABLE…ADD PERIOD**|-|不允許|  
  
## <a name="allowed-alter-table-operations"></a>允許的 ALTER TABLE 作業  
  
|運算|目前|記錄|  
|---------------|-------------|-------------|  
|**ALTER TABLE…REBUILD**|允許 (獨立)|允許 (獨立)|  
|**CREATE INDEX**|允許 (獨立)|允許 (獨立)|  
|**CREATE STATISTICS**|允許 (獨立)|允許 (獨立)|  
  
## <a name="security-of-the-create-temporal-table-statement"></a>建立時態表陳述式的安全性  
  
||建立新的記錄資料表|重複使用現有的記錄資料表|  
|-|------------------------------|----------------------------------|  
|必要的權限|資料庫的**CREATE TABLE** 權限<br /><br /> 在建立目前和記錄資料表之結構描述上的**ALTER** 權限|資料庫的**CREATE TABLE** 權限<br /><br /> 在將建立目前資料表之結構描述上的**ALTER** 權限。<br /><br /> 記錄資料表上的**CONTROL** 權限會指定為建立時態表之 **CREATE TABLE** 陳述式的一部分|  
|稽核|稽核顯示使用者已嘗試建立兩個物件。 作業可能失敗的原因是在資料庫中建立資料表的權限不足，或者變更任一個資料表的結構描述的權限不足。|稽核顯示時態表已建立。 作業可能失敗的原因是在資料庫中建立資料表的權限不足、變更時態表的結構描述的權限不足，或者在記錄資料表上的權限不足。|  
  
## <a name="security-of-the-alter-temporal-table-set-systemversioning-onoff-statement"></a>變更時態表 (SYSTEM_VERSIONING 為 ON/OFF) 陳述式的安全性  
  
||建立新的記錄資料表|重複使用現有的記錄資料表|  
|-|------------------------------|----------------------------------|  
|必要的權限|資料庫的**CONTROL** 權限<br /><br /> 資料庫的**CREATE TABLE** 權限<br /><br /> 在建立記錄資料表之結構描述上的**ALTER** 權限|已變更之原始資料表上的**CONTROL** 權限<br /><br /> 記錄資料表上的**CONTROL** 權限會指定為 **ALTER TABLE** 陳述式的一部分|  
|稽核|稽核顯示時態表已變更，同時已建立記錄資料表。 作業可能失敗的原因是在資料庫中建立資料表的權限不足、變更記錄資料表的結構描述的權限不足，或者修改時態表的權限不足。|稽核顯示時態表已變更，但作業需要記錄資料表的存取權。 作業可能失敗的原因是記錄資料表上的權限不足，或者目前資料表上的權限不足。|  
  
## <a name="security-of-select-statement"></a>SELECT 陳述式的安全性  
 對於不會影響記錄資料表的**SELECT** 陳述式， **SELECT** 權限會維持不變。 對於會影響記錄資料表的 **SELECT** 陳述式，在目前資料表和記錄資料表上都需要 **SELECT** 權限。  
  
## <a name="did-this-article-help-you-were-listening"></a>這篇文章對您有幫助嗎？ 我們會持續聽取您的意見  
 您要尋找哪些資訊？找到了嗎？ 我們會持續聽取您的意見來改進內容。 請將您的意見傳送到 [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Temporal%20Table%20Security%20page)  
  
## <a name="see-also"></a>另請參閱  
 [時態表](../../relational-databases/tables/temporal-tables.md)   
 [開始使用系統建立版本的時態表](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [時態表系統一致性檢查](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [對時態表進行資料分割](../../relational-databases/tables/partitioning-with-temporal-tables.md)   
 [時態表考量與限制](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)   
 [管理系統設定版本之時態表中的歷程記錄資料保留](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [系統版本設定時態表與記憶體最佳化資料表](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [暫存資料表中繼資料檢視和函數](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  

