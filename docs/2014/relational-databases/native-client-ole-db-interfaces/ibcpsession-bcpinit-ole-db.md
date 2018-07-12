---
title: 'Ibcpsession:: Bcpinit (OLE DB) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPInit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPInit method
ms.assetid: 583096d7-da34-49be-87fd-31210aac81aa
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 11ddae5bacdd5428a4381ec034d9dc9f0f22b6b7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413398"
---
# <a name="ibcpsessionbcpinit-ole-db"></a>IBCPSession::BCPInit (OLE DB)
  初始化大量複製結構、執行一些錯誤檢查、確認資料和格式檔案名稱正確無誤，然後開啟這些項目。  
  
## <a name="syntax"></a>語法  
  
```  
  
HRESULT BCPInit(   
const wchar_t *pwszTable,  
const wchar_t *pwszDataFile,  
const wchar_t *pwszErrorFile,  
inteDirection);  
```  
  
## <a name="remarks"></a>備註  
 **BCPInit**方法應在其他任何大量複製方法之前呼叫。 **BCPInit**方法會執行必要的初始化大量複製到工作站之間的資料和[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
 **BCPInit**方法會檢查資料庫來源或目標資料表，不是資料檔案的結構。 此方法會根據資料庫資料表、檢視或 SELECT 結果集中的每個資料行，指定資料檔的資料格式值。 這個指定包括每個資料行的資料類型、資料中是否有長度或 null 指標和結束字元位元組字串，以及固定長度資料類型的寬度。 **BCPInit**方法會設定這些值，如下所示：  
  
-   指定的資料類型為資料行在資料庫資料表、檢視或 SELECT 結果集中的資料類型。 資料類型會列舉[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中指定的原生資料型別[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client 標頭檔 (sqlncli.h)。 其值會採用 BCP_TYPE_XXX 的模式。 資料會以其電腦格式表示。 也就是說，來自 integer 資料類型之資料行的資料會根據建立資料檔案之電腦，以四個位元組由大到小或由小到大的順序表示。  
  
-   如果資料庫資料類型的長度是固定的，資料檔案資料的長度也是固定的。 處理資料的大量複製方法 (例如[Bcpexec](ibcpsession-bcpexec-ole-db.md)) 剖析中的資料庫資料表、 檢視或 SELECT 資料行中指定的資料長度相同的資料檔案中的資料長度的資料列清單。 例如，定義為 `char(13)` 之資料庫資料行的資料，對於檔案中資料的每個資料列，必須以 13 個字元表示。 如果資料庫資料行允許使用 Null 值，固定長度的資料前置詞可以是 Null 指標。  
  
-   複製資料到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，資料檔案對於資料庫資料表中的每個資料行都必須有資料。 從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複製資料時，來自資料庫資料表、檢視或 SELECT 結果集中所有資料行的資料都會複製到資料檔案中。  
  
-   複製資料到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，資料行在資料檔案中的序數位置必須與資料行在資料庫資料表中的序數位置相同。 從複製資料時[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，則**BCPExec**方法會根據資料庫資料表中的資料行的序數位置的資料。  
  
-   如果資料庫資料類型的長度是變數 (例如，`varbinary(22)`)，或者如果資料庫資料行可以包含 Null 值，資料檔案中資料的前置詞為長度/Null 指標。 指標的寬度會根據資料類型和大量複製的版本而改變。 [Ibcpsession:: Bcpcontrol](ibcpsession-bcpcontrol-ole-db.md)方法選項 BCP_OPTION_FILEFMT 會提供舊版大量複製資料檔案和執行較新版本的伺服器之間的相容性[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指出當指標的寬度資料會比預期窄。  
  
> [!NOTE]  
>  若要變更的資料檔指定的資料格式值，請使用[ibcpsession:: Bcpcolumns](ibcpsession-bcpcolumns-ole-db.md)並[ibcpsession:: Bcpcolfmt](ibcpsession-bcpcolfmt-ole-db.md)方法。  
  
 大量複製[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]可以藉由設定資料庫選項，不包含索引的資料表最佳化**選入 / bulkcopy**。  
  
## <a name="arguments"></a>引數  
 *pwszTable*[in]  
 這是要來回複製之資料庫資料表的名稱。 此名稱也可以包含資料庫名稱或擁有者名稱。 例如，"pubs.username.titles"、"pubs..titles" 和 "username.titles" 等。  
  
 如果 eDirection 引數設定為 BCP_DIRECTION_OUT，則 pwszTable 引數也可以做為資料庫檢視的名稱。  
  
 如果 eDirection 引數設定為 BCP_DIRECTION_OUT，而且使用指定的 SELECT 陳述式**BCPControl**方法，然後再**BCPExec**呼叫方法時， *pwszTable*引數必須設定為 NULL。  
  
 *pwszDataFile*[in]  
 這是要來回複製之使用者檔案的名稱。  
  
 *pwszErrorFile*[in]  
 這是錯誤檔案的名稱，該檔案會以進度訊息、錯誤訊息，以及因為任何原因而無法從使用者檔案複製到資料表之任何資料列的複本。 如果*pwszErrorFile*引數設定為 NULL 時，會使用任何錯誤檔案。  
  
 *eDirection*[in]  
 這是複製的方向，BCP_DIRECTION_IN 或 BCP_DIRECTION _OUT。 BCP_DIRECTION _IN 代表從使用者檔案複製到資料庫資料表；BCP_DIRECTION _OUT 則代表從資料庫資料表複製到使用者檔案。  
  
## <a name="return-code-values"></a>傳回碼值  
 S_OK  
 此方法已成功。  
  
 E_FAIL  
 發生提供者特有的錯誤 ' 詳細資訊，請使用[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)介面。  
  
 E_OUTOFMEMORY  
 記憶體不足錯誤  
  
 E_INVALIDARG  
 未正確指定一個或多個引數。 例如，指定了無效的檔案名稱。  
  
## <a name="see-also"></a>另請參閱  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [執行大量複製作業](../native-client/features/performing-bulk-copy-operations.md)  
  
  
