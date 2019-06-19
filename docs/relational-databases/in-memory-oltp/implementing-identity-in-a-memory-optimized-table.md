---
title: 在記憶體最佳化資料表中實作 IDENTITY | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 670cbaf1532c5d958c746ec8645a02815a7e5c01
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "63047656"
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a>在記憶體最佳化資料表中實作 IDENTITY
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

只要種子和遞增值皆為 1 (預設值)，記憶體最佳化資料表便支援 IDENTITY。 記憶體最佳化資料表不支援定義為 IDENTITY(x, y) (其中 x != 1 或 y != 1) 的識別欄位。   
    
若要增加 IDENTITY 種子，請使用工作階段選項 `SET IDENTITY_INSERT table_name ON`，插入具有識別欄位之明確值的新資料列。 插入資料列之後，IDENTITY 種子會變更為明確插入的值加上 1。 例如，若要將種子增加到 1000，請插入識別欄位值為 999 的資料列。 產生的識別值接著會從 1000 開始。     
  
## <a name="see-also"></a>另請參閱  
 [移轉至 In-Memory OLTP](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
