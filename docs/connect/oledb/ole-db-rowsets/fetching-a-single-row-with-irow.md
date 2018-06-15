---
title: 擷取單一資料列使用 irow 來 |Microsoft 文件
description: 擷取 SQL server 使用 IRow 介面的 OLE DB 驅動程式的單一資料列
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [OLE DB Driver for SQL Server]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- OLE DB Driver for SQL Server, fetching
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 7c75eabde5d5691980e0470efd753715015b3011
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35306387"
---
# <a name="fetching-a-single-row-with-irow"></a>使用 IRow 來提取單一資料列
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **IRow**介面實作 OLE DB 驅動程式中的，針對 SQL Server 已經過簡化，以提升效能。 **IRow**允許直接存取單一資料列物件的資料行。 如果您事先知道命令執行的結果將會產生一個資料列， **IRow**會擷取該資料列的資料行。 如果結果集包含多個資料列， **IRow**會公開 （expose) 的第一個資料列。  
  
 **IRow**實作不允許資料列的任何瀏覽。 此資料列中的每個資料行只會存取一次，但有一項例外狀況：您可以存取一次資料行來尋找資料行大小，然後再次存取，以便提取資料。  
  
> [!NOTE]  
>  **Irow:: Open**僅支援開啟 DBGUID_STREAM 和 DBGUID_NULL 類型的物件。  
  
 若要取得資料列的物件使用**icommand:: Execute**方法，您必須傳遞 IID_IRow。 **IMultipleResults**介面必須用來處理多個結果集。 **IMultipleResults**支援**IRow**和**IRowset**。 **IRowset**適用於大量作業。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 IRow::GetColumns](../../oledb/ole-db-rowsets/using-irow-getcolumns.md)   
  
## <a name="see-also"></a>另請參閱  
 [資料列集](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
