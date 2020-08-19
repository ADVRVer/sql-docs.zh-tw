---
description: ObjectProxy (ADO - WFC 語法)
title: ObjectProxy (ADO-WFC 語法) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ObjectProxy collection [ADO]
ms.assetid: f68f58bc-ad28-46cc-9fb3-099e1a678397
author: rothja
ms.author: jroth
ms.openlocfilehash: 7809c1b9ce4d090ed63465061045ea04000f47dc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443030"
---
# <a name="objectproxy-ado---wfc-syntax"></a>ObjectProxy (ADO - WFC 語法)
**ObjectProxy**物件代表伺服器，而且是由量[空間](../../../ado/reference/rds-api/dataspace-object-rds.md)物件的**createObject**方法傳回。 ObjectProxy 類別有一個方法 call，它可以在伺服器上 **叫**用方法，並傳回該調用所產生的物件。  
  
 **封裝 .com. 資料**  
  
## <a name="methods"></a>方法  
  
### <a name="call-method-adowfc-syntax"></a> (ADO/WFC 語法的 Call 方法)   
 在 ObjectProxy 所代表的伺服器上叫用方法。 （選擇性）方法引數可以傳遞為物件的陣列。  
  
#### <a name="syntax"></a>語法  
  
```  
public Object ObjectProxy.( String method )  
public Object ObjectProxy.( String method, Object[] args)  
```  
  
#### <a name="returns"></a>傳回  
 Object  
 叫用方法所產生的物件。  
  
#### <a name="parameters"></a>參數  
 *ObjectProxy*  
 代表伺服器的 **ObjectProxy** 物件。  
  
 *方法*  
 字串，包含要在伺服器上叫用的方法名稱。  
  
 *參數*  
 選擇性。 物件的陣列，這些物件是伺服器上方法的引數。 JAVA 資料類型會自動轉換成適合在伺服器上使用的資料類型。
