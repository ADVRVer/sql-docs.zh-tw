---
title: 大型 CLR 使用者定義型別 |Microsoft Docs
description: 大型 CLR 使用者定義型別在 OLE DB Driver for SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 4cf71fa76c4759364954c8cbff446957dd80c8aa
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2018
ms.locfileid: "39108060"
---
# <a name="large-clr-user-defined-types"></a>大型 CLR 使用者定義型別
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  在 SQL Server 2005，Common Language Runtime (CLR) 中的使用者定義型別 (UDT) 在大小上限制為 8,000 個位元組。 在 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 和更新版本中已提高此限制。 CLR UDT 現在會以大型物件 (LOB) 類型類似的方式處理。 也就是說，小於或等於 8,000 個位元組的 UDT 行為與 SQL Server 2005 相同，但是支援較大的 UDT，而且會將其大小報告為「無限制」。  
  
 如需詳細資訊，請參閱 < [Large CLR User-Defined 類型&#40;OLE DB&#41;](../../oledb/ole-db/large-clr-user-defined-types-ole-db.md)。  
  
## <a name="use-cases"></a>使用案例   
  
 對於 OLE DB，大型 UDT 的支援包括能夠使用 ISequentialStream 繫結，在伺服器來回串流 UDT 值。  
  
 小於或等於 8,000 個位元組的 UDT 行為如同在 SQL Server 2005 中的行為。 OLE db 中，您仍可以使用 ISequentialStream 繫結，以串流小型 Udt。  
  
 原生程式碼有時候必須了解 CLR UDT 的內容，但不必具現化 Managed 物件。 如果是這種情況，您可以使用自訂序列化，將伺服器上的 UDT 值轉換為用戶端熟知的格式。  
  
 對於擁有現有資料存取程式碼的應用程式，您可以透過原生 API 擷取 UDT，並使用混合模式應用程式中的 C++ CLI Interop 進行具現化，藉以利用用戶端上的 CLR UDT 行為。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB Driver for SQL Server 功能](../../oledb/features/oledb-driver-for-sql-server-features.md)    
  
  
