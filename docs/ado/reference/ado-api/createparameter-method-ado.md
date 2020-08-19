---
description: CreateParameter 方法 (ADO)
title: " (ADO) 的 CreateParameter 方法 |Microsoft Docs"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::raw_CreateParameter
- Command15::CreateParameter
helpviewer_keywords:
- CreateParameter method [RDS]
ms.assetid: 9666fdcc-0544-4ed7-a97b-c415f2a56d7e
author: rothja
ms.author: jroth
ms.openlocfilehash: 6bf45e2d458784972d7057e95878c9db3526ffac
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444320"
---
# <a name="createparameter-method-ado"></a>CreateParameter 方法 (ADO)
使用指定的屬性建立新的 [參數](../../../ado/reference/ado-api/parameter-object.md) 物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
Set parameter = command.CreateParameter (Name, Type, Direction, Size, Value)  
```  
  
## <a name="return-value"></a>傳回值  
 傳回 **參數** 物件。  
  
#### <a name="parameters"></a>參數  
 *名稱*  
 選擇性。 包含**參數**物件名稱的**字串**值。  
  
 *型別*  
 選擇性。 [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)值，指定**參數**物件的資料類型。  
  
 *方向*  
 選擇性。 [ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md)值，指定**參數**物件的型別。  
  
 *大小*  
 選擇性。 **Long**值，指定參數值的最大長度（以字元或位元組為單位）。  
  
 *值*  
 選擇性。 **變數**，指定**參數**物件的值。  
  
## <a name="remarks"></a>備註  
 使用 **CreateParameter** 方法，建立具有指定之名稱、類型、方向、大小和值的新 **參數** 物件。 您在引數中傳遞的任何值都會寫入至對應的 **參數** 屬性。  
  
 這個方法不會自動將**參數**物件附加至[Command](../../../ado/reference/ado-api/command-object-ado.md)物件的**Parameters**集合。 這可讓您設定其他屬性，而這些屬性的值會在您將 **參數** 物件附加至集合時進行驗證。  
  
 如果您在*類型*引數中指定可變長度的資料類型，您必須先傳遞*大小*引數，或設定**參數**物件的[size](../../../ado/reference/ado-api/size-property-ado-parameter.md)屬性，然後再將它附加至**Parameters**集合;否則，就會發生錯誤。  
  
 如果您在*類型*引數中指定數值資料類型 (**adNumeric**或**adDecimal**) ，您也必須設定[NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md)和[Precision](../../../ado/reference/ado-api/precision-property-ado.md)屬性。  
  
## <a name="applies-to"></a>套用至  
 [Command 物件 (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [附加和 CreateParameter 方法範例 (VB) ](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [附加和 CreateParameter 方法範例 (VC + +) ](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [ (ADO) 的 Append 方法 ](../../../ado/reference/ado-api/append-method-ado.md)   
 [Parameter 物件](../../../ado/reference/ado-api/parameter-object.md)   
 [Parameters 集合 (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
