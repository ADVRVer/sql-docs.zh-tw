---
title: IRowsetFastLoad (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- IRowsetFastLoad interface
ms.assetid: d19a7097-48d9-409a-aff9-277891b7aca7
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60d4d982eb88498cf3d56f14efdffae05a71d26a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415087"
---
# <a name="irowsetfastload-ole-db"></a>IRowsetFastLoad (OLE DB)
  `IRowsetFastLoad`介面會公開支援[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]記憶體為基礎的大量複製作業。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者取用者使用介面來快速將資料加入至現有[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料表。  
  
 如果您針對工作階段將 SSPROP_ENABLEFASTLOAD 設定為 VARIANT_TRUE，您無法讀取之後從該工作階段傳回之資料列集中的資料。 當 SSPROP_ENABLEFASTLOAD 設定為 VARIANT_TRUE 時，工作階段上建立的所有資料列集都屬於類型 IRowsetFastLoad。 IRowsetFastLoad 資料列集不支援資料列集提取功能;因此，無法讀取這些資料列集的資料。  
  
## <a name="in-this-section"></a>本節內容  
  
|方法|描述|  
|------------|-----------------|  
|[Irowsetfastload:: Commit &#40;OLE DB&#41;](irowsetfastload-commit-ole-db.md)|標示已插入之資料列批次的結尾，並將資料列寫入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表。|  
|[Irowsetfastload:: Insertrow &#40;OLE DB&#41;](irowsetfastload-insertrow-ole-db.md)|將資料列加入至大量複製資料列集。|  
  
## <a name="see-also"></a>另請參閱  
 [介面&#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)   
 [大量複製資料，使用 IRowsetFastLoad &#40;OLE DB&#41;](../native-client-ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [將 BLOB 資料傳送到 SQL SERVER 使用 IROWSETFASTLOAD 和 ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  
