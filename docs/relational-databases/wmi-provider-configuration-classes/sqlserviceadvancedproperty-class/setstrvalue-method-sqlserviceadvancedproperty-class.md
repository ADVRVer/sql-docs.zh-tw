---
title: "SetStrValue 方法 （SqlServiceAdvancedProperty 類別） |Microsoft 文件"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: SetStrValue Method (SqlServiceAdvancedProperty Class)
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: SetStrValue method
ms.assetid: 1fededc3-81ba-4b08-83f9-189b96140799
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 762ad4045b97a7e54b71a59f9f45c95565cbbb94
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="setstrvalue-method-sqlserviceadvancedproperty-class"></a>SetStrValue 方法 (SqlServiceAdvancedProperty 類別)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]設定屬性的字串值。  
  
## <a name="syntax"></a>語法  
  
```  
  
object.SetStrValue(StrValue)  
```  
  
## <a name="parts"></a>組件  
 *物件*  
 代表進階屬性的 [SqlServiceAdvancedProperty 類別](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) 物件。  
  
#### <a name="parameters"></a>參數  
  
|參數|Description|  
|---------------|-----------------|  
|*StrValue*|指定進階屬性值的字串值。|  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 uint32 值，如果已成功修改此服務為 0，如果不支援要求則為 1，以及其他指示錯誤的任何數字。  
  
## <a name="remarks"></a>備註  
 屬性值類型必須是 *string* ，才能將屬性設定為字串值。  
  
## <a name="see-also"></a>請參閱＜  
 [啟動及停止服務](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
