---
title: PropertyIndex 屬性 （SqlServiceAdvancedProperty 類別） |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- PropertyIndex Property (SqlServiceAdvancedProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- PropertyIndex property
ms.assetid: b18b45a2-e187-44f5-a8c9-26fd9828b6c6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ed7b1d3ae88ef50d267cb129d861abab2b33ffd8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68116664"
---
# <a name="propertyindex-property-sqlserviceadvancedproperty-class"></a>PropertyIndex 屬性 (SqlServiceAdvancedProperty 類別)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  取得或設定指定進階屬性位置的屬性索引，該進階屬性位於屬於參考之服務的進階屬性陣列中。  
  
## <a name="syntax"></a>語法  
  
```  
  
object.PropertyIndex [= value]  
```  
  
## <a name="parts"></a>組件  
 *object*  
 代表進階屬性的 [SqlServiceAdvancedProperty 類別](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) 物件。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 A **uint32**值，指定屬於參考之服務的進階的屬性陣列中的進階屬性的位置。  
  
## <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [啟動及停止服務](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
