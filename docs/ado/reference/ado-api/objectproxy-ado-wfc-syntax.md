---
title: ObjectProxy (ADO-WFC 語法) |Microsoft 文件
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ObjectProxy collection [ADO]
ms.assetid: f68f58bc-ad28-46cc-9fb3-099e1a678397
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b9f30144edb28fb58e6cb2606f24df22fedce613
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="objectproxy-ado---wfc-syntax"></a>ObjectProxy (ADO-WFC 語法)
**ObjectProxy**物件代表伺服器，而且由**createObject**方法[DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)物件。 ObjectProxy 類別有一個方法，**呼叫**，這可以叫用伺服器上的方法，並傳回所產生的這個引動過程的物件。  
  
 **封裝 com.ms.wfc.data**  
  
## <a name="methods"></a>方法  
  
### <a name="call-method-adowfc-syntax"></a>呼叫方法 （ADO/WFC 語法）  
 叫用 ObjectProxy 所代表的伺服器上的方法。 （選擇性） 為物件的陣列，可在傳遞方法引數。  
  
#### <a name="syntax"></a>語法  
  
```  
public Object ObjectProxy.( String method )  
public Object ObjectProxy.( String method, Object[] args)  
```  
  
#### <a name="returns"></a>傳回值  
 物件  
 叫用方法所產生的物件。  
  
#### <a name="parameters"></a>參數  
 *ObjectProxy*  
 **ObjectProxy**代表伺服器的物件。  
  
 *方法*  
 字串，包含要在伺服器上叫用的方法名稱。  
  
 *引數*  
 選擇性。 陣列的伺服器上之方法的引數的物件。 Java 資料類型會自動轉換成適用於伺服器上使用的資料類型。
