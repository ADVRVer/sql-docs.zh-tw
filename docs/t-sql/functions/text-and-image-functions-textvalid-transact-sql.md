---
title: "TEXTVALID (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TEXTVALID_TSQL
- TEXTVALID
dev_langs:
- TSQL
helpviewer_keywords:
- invalid text pointers [SQL Server]
- valid text pointers [SQL Server]
- TEXTVALID function
- checking text pointers
- text-pointer values
- verifying text pointers
ms.assetid: 9411c349-b59b-4740-a270-92f91d81ad23
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 279022316af7e3a396c7089f48933281264f900f
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="text-and-image-functions---textvalid-transact-sql"></a>文字和影像函數-TEXTVALID (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  A**文字**， **ntext**，或**映像**函式，以檢查特定文字指標是否有效。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]無法使用替代功能。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
TEXTVALID ( 'table.column' ,text_ ptr )  
```  
  
## <a name="arguments"></a>引數  
 *table*  
 這是將使用的資料表名稱。  
  
 *資料行*  
 這是將使用的資料行名稱。  
  
 *text_ptr*  
 這是將檢查的文字指標。  
  
## <a name="return-types"></a>傳回類型  
 **int**  
  
## <a name="remarks"></a>備註  
 如果指標有效，便傳回 1，如果指標無效，便傳回 0。 請注意的識別項**文字**資料行必須包含資料表名稱。 如果有效的文字指標不存在，您便無法使用 UPDATETEXT、WRITETEXT 或 READTEXT。  
  
 下列函數和陳述式也很有用當您使用**文字**， **ntext**，和**映像**資料。  
  
|函數或陳述式|Description|  
|---------------------------|-----------------|  
|PATINDEX**(**'*%模式 %**'***，** *運算式***)**|傳回指定的字元字串中的字元位置**文字**和**ntext**資料行。|  
|DATALENGTH**(***運算式***)**|傳回的資料長度**文字**， **ntext**，和**映像**資料行。|  
|SET TEXTSIZE|傳回的限制，以位元組為單位，**文字**， **ntext**，或**映像**SELECT 陳述式傳回的資料。|  
  
## <a name="examples"></a>範例  
 下列範例報告 `logo` 資料表之 `pub_info` 資料行中的每個值，是否存在有效的文字指標。  
  
> [!NOTE]  
>  若要執行此範例中，您必須安裝**pubs**資料庫。  
  
```  
USE pubs;  
GO  
SELECT pub_id, 'Valid (if 1) Text data'   
   = TEXTVALID ('pub_info.logo', TEXTPTR(logo))   
FROM pub_info  
ORDER BY pub_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pub_id Valid (if 1) Text data   
------ ----------------------   
0736   1                        
0877   1                        
1389   1                        
1622   1                        
1756   1                        
9901   1                        
9952   1                        
9999   1                        
  
(8 row(s) affected)  
```  
  
## <a name="see-also"></a>另請參閱  
 [DATALENGTH &#40;TRANSACT-SQL &#41;](../../t-sql/functions/datalength-transact-sql.md)   
 [PATINDEX &#40;TRANSACT-SQL &#41;](../../t-sql/functions/patindex-transact-sql.md)   
 [SET TEXTSIZE &#40;TRANSACT-SQL &#41;](../../t-sql/statements/set-textsize-transact-sql.md)   
 [文字和影像函數 &#40;TRANSACT-SQL &#41;](http://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)   
 [TEXTPTR &#40;TRANSACT-SQL &#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)  
  
  

