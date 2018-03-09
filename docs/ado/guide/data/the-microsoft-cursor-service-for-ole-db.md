---
title: "OLE DB 的 Microsoft 資料指標服務 |Microsoft 文件"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursor service for ole db [ADO]
- cursors [ADO], cursor service for OLE DB
ms.assetid: 1ac3bd9b-2d45-4cc8-88ec-bd8a218cfb49
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5dd9f4b279bd38028bb529dcdd0a49f32ffd7cc7
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="the-microsoft-cursor-service-for-ole-db"></a>OLE DB 的 Microsoft 指標服務
當您選取用戶端資料指標，或設定**CursorLocation**屬性**adUseClient**，您會在叫用 Microsoft 資料指標服務的 OLE DB。 您也可能會看到 「 用戶端資料指標引擎 」，也就是基本上相同的動作 ADO 的內容中的參考。 此服務會補充資料提供者的資料指標支援函式。 如此一來，您可以對看待相當一致的功能，從所有資料提供者。  
  
 OLE DB 資料指標服務可提供動態內容，並增強特定方法的行為。 例如，**最佳化**動態屬性可讓建立暫存索引以利於進行某些作業，例如**尋找**方法。  
  
 資料指標服務可提供批次更新在所有情況下支援。 資料提供者只可以提供較不支援的資料指標，例如靜態資料指標時，它也會模擬更適用的資料指標類型，例如動態資料指標。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB （ADO 服務元件） 的 Microsoft 資料指標服務](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)
