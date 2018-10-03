---
title: 在 XML 中的資料錄集動態屬性 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50841931d26847ba339d64634d3eff4d7a7efc1b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47712534"
---
# <a name="recordset-dynamic-properties-in-xml"></a>XML 中的資料錄集動態屬性
下列的資料錄集提供者特定屬性 （從用戶端資料指標引擎） 目前會保存為 XML 格式：  
  
-   更新重新同步處理  
  
-   唯一資料表  
  
-   唯一的結構描述  
  
-   唯一的目錄  
  
-   重新同步命令  
  
-   IRowsetChange  
  
-   IRowsetUpdate  
  
-   CommandTimeout  
  
-   BatchSize  
  
-   UpdateCriteria  
  
-   調整形狀名稱  
  
-   AutoRecalc  
  
 這些屬性會儲存在結構描述區段中，為要保存資料錄集的項目定義的屬性。 這些屬性的資料列集結構描述命名空間中定義，而且必須具有前置詞"rs:"。  
  
## <a name="see-also"></a>另請參閱  
 [以 XML 格式保存記錄](../../../ado/guide/data/persisting-records-in-xml-format.md)
