---
title: 重新同步處理資料列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- synchronization [OLE DB]
- IRowsetResynch interface
- resynchronizing rows
- data updates [SQL Server], OLE DB
ms.assetid: d2d30505-a878-4aa9-b821-53d8118a45a5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b041dc07afb30fff0c03d96fec9cd8a5d62f965
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2020
ms.locfileid: "63229015"
---
# <a name="resynchronizing-rows"></a>重新同步處理資料列
  Native Client OLE DB 提供者只支援資料[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指標支援的資料列集上的**IRowsetResynch。** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **IRowsetResynch** 無法視需要提供。 取用者必須在開啟資料列集前要求此介面。  
  
## <a name="see-also"></a>另請參閱  
 [更新資料列集內的資料](updating-data-in-rowsets.md)  
  
  
