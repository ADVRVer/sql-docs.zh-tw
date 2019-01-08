---
title: sp_cursor (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_TSQL
- sp_cursor
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursor
ms.assetid: 41ade0ca-5f11-469d-bd4d-c8302ccd93b3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e3277e64e4c4e04e270298d3532ebc0c2b1f93c5
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53210517"
---
# <a name="spcursor-transact-sql"></a>sp_cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  要求定點更新。 這個程序會針對資料指標的提取緩衝區內的一個或多個資料列執行作業。 sp_cursor 的叫用方式指定 ID = 1，在表格式資料流 (TDS) 封包中的。  
  
||  
|-|  
|**適用於**：SQL Server ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]經由[目前版本](https://go.microsoft.com/fwlink/p/?LinkId=299658))。|  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_cursor  cursor, optype, rownum, table  
    [ , value[...n]]]  
```  
  
## <a name="arguments"></a>引數  
 *cursor*  
 資料指標控制代碼。 *資料指標*是必要的參數呼叫**int**輸入值。 *資料指標*已*處理*值由 SQL Server 所產生及 sp_cursoropen 程序所傳回。  
  
 *optype*  
 這是必要參數，可指定資料指標將要執行哪一個作業。 *optype*需要下列其中一種**int**輸入值。  
  
|值|名稱|描述|  
|-----------|----------|-----------------|  
|0X0001|UPDATE|這是用來更新提取緩衝區內的一個或多個資料列。  在指定的資料列*rownum*會重新存取及更新。|  
|0x0002|DELETE|這是用來刪除提取緩衝區內的一個或多個資料列。 在指定的資料列*rownum*會重新存取及刪除。|  
|0X0004|Insert|將資料插入而不建置 SQL**插入**陳述式。|  
|0X0008|REFRESH|這是用來從基礎資料表重新填滿緩衝區，而且在更新或刪除因為開放式並行控制而失敗或者在 UPDATE 之後，可用來重新整理資料列。|  
|0X10|LOCK|會導致 SQL Server U-lock 包含指定的資料列的頁面上取得。 這個鎖定與 S-Locks 相容，但是與 X-Locks 或其他 U-Locks 不相容。 可用來實作短期鎖定。|  
|0X20|SETPOSITION|僅當程式即將發出後續的 SQL Server 定位 DELETE 或 UPDATE 陳述式使用。|  
|0X40|ABSOLUTE|只能搭配 UPDATE 或 DELETE 使用。  ABSOLUTE 只能搭配 KEYSET 資料指標使用 (DYNAMIC 資料指標和 STATIC 資料指標則會忽略，而且無法更新)。<br /><br /> 注意：如果在尚未提取之索引鍵集內的資料列上指定 ABSOLUTE，該作業可能無法通過並行檢查，而且無法保證傳回結果。|  
  
 *rownum*  
 指定資料指標將要運作、更新或刪除提取緩衝區內的哪些資料列。  
  
> [!NOTE]  
>  這樣不會影響任何 RELATIVE、NEXT 或 PREVIOUS 提取作業的起點，也不會影響使用 sp_cursor 執行的任何更新或刪除。  
  
 *rownum*是必要的參數呼叫**int**輸入值。  
  
 1  
 代表提取緩衝區內的第一個資料列。  
  
 2  
 代表提取緩衝區內的第二個資料列。  
  
 3, 4, 5  
 代表第三個資料列，依此類推。  
  
 n  
 代表提取緩衝區內的第 n 個資料列。  
  
 0  
 代表提取緩衝區內的所有資料列。  
  
> [!NOTE]  
>  只適用於更新、 刪除、 重新整理或鎖定*optype*值。  
  
 *table*  
 識別資料表的資料表名稱， *optype*適用於當資料指標定義牽涉到的聯結或模稜兩可的資料行名稱會傳回*值*參數。 如果未指定特定的資料表，預設值為 FROM 子句內的第一個資料表。 *資料表*是需要字串輸入的值的選擇性參數。 此字串可以指定為任何字元或 UNICODE 資料類型。 *資料表*可以是多部分的資料表名稱。  
  
 *value*  
 用來插入或更新值。 *值*字串參數只能搭配 UPDATE 和 INSERT *optype*值。 此字串可以指定為任何字元或 UNICODE 資料類型。  
  
> [!NOTE]  
>  參數名稱*值*可以由使用者指派。  
  
## <a name="return-code-values"></a>傳回碼值  
 當使用 RPC 時，緩衝區編號 0 的定位的 DELETE 或 UPDATE 作業會傳回 DONE 訊息，而且*rowcount*為 0 （失敗） 或 1 （成功） 在提取緩衝區中的每個資料列。  
  
## <a name="remarks"></a>備註  
  
## <a name="optype-parameter"></a>optype 參數  
 除了 SETPOSITION 搭配 UPDATE、 DELETE、 重新整理或鎖定; 的組合或搭配 UPDATE 或 DELETE 絕對*optype*是互斥的值。  
  
 更新值的 SET 子句建構自*值*參數。  
  
 使用 插入的一個好處*optype*值是您可以避免將非字元資料轉換成字元格式進行插入。 這些值的指定方式與 UPDATE 相同。 如果未包含任何必要的資料行，INSERT 將會失敗。  
  
-   SETPOSITION 值不會影響任何 RELATIVE、NEXT 或 PREVIOUS 提取作業的起點，也不會影響使用 sp_cursor 介面執行的任何更新或刪除。 未在提取緩衝區內指定資料列的任何數字將會導致位置設定為 1，而且不會傳回任何錯誤。 一旦執行 SETPOSITION 之後，位置會生效，直到下一個 sp_cursorfetch 作業、 T-SQL**擷取**作業或 sp_cursor SETPOSITION 作業，透過相同的資料指標。 後續的 sp_cursorfetch 作業會將資料指標的位置設定為新提取緩衝區內的第一個資料列，而其他資料指標呼叫將不會影響該位置的值。 SETPOSITION 可以透過 OR 子句來連結 REFRESH、UPDATE、DELETE 或 LOCK，以便將該位置的值設定為上一個修改的資料列。  
  
 如果未指定提取緩衝區中的資料列則透過*rownum*參數，位置會設定為 1，而且傳回任何錯誤。 一旦設定位置之後，該位置就會生效，一直到透過相同資料指標執行下一個 sp_cursorfetch 作業、T-SQL FETCH 作業或 sp_cursor SETPOSITION 作業為止。  
  
 SETPOSITION 可以透過 OR 子句來連結 REFRESH、UPDATE、DELETE 或 LOCK，以便將資料指標位置設定為上一個修改的資料列。  
  
## <a name="rownum-parameter"></a>rownum 參數  
 如果指定， *rownum*參數可以解譯為資料列數目，而提取緩衝區內的資料列號碼不是索引鍵集內。 使用者負責確認並行控制的維護。 這表示對於 SCROLL_LOCKS 資料指標而言，您必須獨立維護給定資料列的鎖定 (可以透過交易來完成)。 對於 OPTIMISTIC 資料指標而言，您之前必須已經提取資料列，才能執行這項作業。  
  
## <a name="table-parameter"></a>table 參數  
 如果*optype*值是 UPDATE 或 INSERT 和完整的 update 或 insert 陳述式提交為*值*參數，為指定值*表格*會被忽略。  
  
> [!NOTE]  
>  與檢視表有關，只能修改參與檢視表的一個資料表。 *值*參數資料行名稱必須反映在檢視中，資料行名稱，但是資料表名稱可以是基底資料表 （此時 sp_cursor 將會替代檢視表名稱）。  
  
## <a name="value-parameter"></a>value 參數  
 有兩個替代方式，使用的規則*值*如引數 區段中的稍早所述：  
  
1.  您可以使用的名稱 '\@' 前面的 select 清單中的資料行名稱，針對任何具名*值*參數。 這個替代方案的一個優點是可能不需要轉換資料。  
  
2.  您可以使用參數來提交完整的 UPDATE 或 INSERT 陳述式，或使用多個參數來提交 UPDATE 或 INSERT 陳述式的 SQL Server 會將其建置成完整的陳述式的部分。 這部分的範例可以在本主題稍後的＜範例＞一節找到。  
  
## <a name="examples"></a>範例  
  
### <a name="alternative-value-parameter-uses"></a>其他值參數的使用  
 如果是 UPDATE：  
  
 當使用單一參數時，可以使用下列語法來提交 UPDATE 陳述式：  
  
 `[ [ UPDATE <table name> ] SET ] {<column name> = expression} [,...n]`  
  
> [!NOTE]  
>  如果更新\<資料表名稱 > 指定，則指定的任何值*表格*參數將會被忽略。  
  
 當使用多個參數時，第一個參數必須是以下格式的字串：  
  
 `[ SET ] <column name> = expression  [,...n]`  
  
 後續的參數必須是以下的格式：  
  
 `<column name> = expression  [,...n]`  
  
 在此情況下，\<資料表名稱 > 中建構的 update 陳述式會指定或預設為所*表格*參數。  
  
 如果是 INSERT：  
  
 當使用單一參數時，可以使用下列語法來提交 INSERT 陳述式：  
  
 `[ [ INSERT [INTO] <table name> ] VALUES ] ( <expression> [,...n] )`  
  
> [!NOTE]  
>  如果插入*\<資料表名稱 >* 指定，則指定的任何值*表格*參數將會被忽略。  
  
 當使用多個參數時，第一個參數必須是以下格式的字串：  
  
 `[ VALUES ( ] <expression>  [,...n]`  
  
 後續的參數必須是以下的格式：  
  
 `expression [,...n]`  
  
 除非在指定 VALUES 的情況下，此時最後一個運算式後面必須有尾端 ")"。 在此情況下， *\<資料表名稱 >* 在建構的 UPDATE 陳述式是指定或預設為依*表格*參數。  
  
> [!NOTE]  
>  可以將一個參數當做具名參數來提交，也就是 "`@VALUES`"。 在此情況下，無法使用其他具名參數。  
  
## <a name="see-also"></a>另請參閱  
 [sp_cursoropen &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorfetch &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
