---
description: IsReadOnly 屬性 (SqlServiceAdvancedProperty 類別)
title: 'IsReadOnly 屬性 (SqlServiceAdvancedProperty) '
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- IsReadOnly Property (SqlServiceAdvancedProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- IsReadOnly property
ms.assetid: 9672e70f-1d8c-4133-ac73-3b5733a1c4ee
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 41bfb28199b868276861b68c78af40ea7b83af7d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427170"
---
# <a name="isreadonly-property-sqlserviceadvancedproperty-class"></a>IsReadOnly 屬性 (SqlServiceAdvancedProperty 類別)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  取得或設定布林屬性，該屬性會指定進階屬性是否為唯讀。  
  
## <a name="syntax"></a>語法  
  
```  
  
object.IsReadOnly [= value]  
```  
  
## <a name="parts"></a>組件  
 *object*  
 代表進階屬性的 [SqlServiceAdvancedProperty 類別](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) 物件。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 指定進階屬性是否為唯讀的布林值：如果進階屬性為唯讀則為 **true** ，如果可以修改進階屬性則為 **false** 。  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
