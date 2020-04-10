---
title: SqlTypes 和資料集
description: 描述資料集中對 SqlTypes 的類型支援。
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 2d6f5ec17e800cbac571554a359c2ebd43fa9186
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80918579"
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes 和資料集

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

ADO.NET 2.0 透過 `DataSet` 命名空間引進了對 <xref:System.Data.SqlTypes> 的增強類型支援。 <xref:System.Data.SqlTypes> 中的類型其設計目的是提供與 SQL Server 資料庫中的資料類型具有相同語意及精確度的資料類型。 <xref:System.Data.SqlTypes> 中的每個資料類型，在 SQL Server 中都具有對應的資料類型，並具有相同的基礎資料表示。  
  
直接在 <xref:System.Data.SqlTypes> 中使用 <xref:System.Data.DataSet>，會在使用 SQL Server 資料類型時帶來數個優點。 <xref:System.Data.SqlTypes> 支援與 SQL Server 原生資料類型相同的語意。 在 <xref:System.Data.SqlTypes> 的定義中指定其中一個 <xref:System.Data.DataColumn>，在將十進位或數值資料類型轉換為通用語言執行平台 (CLR) 資料類型之一時就不會發生精確度遺失。  

下列範例建立 <xref:System.Data.DataTable> 物件，其會使用 <xref:System.Data.DataColumn> 而非 CLR 類型，來明確定義 <xref:System.Data.SqlTypes> 資料類型。 該程式碼會將 SQL Server 中 AdventureWorks 資料庫內 Sales.SalesOrderDetail 資料表的資料，填入 <xref:System.Data.DataTable>。 主控台視窗中顯示的輸出會顯示每個資料行的資料類型，以及擷取自 SQL Server 的值。  
  
[!code-csharp[DataWorks DataColumn_DataType#1](~/../sqlclient/doc/samples/DataColumn_DataType.cs#1)]
