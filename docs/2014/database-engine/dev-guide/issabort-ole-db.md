---
title: ISSAbort (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISSAbort interface
ms.assetid: 7c4df482-4a83-4da0-802b-3637b507693a
caps.latest.revision: 11
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6ace6518c1a0f4ece66ec0b9b24cb9e109db7ffa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180345"
---
# <a name="issabort-ole-db"></a>ISSAbort (OLE DB)
  **ISSAbort**介面中公開[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者，可提供[issabort:: Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)方法用來取消目前的資料列集加上任何命令批次使用命令一開始會產生資料列集，和，尚未完成執行。  
  
 **ISSAbort**已[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client 提供者特定介面，可以使用**QueryInterface**上**IMultipleResults**所傳回的物件**Icommand:: Execute**或是**iopenrowset:: Openrowset**。  
  
## <a name="in-this-section"></a>本節內容  
  
|方法|描述|  
|------------|-----------------|  
|[Issabort:: Abort &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)|取消目前的資料列集加上與目前命令相關聯之任何批次處理的命令。|  
  
## <a name="see-also"></a>另請參閱  
 [介面&#40;OLE DB&#41;](../../../2014/database-engine/dev-guide/interfaces-ole-db.md)  
  
  
