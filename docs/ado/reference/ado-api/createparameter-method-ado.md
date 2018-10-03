---
title: CreateParameter 方法 (ADO) |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b150fe1c0c7260960140558eeff74b54c0798d80
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47631346"
---
# <a name="createparameter-method-ado"></a>CreateParameter 方法 (ADO)
建立新[參數](../../../ado/reference/ado-api/parameter-object.md)具有指定之屬性的物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
Set parameter = command.CreateParameter (Name, Type, Direction, Size, Value)  
```  
  
## <a name="return-value"></a>傳回值  
 傳回**參數**物件。  
  
#### <a name="parameters"></a>參數  
 *[名稱]*  
 選擇性。 A**字串**值，包含名稱**參數**物件。  
  
 *型別*  
 選擇性。 A [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)值，指定的資料型別**參數**物件。  
  
 *方向*  
 選擇性。 A [ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md)值，指定的型別**參數**物件。  
  
 *大小*  
 選擇性。 A**長**值，指定參數值的最大長度的字元或位元組。  
  
 *值*  
 選擇性。 A **Variant**所指定的值**參數**物件。  
  
## <a name="remarks"></a>備註  
 使用**CreateParameter**方法來建立新**參數**具有指定的名稱、 類型、 方向、 大小和值物件。 您傳遞的引數中的任何值會寫入到相對應**參數**屬性。  
  
 這個方法不會自動附加**參數**物件**參數**集合[命令](../../../ado/reference/ado-api/command-object-ado.md)物件。 這可讓您設定其他屬性，當您附加時，將會驗證其值 ADO**參數**物件加入集合。  
  
 如果您指定中的可變長度資料類型*型別*引數，您必須將*大小*引數或組[大小](../../../ado/reference/ado-api/size-property-ado-parameter.md)屬性**參數**附加到之前的物件**參數**集合; 否則會發生錯誤。  
  
 如果您指定的數值資料類型 (**adNumeric**或是**adDecimal**) 中*型別*引數，則您也必須設定[NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md)和[精確度](../../../ado/reference/ado-api/precision-property-ado.md)屬性。  
  
## <a name="applies-to"></a>適用於  
 [Command 物件 (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>另請參閱  
 [附加和 CreateParameter 方法範例 (VB)](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vb.md)   
 [附加和 CreateParameter 方法範例 （VC + +）](../../../ado/reference/ado-api/append-and-createparameter-methods-example-vc.md)   
 [Append 方法 (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [參數物件](../../../ado/reference/ado-api/parameter-object.md)   
 [Parameters 集合 (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)
