---
title: 'Ibcpsession:: Bcpcolumns (OLE DB) |Microsoft 文件'
description: IBCPSession::BCPColumns (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBCPSession::BCPColumns (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPColumns method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: c66dadc27b4a58e507aa08f0e075d05f17500740
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35304947"
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a>IBCPSession::BCPColumns (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  設定要繫結至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料表中之資料行的欄位數目。  
  
## <a name="syntax"></a>語法  
  
```  
  
HRESULT BCPColumns(   
      DBCOUNTITEM nColumns);  
```  
  
## <a name="remarks"></a>備註  
 它會在內部呼叫[ibcpsession:: Bcpcolfmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)設定欄位資料的預設值。 這些預設值從提供者，在內部擷取透過指定資料表名稱時，SQL Server 資料行資訊取得[ibcpsession:: Bcpinit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)。  
  
> [!NOTE]  
>  這個方法後，才可以呼叫**BCPInit**已使用有效的檔案名稱呼叫。  
  
 只有打算使用與預設值不同的使用者檔案格式時，才可以呼叫此方法。 如需預設使用者檔案格式描述的詳細資訊，請參閱**BCPInit**方法。  
  
 在呼叫**BCPColumns**方法，您必須呼叫**BCPColFmt**以完整定義自訂的檔案格式的使用者檔案中的每個資料行的方法。  
  
## <a name="arguments"></a>引數  
 *nColumns*[in]  
 使用者檔案中的欄位總數。 即使您準備要從使用者檔案的 SQL server 的大量複製資料的資料表，並不想複製使用者檔案中的所有欄位，您仍然必須設定*nColumns*使用者檔案欄位的總數目的引數。 然後可以透過指定略過的欄位**BCPColFmt**。  
  
## <a name="return-code-values"></a>傳回碼值  
 S_OK  
 此方法已成功。  
  
 E_FAIL  
 發生提供者特定的錯誤。詳細資訊，請使用[ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)介面。  
  
 E_UNEXPECTED  
 此方法的呼叫是非預期的。 例如， **BCPInit**方法不會呼叫這個方法之前呼叫。 針對大量複製作業呼叫此方法超過一次時，也會發生這個狀況。  
  
 E_OUTOFMEMORY  
 記憶體不足錯誤  
  
## <a name="see-also"></a>另請參閱  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [執行大量複製作業](../../oledb/features/performing-bulk-copy-operations.md)  
  
  
